# Taking LS

## Objective

Find the hidden flag inside the provided ZIP file.

## 1. Download the ZIP

Download the challenge ZIP file from the provided Mega link and save it to your Kali Linux system.

Then navigate to the directory containing the ZIP:
```bash
cd ~/Downloads
```
Check the file:
```bash
ls
```
## 2. Extract the ZIP

Extract the archive:
```bash
unzip "The Flag.zip"
```
Enter the extracted directory:
```bash
cd "The Flag"
```
Check the contents:
```bash
ls
```
You may see:
```
The Flag.pdf
```
At first, there appears to be nothing else interesting.

## 3. Look for Hidden Files

The challenge name "Taking LS" is a hint to use the Linux ls command. So the normal `ls` does not display hidden files.

Use:
```bash
ls -la
```
The -a option means all files, including hidden files.

You should find something similar to:
```
.
..
.ThePassword
The Flag.pdf
```
## 4. Explore the Hidden Directory

Enter the hidden directory:
```bash
cd .ThePassword
```
List its contents:
```bash
ls -la
```
You should find:

ThePassword.txt
## 5. Read the Password

Display the file:
```bash
cat ThePassword.txt
```
The password is:
```bash
Im The Flag
```
## 6. Unlock the PDF

The PDF is password protected.

If evince is not installed, you can use qpdf from the terminal.

Install it:
```bash
sudo apt update
sudo apt install qpdf
```
Go back to the parent directory:
```bash
cd ..
```
Decrypt the PDF:
```bash
qpdf --password="Im The Flag" --decrypt "The Flag.pdf" unlocked.pdf
```
This creates:
```
unlocked.pdf
```
## 7. Extract the PDF Text

Install pdftotext if necessary:
```bash
sudo apt install poppler-utils
```
Extract the text:
```bash
pdftotext unlocked.pdf -
```
The flag is:
```bash
ABCTF{T3Rm1n4l_is_c00l}
```
Flag
```
ABCTF{T3Rm1n4l_is_c00l}
```
Key Takeaway

The main trick was recognizing that hidden Linux files start with ..

The important command was:
```bash
ls -la
```
Instead of:
```bash
ls
```
The challenge flow was:

ZIP
 │
 ├── The Flag.pdf
 │
 └── .ThePassword
       │
       └── ThePassword.txt
              │
              └── "Im The Flag"
                       │
                       ▼
                Unlock PDF
                       │
                       ▼
          ABCTF{T3Rm1n4l_is_c00l}