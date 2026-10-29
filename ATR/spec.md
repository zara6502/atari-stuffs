# **ATR File Format Description**
Programs  
Used w  
idely by emulators, SIO2PC & APE peripheal emulators.  

# **Conventions**
**DWORD** - 32bit unsigned long (little endian)  
**WORD** - 16bit unsigned short (little endian)  
**BYTE** - 8bit unsigned char  

# **Header**

16 bytes long.  
 
| Type |	Name |	Description |
| :--- | :--: | :---------- |
| WORD	| wMagic |	$0296 (sum of 'NICKATARI') |
| WORD	| wPars	| size of this disk image, in paragraphs (size/$10) |
| WORD	| wSecSize	| sector size. ($80 or $100) bytes/sector |
| BYTE	| btParsHigh	| high part of size, in paragraphs (added by REV 3.00) |
| DWORD	| dwCRC	| 32bit CRC of file (added by APE?) |
| DWORD	| dwUnused	| unused |
| BYTE	| btFlags	| bit 0 (ReadOnly) (added by APE?) |

# **Body**
Then there are continuous sectors. Some ATR files are incorrect - if sector size is > $80 first three sectors should be $80 long. But, few files have these sectors $100 long.  
Format was created by Nick Kennedy.
