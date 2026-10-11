1. HTML: the structure
This is the page layout: the top bar, the four summary boxes, the path box, the folder buttons, the file list and the result area.

2. CSS: the look
This sets the colors, spacing and dashboard layout, including greyed-out unavailable folders and the red warning box. It also makes the page fit any screen size.

3. JavaScript: the logic
This does the real work, step by step:

Choose the main folder: selectFolderPath() opens the folder window. If the browser doesn't support that, it uses a normal folder dialog instead. It also copies a pasted server path so you can paste it into the window.
Show folder buttons: showSubFolderButtons() compares the folders it finds with a list of expected folders called EXPECTED_FOLDERS. Folders found get a clickable button, and missing ones are greyed out.
Click a folder: selectSubFolder() reads all Excel files in that folder, including inner folders, and ignores temporary files that start with ~$.
Sort the files: handleFiles() reads the number in each file name, like (324-357), and sorts by it.
Merge: mergeFiles() opens each file, reads the first sheet, and removes empty rows. It keeps the header from the first file only and stacks the rest below. If the Column C value changes between two files, it inserts a blank row and colors it cyan.
Check for missing items: It checks the file names for gaps in the number ranges. It also checks Column D for missing numbers, which are the missing forms.
Download: It builds a new Excel file and saves it with the folder's name, like ATFL.xlsx.

The Excel library
The tool uses a free library called xlsx-js-style, loaded from the internet. It reads and writes Excel files and supports cell colors. Without it, the page can't open or create Excel files, so the first load needs internet.

One-line summary for your manager
"The page reads the Excel files in the browser, sorts and combines them with JavaScript, checks for gaps, and downloads one new Excel file. Nothing is sent to a server."

Likely questions

Is it safe? Yes. Everything runs on your computer, and no files are uploaded.
Can it be changed? Yes. For example, the folder list is just one line of code, and the Column C and D checks can be changed.
What if it fails? The page shows an error message, and details appear in the browser console.
