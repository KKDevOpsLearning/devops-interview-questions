# 🔗 Linux Link Commands (`ln`) – Interview Q&A with Examples

This document covers the most commonly asked **scenario-based interview questions** about Linux **hard links** and **soft (symbolic) links**, with simple answers and examples.

---

## 1. What is the difference between a Hard Link and a Soft Link?
- **Hard Link:** Points to file’s data (inode). Works even if the original file is deleted.  
- **Soft Link (Symbolic Link):** Points to the file name/path. Breaks if the file is deleted or moved.  

### Example:
```bash
ln file1 hardlink1        # Create hard link
ln -s file1 softlink1     # Create soft link
2. What happens if the original file is deleted?
Hard Link: Still works (same inode).

Soft Link: Becomes broken (dangling).

3. Can you create a hard link for a directory?
Normally No (to avoid loops).

Soft links can be created for directories.

Example:
bash
Copy code
ln -s /etc etc_link    # Creates soft link to /etc directory
4. How to find all hard links of a file?
Check inode:

bash
Copy code
ls -i file1
Find all files with the same inode:

bash
Copy code
find . -inum <inode_number>
5. If you edit a file via hard/soft link, does it affect the original?
Yes, changes are saved because both point to the same data.

6. How to check the number of links a file has?
bash
Copy code
ls -l
The second column shows link count.

7. Can hard links work across different file systems?
No, hard links only work in the same file system.

Soft links can span file systems.

8. How to find broken soft links?
bash
Copy code
find . -xtype l
9. What happens if you rename or move the target file?
Hard Link: Still works (inode unchanged).

Soft Link: Breaks (path changed).

10. How to check inode of a file?
bash
Copy code
ls -i filename
11. What happens when you copy a soft link?
By default, it copies the target file content.

To copy the link itself:

bash
Copy code
cp -a softlink newlink
