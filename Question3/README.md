1. File Creation

Commands:

cd ~

echo "This is sample data for link testing." > sample_data.txt

cat sample_data.txt

Output:

This is sample data for link testing.

Explanation:

This command creates a file named sample_data.txt in my home directory and writes sample text into it.

Screenshot:
<img width="513" height="94" alt="Screenshot 2026-01-05 at 11 55 44 PM" src="https://github.com/user-attachments/assets/6ff3eb4f-5c04-45db-9fb2-90128ba63885" />

2. Hard Link Creation

Commands:

ln sample_data.txt sample_hard.txt

Explanation:
This command creates a hard link named sample_hard.txt that points to the same inode as the original file.

3. Symbolic (Soft) Link Creation

Commands:

ln -s sample_data.txt sample_soft.txt

Explanation:

This command creates a symbolic link named sample_soft.txt that points to the original file path.

4.  Inode Verification

Commands:

ls -li sample_data.txt sample_hard.txt sample_soft.txt

Output:

141459624 -rw-r--r--  2 bhupen  staff  38 Jan  5 23:54 sample_data.txt
141459624 -rw-r--r--  2 bhupen  staff  38 Jan  5 23:54 sample_hard.txt
141460532 lrwxr-xr-x  1 bhupen  staff  15 Jan  5 23:57 sample_soft.txt -> sample_data.txt

Explanation:

The ls -li command displays inode numbers along with file details for each file and link.

Screenshot:<img width="684" height="95" alt="Screenshot 2026-01-05 at 11 59 22 PM" src="https://github.com/user-attachments/assets/a27a47af-17bc-4675-9120-6019124e37f5" />

5. Inode Analysis

Explanation:
The files `sample_data.txt` and `sample_hard.txt` share the same inode number because a hard link points to the same underlying file. The symbolic link `sample_soft.txt` has a different inode because it only stores the path to the original file.

6. File Metadata Inspection

Command:

ls -l sample_data.txt

Output:

-rw-r--r--  2 bhupen  staff  38 Jan  5 23:54 sample_data.txt

Explanation:

The ls -l command displays detailed file metadata including permissions, ownership, size, and timestamps.

Screenshot:
<img width="487" height="72" alt="Screenshot 2026-01-06 at 12 02 17 AM" src="https://github.com/user-attachments/assets/56e97d5e-44c4-48f6-9b58-919797f1d266" />

7.  Disk Usage Check (Home Directory)

Command:

du -sh ~

Explanation:
The du -sh command shows the total disk usage of my home directory in a human-readable format.

8. File Size Overview

Command:

ls -lh ~

Output:

total 16
drwx------@    5 bhupen  staff   160B Sep 13 15:59 Applications
drwx------+   21 bhupen  staff   672B Jan  5 23:24 Desktop
drwx------+   33 bhupen  staff   1.0K Jan  5 23:31 Documents
drwx------@ 1584 bhupen  staff    50K Dec 30 13:00 Downloads
drwx------@  107 bhupen  staff   3.3K Oct  7 16:57 Library
drwx------    13 bhupen  staff   416B Apr 23  2025 Movies
drwx------+    6 bhupen  staff   192B Jan 13  2024 Music
drwx------+   39 bhupen  staff   1.2K May  2  2025 Pictures
drwxr-xr-x+    4 bhupen  staff   128B Jun 14  2023 Public
-rw-r--r--     2 bhupen  staff    38B Jan  5 23:54 sample_data.txt
-rw-r--r--     2 bhupen  staff    38B Jan  5 23:54 sample_hard.txt
lrwxr-xr-x     1 bhupen  staff    15B Jan  5 23:57 sample_soft.txt -> sample_data.txt

Explanation:

This command lists files in the home directory along with their sizes in a human-readable format.

Screenshot:
<img width="729" height="280" alt="Screenshot 2026-01-06 at 12 04 50 AM" src="https://github.com/user-attachments/assets/c2bb68d1-3cb1-439b-89e1-265e13d04eda" />

9. Link Deletion Test

Command:

rm sample_soft.txt

cat sample_data.txt

Output:

This is sample data for link testing.

Explanation:

Deleting the symbolic link does not affect the original file, confirming that symbolic links only reference the file path.

Screenshot:
<img width="448" height="100" alt="Screenshot 2026-01-06 at 12 06 12 AM" src="https://github.com/user-attachments/assets/dcdbd75c-265f-4898-bdd4-38c5e3336ed0" />

10. Disk Utility Demonstration (`du` & `df`)

Command:

du -h --max-depth=1 ~
df -h

OUtput:

du: unrecognized option `--max-depth=1'
usage: du [-Aclnx] [-H | -L | -P] [-g | -h | -k | -m] [-a | -s | -d depth] [-B blocksize] [-I mask] [-t threshold] [file ...]
Filesystem        Size    Used   Avail Capacity iused ifree %iused  Mounted on
/dev/disk3s1s1   228Gi    11Gi    69Gi    15%    451k  725M    0%   /
devfs            202Ki   202Ki     0Bi   100%     700     0  100%   /dev
/dev/disk3s6     228Gi   4.0Gi    69Gi     6%       4  725M    0%   /System/Volumes/VM
/dev/disk3s2     228Gi   7.5Gi    69Gi    10%    1.3k  725M    0%   /System/Volumes/Preboot
/dev/disk3s4     228Gi   2.9Mi    69Gi     1%      66  725M    0%   /System/Volumes/Update
/dev/disk1s2     500Mi   6.0Mi   483Mi     2%       1  4.9M    0%   /System/Volumes/xarts
/dev/disk1s1     500Mi   5.7Mi   483Mi     2%      30  4.9M    0%   /System/Volumes/iSCPreboot
/dev/disk1s3     500Mi   684Ki   483Mi     1%      50  4.9M    0%   /System/Volumes/Hardware
/dev/disk3s5     228Gi   135Gi    69Gi    67%    963k  725M    0%   /System/Volumes/Data
map auto_home      0Bi     0Bi     0Bi   100%       0     0     -   /System/Volumes/Data/home

Explanation:

The du command shows disk usage of directories, while the df command displays filesystem disk space usage in a human-readable format.

Screenshot:
<img width="952" height="306" alt="Screenshot 2026-01-06 at 12 07 23 AM" src="https://github.com/user-attachments/assets/1500c1b1-58fa-4ab9-90c1-49b22723dd78" />

