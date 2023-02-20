# updutils
Tools for managing and versioning CMS files using the CMS UPDATE/EXECUPDT commands.

The tools in this package assist in creating files that can be managed and updated
using the standard CMS UPDATE/EXECUPDT facility. The tools are:

NEWEXEC -   Creates a new file compatible with UPDATE/EXECUPDT with proper serial 
            numbers and other settings. The tool creates a control file, two AUX files, and two initial updates to produce a useful starting point file. 

NEWCHG   -  Creates a new update to a file and inserts it into the appropriate 
            AUX files. After performing this step, running the UPDEXEC command
            will apply all previous updates and create the contents of the new update file as the delta between the previous version and the new version.

UPDEXEC -   Apply all updates to base file. If the control file contains a new 
            update file, the user is left in XEDIT to create changes to the file.

BLDEXEC -   Builds the specfified exec, applying all updates. 

BLDMAC -    Builds a CMS MACLIB from a list of member file names. The 1st line of each 
            member name must be COPY <membername> or MACRO <membername>. See the description in the CMS MACLIB documentation for the difference.

Note that while these tools are primarily intended for use with EXEC files, they can be used with any type of file by renaming the base file filetype to $<filetype>, ensuring the file is LRECL 80, RECFM F, and the file possesses serial numbers in columns 72-80. 
The serial numbers may be added to the file using the SET SERIAL ALL command in XEDIT.

When unpacking these files, they should all be RECFM F, LRECL 80. 