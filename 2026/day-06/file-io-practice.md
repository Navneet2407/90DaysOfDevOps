File-io-pratcie
--------------------------------------------------------------------------------------------
- To create a n file and write to it at the same time:
   -> echo "This is Line 1" > notes.txt (this will create a notes.txt file and overwrites  the content)
   -> echo "this is Line 2" >> notes.txt (this will create a notes.txt file and append the content into the next line)
   -> echo "this is Line 3" >> notes.txt 
   -> echo "this is Line 4" | tee -a notes.txt ( this will create a file append to it and display the line)

- cat notes.txt : cat is used to read the contect of the file.
- head notes.txt : display the first 10 line from the file.
- tail notes.txt : display the last 10 line from the file.
- head -n 2 notes.txt : display first 2 line from the file.
- tail -n 2 notes.txt : display last 2 line from the file.
--------------------------------------------------------------------------------------------