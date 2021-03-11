# ArcGIS--v10.8-Spell-Checker



CartTextrophe
Cartography + text →catastrophe 
∴CartTextrophe

An open-sourced multi-lingual spellchecker for ArcGIS v10.8 or earlier.


CartTextrophe provides spellchecking capabilities to an ArcGIS MXD file using open-source language dictionaries, add-on Python libraries, and the arcpy application programming interface.  CartTextrophe includes four separate ArcToolbox tools that can check spelling, make spelling recommendations, and update text items for a variety of map elements.  CartTextrophe is customizable-allowing the user to build a custom dictionary of words that are skipped by the spellcheckers.
CartTextrophe is Python-based and uses the Pyenchant library, the EasyGUI library, and Open Office (or LibreOffice) dictionary files.  Both Pyenchant and the OpenOffice/LibreOffice dictionary files are free/ open source tools and include in with the source folders.
The standard build of CartTextrophe includes dictionary files that can spellcheck American English (default), British English, French and German (although the tool interface is always in American English).  Over 30 different language libraries are available from Open Office.  With a little effort the user can leverage these dictionary files for use with CartTextrophe.
 What CartTextrophe Can Do:
1.	Check spellings, make spelling recommendations, and update and alter text in layout frame text elements, legend titles, and MXD map document properties (title, summary, description, author, credits, and tags).  CartTextrophe uses regular expressions to skip any dynamic text in a text box!
2.	Check spellings, make spelling recommendations, and update and alter text in an attribute table in a feature class.
3.	Check spellings, make spelling recommendations, and update and alter text for all table-of-content items including the data frame layer names, layer group manes and layer names in the table of contents.
4.	CartTextrophe is customizable-allowing the user to build a custom dictionary of words that are skipped by the spell checkers.  The custom dictionary is stored in a text file so the custom dictionary can be shared among users.
5.	The PyEnchant library included instructions for adding spelling support for over 100 dictionaries.
What CartTextrophe will not do:
Text items in the MXD Data View are not exposed to Python via arcpy and cannot be checked by CartTextrophe.
CartTextrophe can correct the text only if the text item has read/write permissions in arcpy.  Arcpy annotation text is stored in a binary large object (BLOB).  Currently the tools will not support BLOB items but some annotation tables contain an attribute called TextString.  Since TextString mimics the text BLOB CartTextrophe can read TextString but it will only notify the user of misspellings (or make spelling recommendations) to the geoprocessing window in ArcGIS.  Unselect the Close this dialog when completed successfully in the ArcGIS geoprocessing results window to see misspelled words and suggestions.
This toolset is in beta.  While I have tested this code on a variety of MXDs and data-there are too many contingencies for me to catch.  If you find the tool throws an error please email me with the error, and if possible, the offending MXD or data.
Real time corrections?  No, if a word shows as a misspelling you can only skip the word, add the word to the custom dictionary and leave the word intact, or accept a suggestion.  While easygui provides a means to get user input, arcpy does not play nicely with easygui.  Why can’t I manually enter a correction in real time?  When ArcMap opens a geoprocessing window, the geoprocessor window is repeatedly gaining focus making it impossible to enter text for a correction.
Installing CartTextrophe:
Note, you must have ArcGIS 10.0 or later installed on your computer and Python 2.7 (included with ArcGIS). 
1.	Transfer the directory SpellcheckerForArcGIS to your computer.
2.	Install PyEnchant:  Run the.../SpellcheckerForArcGIS/InstallFiles/pyenchant-1.6.6.win32.exe application to install the PyEnchant libraries and the English, French, and German language packs.  Alternatively, Pip users can install PyEnchant using pip install pyenchant from the command line.).
3.	Install EasyGUI:  Move the entire easygui directory .from ../SpellcheckerForArcGIS/InstallFiles/easygui to C:\Python27\ArcGIS10.x\Lib\easygui
4.	In ArcMap open ArcToolbox.
5.	Right Click in ArcToolbox and select Add Toolbox.
6.	Add the SpellcheckerTools.tbx to ArcToolbox
7.	Execute the tools!
Building and Maintaining your Custom Library:
1.	Open the file ../SpellcheckerForArcGIS/ListOfWordsToSkip.txt
2.	Add words to new lines as necessary.  Words saved in this file will be skipped by the spell checker.
Adding Other Language Dictionaries.
There are language packs available for Arabic, Italian, Russian, and Spanish included with this distribution in the OtherLanguageDictionanaries directory.  These directories contain the needed *.DIC and *.AFF files (see below for more instructions).
Other language dictionary files are available from these links.
http://extensions.openoffice.org/en/search?f[0]=field_project_tags%3A157
https://extensions.libreoffice.org/extensions?getCategories=Dictionary&getCompatibility=any
Dictionary files download as *.OXT files, a compressed file format.  Unzip the .OXT file.  Find the *.dic and *.aff files from the unzipped contents.  Place these two files in this directory:  C:\Python27\ArcGIS10.4\Lib\site-packages\enchant\share\enchant\myspell
The prefix (*) for the language file is the text you need to enter in the CartTextrophe tools.  For example, to spell check Italian place it_IT.aff and it_IT.dic into the myspell directory. When running the ArcToolbox tool spell checkers replace the default en_US with it_IT. 

Problems, Recommendation, and Credits.
Errors in the code?  Please email me with the error message and if reasonable, the data that threw the error.
CartTextrophe is a free and open-source product.  You are free to alter or share the code but please attribute me.
Gerald Gabrisch, GISP
Lummi Indian Business Council GIS Manager
2665 Kwina Road
Bellingham, WA 98225
(360) 312-2310
geraldg@lummi-nsn.gov
gerry@gabrisch.us

