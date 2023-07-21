---
title: "How to extract VBA code from malicious Office documents" 
date: 2023-07-21T15:25:21+02:00 
description: "Learn how to extract VBA code from a malicious Microsoft Office document." 
featured: false 
draft: false 
toc: true 
# menu: main
usePageBundles: true 
# featureImage: "/images/path/file.jpg" # Sets featured image on blog post.
# featureImageAlt: 'Description of image' # Alternative text for featured image.
# featureImageCap: 'This is the featured image.' # Caption (optional).
# thumbnail: "/images/path/thumbnail.png" # Sets thumbnail image appearing inside card on homepage.
categories:
  - security-operations
tags:
  - malware-analysis
  - office-documents
  - threat-intelligence 

---

Learn how to extract VBA code from a malicious Microsoft Office document. 

<!--more-->

*** 

## Introduction 
In some cases it is advisable to check what's inside of an document before opening it. For our purpose we are using tools provided by REMnux to exactly do that. In malware analysis, this is called **static analysis**. 

## Preparations 
REMnux is a collection of tools which can be installed on a Ubuntu instance. Make sure to use a 2020-* version of Ubuntu due to compatibility issues. We are using the tools in a Ubuntu installation placed in the Windows Subsystem for Linux (WSL). 

**Assumption:** Let's assume we have a malicious Word document named "sample.docx". The Word document contains a malicious VBA macro. 

## Tools 
We are going to use different tools for the extraction of the VBA code provided by REMnux. Most of the tools are written in Python. 

### oleid 
oleid will give you a brief and high-level analysis of the documents nature. It's awesome to get a first indication regarding the reputation of the document. 

Statement: 

```bash
oleid sample.doc 
```

Output: 

```
analyst@scapegoat:~/malware/samples/case017$ oleid sample.doc
XLMMacroDeobfuscator: pywin32 is not installed (only is required if you want to use MS Excel)
oleid 0.60.1 - http://decalage.info/oletools
THIS IS WORK IN PROGRESS - Check updates regularly!
Please report any issue at https://github.com/decalage2/oletools/issues

Filename: sample.doc
--------------------+--------------------+----------+--------------------------
Indicator           |Value               |Risk      |Description
--------------------+--------------------+----------+--------------------------
File format         |MS Word 97-2003     |info      |
                    |Document or Template|          |
--------------------+--------------------+----------+--------------------------
Container format    |OLE                 |info      |Container type
--------------------+--------------------+----------+--------------------------
Application name    |Microsoft Office    |info      |Application name declared
                    |Word                |          |in properties
--------------------+--------------------+----------+--------------------------
Properties code page|1252: ANSI Latin 1; |info      |Code page used for
                    |Western European    |          |properties
                    |(Windows)           |          |
--------------------+--------------------+----------+--------------------------
Author              |Aijiao Chao         |info      |Author declared in
                    |                    |          |properties
--------------------+--------------------+----------+--------------------------
Encrypted           |False               |none      |The file is not encrypted
--------------------+--------------------+----------+--------------------------
VBA Macros          |Yes, suspicious     |HIGH      |This file contains VBA
                    |                    |          |macros. Suspicious
                    |                    |          |keywords were found. Use
                    |                    |          |olevba and mraptor for
                    |                    |          |more info.
--------------------+--------------------+----------+--------------------------
XLM Macros          |No                  |none      |This file does not contain
                    |                    |          |Excel 4/XLM macros.
--------------------+--------------------+----------+--------------------------
External            |0                   |none      |External relationships
Relationships       |                    |          |such as remote templates,
                    |                    |          |remote OLE objects, etc
--------------------+--------------------+----------+--------------------------
```

In the output we can see that there are - at least - suspicious VBA macros. In the description it is advised to use **olevba** to get further information. 

So let's do that. 

### olevba 
olevba has different switches to use. Try **- h** to get a full list. 

Next, we're going with a basic analysis of any code inside of the doc:  

```
olevba -a sample.doc
```

Output: 

```
analyst@scapegoat:~/malware/samples/case017$ olevba -a sample.doc
XLMMacroDeobfuscator: pywin32 is not installed (only is required if you want to use MS Excel)
olevba 0.60.1 on Python 3.8.10 - http://decalage.info/python/oletools
===============================================================================
FILE: sample.doc
Type: OLE
-------------------------------------------------------------------------------
VBA MACRO ThisDocument.cls
in file: sample.doc - OLE stream: 'Macros/VBA/ThisDocument'
-------------------------------------------------------------------------------
VBA MACRO Module1.bas
in file: sample.doc - OLE stream: 'Macros/VBA/Module1'
+----------+--------------------+---------------------------------------------+
|Type      |Keyword             |Description                                  |
+----------+--------------------+---------------------------------------------+
|AutoExec  |AutoOpen            |Runs when the Word document is opened        |
|Suspicious|CreateObject        |May create an OLE object                     |
|Suspicious|CallByName          |May attempt to obfuscate malicious function  |
|          |                    |calls                                        |
|Suspicious|System              |May run an executable file or a system       |
|          |                    |command on a Mac (if combined with           |
|          |                    |libc.dylib)                                  |
|Suspicious|Base64 Strings      |Base64-encoded strings were detected, may be |
|          |                    |used to obfuscate strings (option --decode to|
|          |                    |see all)                                     |
+----------+--------------------+---------------------------------------------+
```

This gives us a little bit more detail about potential threats. 

Now, let's extract the code from the document: 

```
olevba -c sample.doc >> macro.txt
```

Output: 
*(The statement above will redirect the output shown below into the file "macro.txt" for further investigations.)* 
```
analyst@scapegoat:~/malware/samples/case017$ olevba -c sample.doc
XLMMacroDeobfuscator: pywin32 is not installed (only is required if you want to use MS Excel)
olevba 0.60.1 on Python 3.8.10 - http://decalage.info/python/oletools
===============================================================================
FILE: sample.doc
Type: OLE
-------------------------------------------------------------------------------
VBA MACRO ThisDocument.cls
in file: sample.doc - OLE stream: 'Macros/VBA/ThisDocument'
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
(empty macro)
-------------------------------------------------------------------------------
VBA MACRO Module1.bas
in file: sample.doc - OLE stream: 'Macros/VBA/Module1'
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Function eAsSgsVL() As Object
Dim hrOyFMRd As String
Dim blSoELVq As String
Dim sHjDF(26) As Long
Dim hzQtU As Long
Dim fOueQX As Integer
fOueQX = 26
hzQtU = fOueQX
blSoELVq = "fxNNbmIerSxhpodpsFcqTYulnMJVsgMDboqDrDOycnByYxmIjnkONhZRrZjtCjTtwcjLCBqYCxngbZybVrRxszmnMKSFwA.LkogGEnOLZlWnlyicKfXtwfqXjZWODmYfdyKTqiXoNZBZoPSUvvaWBeCaoveFeAFeEsoicKcriFIJpitcVesGlgxZCXrKFlTO"
Dim yYiP As Integer
yYiP = 10
sHjDF(0) = yYiP
Dim pmCmqsv As Integer
pmCmqsv = 19
sHjDF(1) = pmCmqsv
Dim Csyv As Integer
Csyv = 9
sHjDF(2) = Csyv
Dim AxwmZOJg As Integer
AxwmZOJg = 111
sHjDF(3) = AxwmZOJg
Dim MmZEQ As Integer
MmZEQ = 13
sHjDF(4) = MmZEQ
Dim cqXs As Integer
cqXs = 60
sHjDF(5) = cqXs
Dim eRXHBaNz As Integer
eRXHBaNz = 111
```

The output can now be analyzed in Visual Studio Code. 

## Conclusion 
As you can see the tools available are pretty powerful and can lead to a quick verdict. Or at least to some starting points for further investigations. 


