# 🔹 Linux `sed` Interview Questions & Answers

This document contains **commonly asked interview questions** on the `sed` (Stream Editor) command in Linux.  
It covers practical scenarios and simple examples to help you prepare.

---

## 1. What is `sed` in Linux?
**Answer:**  
`sed` stands for **Stream Editor**.  
It is used to **search, find, replace, insert, delete, and print** text in files or streams **without opening the file in an editor**.

---

## 2. How do you replace the first occurrence of a word in each line?
```bash
sed 's/old/new/' file.txt
👉 Replaces the first occurrence of old with new in every line.

3. How do you replace all occurrences of a word in a file?
bash
Copy code
sed 's/old/new/g' file.txt
👉 The g flag replaces all occurrences of old with new.

4. How do you replace text directly inside a file (in-place)?
bash
Copy code
sed -i 's/old/new/g' file.txt
👉 The -i option edits the file in place (saves changes permanently).

5. How do you print only specific lines from a file?
bash
Copy code
sed -n '3p' file.txt
👉 Prints only line 3.

bash
Copy code
sed -n '2,5p' file.txt
👉 Prints lines 2 to 5.

6. How do you delete a specific line in a file?
bash
Copy code
sed '2d' file.txt
👉 Deletes line 2.

bash
Copy code
sed '2,4d' file.txt
👉 Deletes lines 2 to 4.

7. How do you delete blank (empty) lines?
bash
Copy code
sed '/^$/d' file.txt
👉 Removes all empty lines.

8. How do you delete lines containing a specific word?
bash
Copy code
sed '/error/d' file.txt
👉 Deletes all lines that contain the word "error".

9. How do you insert a line before a specific line?
bash
Copy code
sed '3i\This is a new line' file.txt
👉 Inserts text before line 3.

10. How do you append a line after a specific line?
bash
Copy code
sed '3a\This is an appended line' file.txt
👉 Adds text after line 3.

11. How do you substitute only on a specific line?
bash
Copy code
sed '5s/old/new/' file.txt
👉 Replaces old with new only on line 5.

12. How do you replace only the nth occurrence of a word in each line?
bash
Copy code
sed 's/old/new/2' file.txt
👉 Replaces the second occurrence of old with new.

13. How do you print only lines matching a pattern?
bash
Copy code
sed -n '/success/p' file.txt
👉 Prints only lines containing "success".

14. How do you print lines that do NOT match a word?
bash
Copy code
sed -n '/error/!p' file.txt
👉 Prints all lines except those containing "error".

15. How do you remove everything after a specific character?
bash
Copy code
sed 's/:.*//' file.txt
👉 Removes everything after : in each line.

16. How do you replace text in multiple files at once?
bash
Copy code
sed -i 's/old/new/g' file1.txt file2.txt
👉 Replaces old with new in multiple files.

17. How do you apply multiple sed commands together?
bash
Copy code
sed -e 's/old/new/g' -e '2d' file.txt
👉 Replaces text and deletes line 2 in one go.

18. How do you extract a range of lines from a file?
bash
Copy code
sed -n '10,20p' file.txt
👉 Prints lines 10 to 20 only.

19. How do you remove the first line of a file?
bash
Copy code
sed '1d' file.txt
👉 Deletes the first line.

20. How do you remove the last line of a file?
bash
Copy code
sed '$d' file.txt
👉 Deletes the last line (where $ means end of file).

✅ Quick Summary of Useful Flags
s → substitute (replace text)

d → delete (remove lines)

p → print (show lines)

i → insert (add line before)

a → append (add line after)

-n → suppress output (print only what you specify)

-i → in-place edit (save changes in file)

