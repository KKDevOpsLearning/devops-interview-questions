# Hard Link vs Soft Link (with Real-Time Examples)

## 🔗 Hard Link vs Soft Link

  ------------------------------------------------------------------------------
  Feature           **Hard Link**        **Soft Link (Symbolic Link)**
  ----------------- -------------------- ---------------------------------------
  **Points to**     Actual file data     File path (like a shortcut)
                    (inode)              

  **File Deletion** Original file        If original file is deleted, soft link
                    deletion does        becomes a **broken link**
                    **not** affect hard  
                    link (data is still  
                    accessible)          

  **Cross           ❌ Cannot span       ✅ Can link across file systems
  Filesystem**      across different     
                    file systems or      
                    partitions           

  **Directory       ❌ Cannot create     ✅ Can create soft link to directories
  Linking**         hard link to         
                    directories (mostly  
                    restricted)          

  **Performance**   Slightly faster      Slightly slower (path resolution
                    (direct inode        required)
                    reference)           
  ------------------------------------------------------------------------------

------------------------------------------------------------------------

## 📍 Real-Time Use Cases

### 🔧 Hard Link Use Cases

-   **Backup Systems** -- Avoids duplication of data (uses same inode,
    saves disk space).
-   **Version Control Systems (Git)** -- Uses hard links internally to
    point to the same object files.
-   **Data Deduplication** -- Multiple copies of same file without extra
    disk space.

### 🔧 Soft Link Use Cases

-   **Configuration Management** -- Linking `/etc/config/current` to
    `/etc/config/v2.3`.
-   **Shortcuts** -- Quick access to long paths.
-   **Sharing Common Files** -- Multiple apps point to one file.
-   **Legacy System Migration** -- Keep old paths working.

------------------------------------------------------------------------

## 📝 Scenario-Based Questions

### 1️⃣ File Deletion

**Q:** If you delete original file after creating hard & soft links?\
**A:** Hard link still works ✅, Soft link breaks ❌

### 2️⃣ Space Saving

**Q:** Share 10 GB file without duplicating data?\
**A:** Hard link ✅ (same inode, no extra space).

### 3️⃣ Directory Linking

**Q:** Point `/var/www/current` to latest build folder?\
**A:** Soft link ✅ (easy to update).

### 4️⃣ Cross Filesystem

**Q:** Link file across `/mnt/disk1` & `/mnt/disk2`?\
**A:** Soft link ✅ (hard link not allowed).

### 5️⃣ Protect Logs

**Q:** Prevent accidental deletion of log file?\
**A:** Hard link ✅ (data survives even if original deleted).

------------------------------------------------------------------------

## 🖥️ Hands-On Commands

### 1️⃣ Create File

``` bash
echo "Hello World" > file.txt
ls -li file.txt
```

### 2️⃣ Create Hard Link

``` bash
ln file.txt file_hard.txt
ls -li file.txt file_hard.txt
```

### 3️⃣ Create Soft Link

``` bash
ln -s file.txt file_soft.txt
ls -li file.txt file_soft.txt
```

### 4️⃣ Delete & Test

``` bash
rm file.txt
cat file_hard.txt   # Still works ✅
cat file_soft.txt   # Broken link ❌
```

### 5️⃣ Cross-Filesystem

``` bash
ln file_hard.txt /mnt/disk2/hard_link.txt   # ❌ Fails
ln -s file_hard.txt /mnt/disk2/soft_link.txt  # ✅ Works
```

------------------------------------------------------------------------

## 🧠 Quick Cheat Sheet

  Task                     Command
  ------------------------ ------------------------
  Create Hard Link         `ln source target`
  Create Soft Link         `ln -s source target`
  Check Inode              `ls -li`
  Check Soft Link Target   `ls -l`
  Find Links to File       `find . -inum <inode>`
  Remove Link              `rm link_name`

------------------------------------------------------------------------

✅ Perfect for GitHub README or Documentation.
