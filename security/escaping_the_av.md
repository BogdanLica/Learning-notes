## Obfuscating mimikatz from an AV

* ##### Change all the strings that relate to *mimikatz* to a different string
* ##### If a file is detected as soon as it touches the disk, then it is probably based on the signature
  * if the file has a size of 100000, then do 
  ```bash
  head -c 50000 my_program.exe > av_test.txt
  ```
  * open a hex editor and try to change the bytes and continue doing this until the full binary is undetected