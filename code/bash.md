
###Simple for loop in terminal

`for i in e f; do echo $i; done`


---

###Count the number of lines in a file
`$wc -l < /path/to/file`

Explanation:

wc = Terminal command for "word count"

-l = Flag to specify line count

< = Redirect your file as the input data source for the "wc" command


---
###Count the number of instances/occurrences of items in a column in a file

`$cut -f1 | sort | uniq -c`

Explanation:

cut - Command to apply options to the designated field (i.e. column).

-f1 - -f1 = specifies which field (i.e. column) to work on. Change the number to specify your desired column. Or, you can even specify a range of columns to work on (e.g. -f2-6)

"|" - Pipe which sends the results of the previous command ("cut" in this example) to another command.

sort - Sorts the info from the "cut" command in ascending order.

"|" - Pipe which sends the results of the previous command ("sort" in this example) to another command.

uniq -c - Counts the number of occurrences of each unique "word" in the specified column(s). (Note: Technically "uniq -c" is counting the occurrence of each unique line in the specified column, not the actual "words." It is this reason (that uniq occurrences are tallied by line) that you use the cut command to have the uniq command focus on a single column from the source file.)



---
###Count the number of characters in column

`!awk '{print $1, "\t", $2, "\t", length($2)}' j_tab2 > tab_1_length﻿`

---

###Basic Substitutions in a File
This is the same as Find and Replace in programs like Microsoft Word, but will run on files that are too large to be opened with such programs.

```
$sed 's/text_you_want_replaced/replacement_text/g' path/to/source_file > path/to/destination_file
```

Code explanation:

- "s" invokes the substitute command in sed
- 
- "g" tells sed to apply the substitute command globally on each line. Without the "g" argument, sed will only apply your substitute command to the first instance it encounters on each line that contains your "text_you_want_replaced".

NOTE: This command is case sensitive and will only match EXACLTY what you enter in as the "text_you_want_replaced". If you need more flexibility (e.g. having sed find variations like upper- and lowercase text), it exists, but is a bit too in-depth to go into here.




###Audible Notification of Job Completion (Terminal)

After typing in a Terminal command (and before hitting 'Enter') add the following:

`; say "Text that you want to have the computer read aloud to notify you that the job is finished"`

Code explanation:

; - Semicolon separates the "say" command from the previous command.

say - The speech-to-text command for Terminal

"text between quotes" - This is the text that you want to be read when your job is finished.




---

### Moving multiple files from multiple subdirectories up one level into a single folder.

Example code is below which will move any files with the extension ".sra" in any subdirectories to a new, single directory. An explanation of how it works after the code.
    
```   
find /volume1/web/trilobite/Crassostrea_gigas_HTSdata/SRP014 -iname '*.sra' -exec mv '{}' /volume1/web/trilobite/Crassostrea_gigas_HTSdata/SRP014 \;
```

---

### Sum Column in Tab Delimited File

**code:** `cat /Volumes/web/cnidarian/TGR_intersectbed_CDS_v9_CGmotif.txt | awk -F"\t" '{ sum+=$10} END {print sum}'`

screenshot:
<img src="http://eagle.fish.washington.edu/cnidarian/skitch/BiGo_methratio_17A2220E.png" alt="BiGo_methratio_17A2220E.png"/>

---

### Count Lines with String

**code:** `!fgrep -c "fuzznuc" /Volumes/web/cnidarian/TJGR_oyster_v9_CG.gff`   

screenshot:   
<img src="http://eagle.fish.washington.edu/cnidarian/skitch/BiGo_methratio_17A2231A.png" alt="BiGo_methratio_17A2231A.png"/>


---

### Convert csv to tab

**code:** `!tr ',' "\t" </Users/sr320/Desktop/Ruphi\ Enriched\ Genes.csv> /Users/sr320/Desktop/Ruphi\ Enriched\ Genes.txt`

---

### Copy Program of Interest to Run

**code:** `cp ncbi-blast-2.2.27+/bin/* /usr/local/bin`

---
###Remove duplicate lines
**code:** `!uniq  /Volumes/web/cnidarian/TJGR_prom_notgene_cpgIsland1.gff  > /Volumes/web/cnidarian/TJGR_prom_notgene_cpgIsland1u.gff`

---

### Remove first line of file

**code:** `!tail -n +2 /Volumes/web/cnidarian/BiGo_methratio_boop.gff > /Volumes/web/cnidarian/BiGo_methratio_boop_c.gff`


---
### Remove lines containing
**code:**  `!grep -Ev '>' /Volumes/web/Mollusk/174gm_analysis/GenomeTracks_Fastas/Exons.fa > /Users/sr320/Desktop/tst.txt`

---   

### Find and Replace   


**code:**    

```
!sed 's/Roberts_20100712_CC_F3_trimmed/Haliotis_cra_v3/g' </Volumes/web/cnidarian/lft_BlackAbalone_v3_swissprot_blastout_c> /Volumes/web/cnidarian/lft_BlackAbalone_v3_swissprot_blastout_d
#sed 's/abc/XYZ/g' <infile> outfile
```


