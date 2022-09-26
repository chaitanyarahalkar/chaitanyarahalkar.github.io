---
title: "Computer Forensics: Theoretical Concepts"  
layout: post  
date: 2019-06-25  
headerImage: false
tag:
- forensics
- computer
- concepts  
category: blog  
author: anushkavirgaonkar  
description: Basic theoretical concepts in computer forensics.
---

## **File Formats and Carving**  

   Files of different kinds have different file structures. For example, a PNG file has a completely different structure than a Microsoft Word document, starting from the first few bytes of at the beginning, continuing into the locations where data are stored in the main body and terminating with a few distinctive bytes at the end of the file. The common headers of these file types are known as file signatures. They can be used to locate and salvage portions of deleted files. The process of searching for a certain file signature and attempting to extract the associated data is called “carving” because it conceptually involves cutting a specific piece of data out of a larger dataset.
    
   | **Extension**  |          **Header (Hex)**            |                                **Footer (Hex)**                                                                    |                                   
   |:----------:|:--------------------------------:|:--------------------------------------------------------------------------------------------------------------:|  
   | DOC	    | D0 CF 11 E0 A1 B1 1A E1          | 57 6F 72 64 2E 44 6F 63 75 6D 65 6E 74 2E                                                                      |  
   | XLS	    | D0 CF 11 E0 A1 B1 1A E1          | FE FF FF FF 00 00 00 00 00 00 00 00 57 00 6F 00 72 00 6B 00 62 00 6F 00 6F 00 6B 00                            |  
   | PPT	    | D0 CF 11 E0 A1 B1 1A E1          | 50 00 6F 00 77 00 65 00 72 00 50 00 6F 00 69 00 6E 00 74 00 20 00 44 00 6F 00 63 00 75 00 6D 00 65 00 6E 00 74 |  
   | ZIP	    | 50 4B 03 04 14                   | 50 4B 05 06 00                                                                                                 |                                  
   | GIF	    | 47 49 46 38 39 61 4E 01 53 00 C4 | 21 00 00 3B 00                                                                                                 |  
   | PDF	    | 25 50 44 46 2D 31 2E             | 25 25 45 4F 46                                                                                                 |  
 
## **Data Recovery**  

   Hard disks are the richest source for digital evidence. When a file is deleted, its entry in the file system is updated to indicate it's deleted status and the clusters that were previously allocated to storing are unallocated and can be reused to store a new file. However, the data are left on the disk and it is often possible to retrieve a file immediately after it has been deleted. The data will remain on the disk until a new file overwrites them. However, if a new file does not take up the entire cluster, a portion of the old file might remain in the slack space. In this case, a portion of a file can be retrieved long after it has been deleted and partially overwritten.   

   ![When old data are overwritten with new data, some of the old data can remain.](/assets/images/cftc_fig2.png)  


   
## **Data Hiding**  

   A file system may not use an entire partition. The space after the end of the volume called volume slack that can be used to hide data. The space between partitions is also vulnerable for hiding data. File slack space is another hidden storage.  

   ![Slack space.](/assets/images/cftc_fig3.png)  
   

   Steganography is the technique of hiding secret data within an ordinary, non-secret, file or message in order to avoid detection. Forensic tools are used to extract the hidden file from the steganographic image. Other forms of data hiding involve the use of tools and techniques to hide data throughout various locations in a computer system. Some of these places can include memory, slack space, hidden directories, bad blocks, alternate data streams, and hidden partitions.  

