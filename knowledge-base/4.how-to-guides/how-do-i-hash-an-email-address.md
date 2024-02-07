---
title: 'How do I hash a list of emails?'
description: 'We''ll go over pre-formatting best practices and provide step-by-step instruction on how to use our hashingFunction script from the Command Line.'
lastUpdated: '2020-12-03T17:26:57.138Z'
tags: ['Touchless PII Hasher']
---
### **Follow the steps below to manually hash your emails, or use our free [Touchless PII Hasher app](https://app.narrative.io/app/touchless-pii-hasher) to do it quickly, easily, and securely.**

### **Overview**

All emails uploaded to Narrative must be [pseudonymized](https://kb.narrative.io/what-is-pseudonymization) with one or more [hashing](https://kb.narrative.io/what-is-hashing) function: MD5, SHA-1, or SHA-256. And whichever function you use, there are standard pre-formatting practices that can help enable correspondence with other pseudonymized data.

#### Tools for Automatic Formatting and Hashing

1. For smaller lists, just make a copy our [Hashing Functions](https://docs.google.com/spreadsheets/d/1_x2vPJXY8_ycgPlzx1UKktdFIJdqelEnZNAdyJRphrU/copy) spreadsheet.
2. For larger lists, use our [hashingFunction](https://solutions.narrative.io/hubfs/hashingFunction.py) script and follow the Command Line procedure detailed below.

### **Pre-Formatting**

1. **_lowercase_ all text**  
    Hashing functions are case-sensitive. So _before_ pseudonymizing emails, it's standard practice to lowercase all text.
2. **Remove Extra Characters and Whitespace**

    Any extra whitespaces or unnecessary characters will result in a completely different hashed result. So make sure to remove:

    1. whitespace and/or delimiters between emails (e.g. commas)
    2. extra periods in the email _username_  
        (an email address is made up of _username@domain.com_)
    3. "+" signs and all characters between the "+" and "_@domain.com_"  
        (e.g. remove "+news" from _johndoe+news@gmail.com_)
3. **Make sure your list is a single-column .csv file.**

### **Hashing Functions**

Hashing can be performed with either of three common hashing functions: [MD5](https://en.wikipedia.org/wiki/MD5), [SHA1](https://en.wikipedia.org/wiki/SHA-1), [SHA256](https://en.wikipedia.org/wiki/SHA-2).

To get the highest rate of correspondence, **we recommend using all three functions**, resulting in three pseudonymized character strings for each email on your list.

**Email:** <johndoe@gmail.com>  
**MD5:** 29a1df4646cb3417c19994a59a3e022a  
**SHA1:** e1e8d3e4a336d4f9dc63b70a534ff10834471556  
**SHA256:** 06a240d11cc201676da976f7b49341181fd180da37cbe40a77432c0a366c80c3

### How to Format and Hash Small Lists in Google Sheets

Our [Hashing Functions](https://docs.google.com/spreadsheets/d/1_x2vPJXY8_ycgPlzx1UKktdFIJdqelEnZNAdyJRphrU/copy) spreadsheet automatically performs pre-formatting and all three hashing functions.

_Step 1:_    Copy your list of emails and paste, starting in cell A4.

![sheetsinput](https://solutions.narrative.io/hubfs/sheetsinput.gif)

_Step 2:_    The spreadsheet may take a few minutes to compute. When the process is complete,                         navigate to the tab titled DOWNLOAD\_THIS\_SHEET\_AS\_.CSV\_FILE.

_Step 3:_    Finally, go to the File menu, go to Download, and then select _Comma-separated values                     (.csv, current sheet)_. Use this list to [upload to Narrative](https://kb.narrative.io/sending-lists).

![hashingExport](https://solutions.narrative.io/hubfs/hashingExport.gif)

_(Just in case, we also have a Google Sheet that will work to hash phone numbers, which removes all non-numerical characters prior to hashing: [Hashing Functions (Phone Numbers)](https://docs.google.com/spreadsheets/d/1QRHVDKbKk8t9Xga8s08HSKv1Mi91yFddxcoSOgpv8Vg/copy). You can use the same procedure as above.)_

### **How To Format and Hash From The Command Line on Mac OS**

Our _hashingFunction_ script automatically preforms pre-formatting and all three hashing functions. It can be copy-and-pasted for one-time use, or saved to your system repeated use.

First, access the Command Line by searching for the application called Terminal.![accessTerminal](https://solutions.narrative.io/hubfs/accessTerminal.gif)

#### For one-time use

_Step 1:_     Click the link here to open our [hashingFunctionCopyPaste.txt](https://solutions.narrative.io/hubfs/hashingFunctionCopyPaste.txt) file in a new tab.  Copy the text from the file, paste into the command line and press _Enter_.  (Make sure you include the final } at the bottom.)

![hashingPaste2](https://solutions.narrative.io/hubfs/hashingPaste2.gif)

_Step 2:_    Type _hashingFunction <_  

##### hashingFunction

_Step 3:_    Make sure your list of emails is a **single-column ._csv_ file.**

                 Drag and drop your file into the Terminal.  

hashingFunction < **/Users/narrative/Documents/emailTestList.csv**

_Step 4:_    Type the > symbol and whatever you want to name your new hashed list. Press _Enter_.

hashingFunction < /Users/narrative/Documents/emailTestList.csv **> emailHashedList.csv**

_CAUTION:_ **DO** **NOT** direct the output to the same file name. **This will result in the contents of your file being deleted.**

hashingFunction < fileName.csv > fileName.csv

![hashingComplete](https://solutions.narrative.io/hubfs/hashingComplete.gif)

_Step 5:_    Navigate to your Home directory to find your processed file.

![homeDirectory](https://solutions.narrative.io/hubfs/homeDirectory.gif)

_(Just in case, we also have a script that will work to hash phone numbers, which removes all non-numerical characters prior to hashing: [phoneHashingFunctionCopyPaste.txt](https://solutions.narrative.io/hubfs/phoneHashingFunctionCopyPaste.txt). You can use the same Copy & Paste procedure as above.)_

####  To save the hashingFunction for regular use

1. Download the [hashingFunction.py](https://solutions.narrative.io/hubfs/hashingFunction.py) script. (Control+Click and select "Save Link As...")
2. Place the file in your _bin_ folder_,_ at the location: /Users/_YOUR\_USERNAME\_HERE_/bin  

    To check if you already have a _bin_ folder, navigate to your Home directory and press Command+Shift+Period to reveal hidden folders. If you see a folder called _bin_, simply drag _hashingFunction.py_ into the folder.

    If you don't already have a _bin_ folder, create one in your Home directory. Then, drag _hashingFunction.py_ into the folder.

    ![creatBin2](https://solutions.narrative.io/hubfs/creatBin2.gif)
3. Make the file executable

    Open Terminal, type in the following, and press Enter:

    chmod +x hashingFunction.py

4. Now, you'll be able to use the script _hashingFunction.py_ whenever you want, using the same process detailed above.  

    _Step 1:_     Type _hashingFunction.py <_  
    _Step 2:_    Drag and drop your file (make sure your file is a **single-column ._csv_ file**)  
    _Step 3:_    Type > _emailHashedList.csv_  
    _Step 4:_    Access your _emailHashedList.csv_ in your Home directory

hashingFunction.py < /Users/narrative/Documents/emailTestList.csv > emailHashedList.csv

#### Testing Your Output

When using this process to hash your list of emails, we recommend testing the _hashingFunction_ on this [testList](https://solutions.narrative.io/hubfs/emailTestList.csv) of emails. Your output file should exactly match the following:

06a240d11cc201676da976f7b49341181fd180da37cbe40a77432c0a366c80c3  
29a1df4646cb3417c19994a59a3e022a  
e1e8d3e4a336d4f9dc63b70a534ff10834471556  
06a240d11cc201676da976f7b49341181fd180da37cbe40a77432c0a366c80c3  
29a1df4646cb3417c19994a59a3e022a  
e1e8d3e4a336d4f9dc63b70a534ff10834471556  
9f543669a5fee1099e4831c5a6fbf4e5ac0bf034ab4a21619f8e4886b6c4dea4  
54e90da195dd1493951bf561df4a3efd  
0f56865108d4c1325ecd2d5db8d15e1db4f2725b  
45600ad2083b4eabe118fba5e6eb19369cb23bbedee4e6b35607a552e693d4cd  
ca51a2716ebffd663a8bf16e1f269b31  
1ce4d2f27b9780cfa201e5f7815e27498fd4cfe6

#### Uploading Your List To Narrative

All lists uploaded to Narrative must be in _.csv_ format. See [How Do I Upload an ID List](https://kb.narrative.io/sending-lists) for more detail on uploading lists in general.

#### Additional Information

* [Blog Post: Convert email addresses into privacy-safe identifiers with Touchless PII Hasher](/blog/touchless-pii-hasher)
* [How do I use the Touchless PII Hasher app?](https://kb.narrative.io/how-do-i-use-the-touchless-pii-hasher-app)
* Wikipedia: [MD5 message-digest algorithm](https://en.wikipedia.org/wiki/MD5)
* Wikipedia: [SHA-1 (Secure Hash Algorithm 1)](https://en.wikipedia.org/wiki/SHA-1)
* Wikipedia: [SHA-2 (Secure Hash Algorithm 2)](https://en.wikipedia.org/wiki/SHA-2)
