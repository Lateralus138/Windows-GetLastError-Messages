# Windows GetLastError Messages

![Readme Card](https://github-readme-stats.vercel.app/api/pin/?username=Lateralus138&repo=Windows-GetLastError-Messages)

- [Windows GetLastError Messages](#windows-getlasterror-messages)
	- [Generation Code](#generation-code)
	- [Error list](#error-list)
		- [0x0000 - 0x00001FFF : 0 - 8191](#0x0000---0x00001fff--0---8191)

---

## Generation Code

List generated in ***C++*** with:

```CPP
#include <Windows.h>
#include <iostream>
#include <string>
std::string GetLastErrorAsString()
{
  DWORD errorId = ::GetLastError();
  if (errorId == 0)
  {
    return std::string();
  }
  LPSTR buffer = nullptr;
  size_t messageSize =
    FormatMessageA
    (
      FORMAT_MESSAGE_ALLOCATE_BUFFER |
        FORMAT_MESSAGE_FROM_SYSTEM |
        FORMAT_MESSAGE_IGNORE_INSERTS,
      NULL, errorId,
      MAKELANGID(LANG_NEUTRAL, SUBLANG_DEFAULT),
      (LPSTR)&buffer, 0, NULL
    );
  std::string message(buffer, messageSize);
  LocalFree(buffer);
  return message;
}
int main()
{
  std::cout << "|Number|Message|\n|------:|:------|\n";
  for (DWORD i = 0x0000; i < 0x1FFF; i++)
  {
    SetLastError(i);
    std::string em = GetLastErrorAsString();
    if (!em.empty())
    {
      std::string message = "|";
      message.append(std::to_string(i));
      message.push_back('|');
      message.append(em);
      message.append("|\n");
      std::cout << message;
    }
  }
}
```

and then new lines were replaced by `<br>` in an editor for this README.

---

## Error list

List 2 can be found here: [README_2.md](./README_2.md).

### 0x0000 - 0x00001FFF : 0 - 8191

Not all values have strings.

|Number|Message|
|------:|:------|
|1|Incorrect function.|
|2|The system cannot find the file specified.|
|3|The system cannot find the path specified.|
|4|The system cannot open the file.|
|5|Access is denied.|
|6|The handle is invalid.|
|7|The storage control blocks were destroyed.|
|8|Not enough memory resources are available to process this command.|
|9|The storage control block address is invalid.|
|10|The environment is incorrect.|
|11|An attempt was made to load a program with an incorrect format.|
|12|The access code is invalid.|
|13|The data is invalid.|
|14|Not enough memory resources are available to complete this operation.|
|15|The system cannot find the drive specified.|
|16|The directory cannot be removed.|
|17|The system cannot move the file to a different disk drive.|
|18|There are no more files.|
|19|The media is write protected.|
|20|The system cannot find the device specified.|
|21|The device is not ready.|
|22|The device does not recognize the command.|
|23|Data error (cyclic redundancy check).|
|24|The program issued a command but the command length is incorrect.|
|25|The drive cannot locate a specific area or track on the disk.|
|26|The specified disk or diskette cannot be accessed.|
|27|The drive cannot find the sector requested.|
|28|The printer is out of paper.|
|29|The system cannot write to the specified device.|
|30|The system cannot read from the specified device.|
|31|A device attached to the system is not functioning.|
|32|The process cannot access the file because it is being used by another process.|
|33|The process cannot access the file because another process has locked a portion of the file.|
|34|The wrong diskette is in the drive.<br>Insert %2 (Volume Serial Number: %3) into drive %1.|
|36|Too many files opened for sharing.|
|38|Reached the end of the file.|
|39|The disk is full.|
|50|The request is not supported.|
|51|Windows cannot find the network path. Verify that the network path is correct and the destination computer is not busy or turned off. If Windows still cannot find the network path, contact your network administrator.|
|52|You were not connected because a duplicate name exists on the network. If joining a domain, go to System in Control Panel to change the computer name and try again. If joining a workgroup, choose another workgroup name.|
|53|The network path was not found.|
|54|The network is busy.|
|55|The specified network resource or device is no longer available.|
|56|The network BIOS command limit has been reached.|
|57|A network adapter hardware error occurred.|
|58|The specified server cannot perform the requested operation.|
|59|An unexpected network error occurred.|
|60|The remote adapter is not compatible.|
|61|The printer queue is full.|
|62|Space to store the file waiting to be printed is not available on the server.|
|63|Your file waiting to be printed was deleted.|
|64|The specified network name is no longer available.|
|65|Network access is denied.|
|66|The network resource type is not correct.|
|67|The network name cannot be found.|
|68|The name limit for the local computer network adapter card was exceeded.|
|69|The network BIOS session limit was exceeded.|
|70|The remote server has been paused or is in the process of being started.|
|71|No more connections can be made to this remote computer at this time because there are already as many connections as the computer can accept.|
|72|The specified printer or disk device has been paused.|
|80|The file exists.|
|82|The directory or file cannot be created.|
|83|Fail on INT 24.|
|84|Storage to process this request is not available.|
|85|The local device name is already in use.|
|86|The specified network password is not correct.|
|87|The parameter is incorrect.|
|88|A write fault occurred on the network.|
|89|The system cannot start another process at this time.|
|100|Cannot create another system semaphore.|
|101|The exclusive semaphore is owned by another process.|
|102|The semaphore is set and cannot be closed.|
|103|The semaphore cannot be set again.|
|104|Cannot request exclusive semaphores at interrupt time.|
|105|The previous ownership of this semaphore has ended.|
|106|Insert the diskette for drive %1.|
|107|The program stopped because an alternate diskette was not inserted.|
|108|The disk is in use or locked by another process.|
|109|The pipe has been ended.|
|110|The system cannot open the device or file specified.|
|111|The file name is too long.|
|112|There is not enough space on the disk.|
|113|No more internal file identifiers available.|
|114|The target internal file identifier is incorrect.|
|117|The IOCTL call made by the application program is not correct.|
|118|The verify-on-write switch parameter value is not correct.|
|119|The system does not support the command requested.|
|120|This function is not supported on this system.|
|121|The semaphore timeout period has expired.|
|122|The data area passed to a system call is too small.|
|123|The filename, directory name, or volume label syntax is incorrect.|
|124|The system call level is not correct.|
|125|The disk has no volume label.|
|126|The specified module could not be found.|
|127|The specified procedure could not be found.|
|128|There are no child processes to wait for.|
|129|The %1 application cannot be run in Win32 mode.|
|130|Attempt to use a file handle to an open disk partition for an operation other than raw disk I/O.|
|131|An attempt was made to move the file pointer before the beginning of the file.|
|132|The file pointer cannot be set on the specified device or file.|
|133|A JOIN or SUBST command cannot be used for a drive that contains previously joined drives.|
|134|An attempt was made to use a JOIN or SUBST command on a drive that has already been joined.|
|135|An attempt was made to use a JOIN or SUBST command on a drive that has already been substituted.|
|136|The system tried to delete the JOIN of a drive that is not joined.|
|137|The system tried to delete the substitution of a drive that is not substituted.|
|138|The system tried to join a drive to a directory on a joined drive.|
|139|The system tried to substitute a drive to a directory on a substituted drive.|
|140|The system tried to join a drive to a directory on a substituted drive.|
|141|The system tried to SUBST a drive to a directory on a joined drive.|
|142|The system cannot perform a JOIN or SUBST at this time.|
|143|The system cannot join or substitute a drive to or for a directory on the same drive.|
|144|The directory is not a subdirectory of the root directory.|
|145|The directory is not empty.|
|146|The path specified is being used in a substitute.|
|147|Not enough resources are available to process this command.|
|148|The path specified cannot be used at this time.|
|149|An attempt was made to join or substitute a drive for which a directory on the drive is the target of a previous substitute.|
|150|System trace information was not specified in your CONFIG.SYS file, or tracing is disallowed.|
|151|The number of specified semaphore events for DosMuxSemWait is not correct.|
|152|DosMuxSemWait did not execute; too many semaphores are already set.|
|153|The DosMuxSemWait list is not correct.|
|154|The volume label you entered exceeds the label character limit of the target file system.|
|155|Cannot create another thread.|
|156|The recipient process has refused the signal.|
|157|The segment is already discarded and cannot be locked.|
|158|The segment is already unlocked.|
|159|The address for the thread ID is not correct.|
|160|One or more arguments are not correct.|
|161|The specified path is invalid.|
|162|A signal is already pending.|
|164|No more threads can be created in the system.|
|167|Unable to lock a region of a file.|
|170|The requested resource is in use.|
|171|Device's command support detection is in progress.|
|173|A lock request was not outstanding for the supplied cancel region.|
|174|The file system does not support atomic changes to the lock type.|
|180|The system detected a segment number that was not correct.|
|182|The operating system cannot run %1.|
|183|Cannot create a file when that file already exists.|
|186|The flag passed is not correct.|
|187|The specified system semaphore name was not found.|
|188|The operating system cannot run %1.|
|189|The operating system cannot run %1.|
|190|The operating system cannot run %1.|
|191|Cannot run %1 in Win32 mode.|
|192|The operating system cannot run %1.|
|193|%1 is not a valid Win32 application.|
|194|The operating system cannot run %1.|
|195|The operating system cannot run %1.|
|196|The operating system cannot run this application program.|
|197|The operating system is not presently configured to run this application.|
|198|The operating system cannot run %1.|
|199|The operating system cannot run this application program.|
|200|The code segment cannot be greater than or equal to 64K.|
|201|The operating system cannot run %1.|
|202|The operating system cannot run %1.|
|203|The system could not find the environment option that was entered.|
|205|No process in the command subtree has a signal handler.|
|206|The filename or extension is too long.|
|207|The ring 2 stack is in use.|
|208|The global filename characters, * or ?, are entered incorrectly or too many global filename characters are specified.|
|209|The signal being posted is not correct.|
|210|The signal handler cannot be set.|
|212|The segment is locked and cannot be reallocated.|
|214|Too many dynamic-link modules are attached to this program or dynamic-link module.|
|215|Cannot nest calls to LoadModule.|
|216|This version of %1 is not compatible with the version of Windows you're running. Check your computer's system information and then contact the software publisher.|
|217|The image file %1 is signed, unable to modify.|
|218|The image file %1 is strong signed, unable to modify.|
|220|This file is checked out or locked for editing by another user.|
|221|The file must be checked out before saving changes.|
|222|The file type being saved or retrieved has been blocked.|
|223|The file size exceeds the limit allowed and cannot be saved.|
|224|Access Denied. Before opening files in this location, you must first add the web site to your trusted sites list, browse to the web site, and select the option to login automatically.|
|225|Operation did not complete successfully because the file contains a virus or potentially unwanted software.|
|226|This file contains a virus or potentially unwanted software and cannot be opened. Due to the nature of this virus or potentially unwanted software, the file has been removed from this location.|
|229|The pipe is local.|
|230|The pipe state is invalid.|
|231|All pipe instances are busy.|
|232|The pipe is being closed.|
|233|No process is on the other end of the pipe.|
|234|More data is available.|
|235|The action requested resulted in no work being done. Error-style clean-up has been performed.|
|240|The session was canceled.|
|254|The specified extended attribute name was invalid.|
|255|The extended attributes are inconsistent.|
|258|The wait operation timed out.|
|259|No more data is available.|
|266|The copy functions cannot be used.|
|267|The directory name is invalid.|
|275|The extended attributes did not fit in the buffer.|
|276|The extended attribute file on the mounted file system is corrupt.|
|277|The extended attribute table file is full.|
|278|The specified extended attribute handle is invalid.|
|282|The mounted file system does not support extended attributes.|
|288|Attempt to release mutex not owned by caller.|
|298|Too many posts were made to a semaphore.|
|299|Only part of a ReadProcessMemory or WriteProcessMemory request was completed.|
|300|The oplock request is denied.|
|301|An invalid oplock acknowledgment was received by the system.|
|302|The volume is too fragmented to complete this operation.|
|303|The file cannot be opened because it is in the process of being deleted.|
|304|Short name settings may not be changed on this volume due to the global registry setting.|
|305|Short names are not enabled on this volume.|
|306|The security stream for the given volume is in an inconsistent state.<br>Please run CHKDSK on the volume.|
|307|A requested file lock operation cannot be processed due to an invalid byte range.|
|308|The subsystem needed to support the image type is not present.|
|309|The specified file already has a notification GUID associated with it.|
|310|An invalid exception handler routine has been detected.|
|311|Duplicate privileges were specified for the token.|
|312|No ranges for the specified operation were able to be processed.|
|313|Operation is not allowed on a file system internal file.|
|314|The physical resources of this disk have been exhausted.|
|315|The token representing the data is invalid.|
|316|The device does not support the command feature.|
|317|The system cannot find message text for message number 0x%1 in the message file for %2.|
|318|The scope specified was not found.|
|319|The Central Access Policy specified is not defined on the target machine.|
|320|The Central Access Policy obtained from Active Directory is invalid.|
|321|The device is unreachable.|
|322|The target device has insufficient resources to complete the operation.|
|323|A data integrity checksum error occurred. Data in the file stream is corrupt.|
|324|An attempt was made to modify both a KERNEL and normal Extended Attribute (EA) in the same operation.|
|326|Device does not support file-level TRIM.|
|327|The command specified a data offset that does not align to the device's granularity/alignment.|
|328|The command specified an invalid field in its parameter list.|
|329|An operation is currently in progress with the device.|
|330|An attempt was made to send down the command via an invalid path to the target device.|
|331|The command specified a number of descriptors that exceeded the maximum supported by the device.|
|332|Scrub is disabled on the specified file.|
|333|The storage device does not provide redundancy.|
|334|The specified operation is not supported on a resident file.|
|335|The specified operation is not supported on a compressed file.|
|336|The specified operation is not supported on a directory.|
|337|The specified copy of the requested data could not be read.|
|338|The specified data could not be written to any of the copies.|
|339|One or more copies of data on this device may be out of sync. No writes may be performed until a data integrity scan is completed.|
|340|The supplied kernel information version is invalid.|
|341|The supplied PEP information version is invalid.|
|342|This object is not externally backed by any provider.|
|343|The external backing provider is not recognized.|
|344|Compressing this object would not save space.|
|345|The request failed due to a storage topology ID mismatch.|
|346|The operation was blocked by parental controls.|
|347|A file system block being referenced has already reached the maximum reference count and can't be referenced any further.|
|348|The requested operation failed because the file stream is marked to disallow writes.|
|349|The requested operation failed with an architecture-specific failure code.|
|350|No action was taken as a system reboot is required.|
|351|The shutdown operation failed.|
|352|The restart operation failed.|
|353|The maximum number of sessions has been reached.|
|354|Windows Information Protection policy does not allow access to this network resource.|
|355|The device hint name buffer is too small to receive the remaining name.|
|356|The requested operation was blocked by Windows Information Protection policy. For more information, contact your system administrator.|
|357|The requested operation cannot be performed because hardware or software configuration of the device does not comply with Windows Information Protection under Lock policy. Please, verify that user PIN has been created. For more information, contact your system administrator.|
|358|The cloud sync root metadata is corrupted.|
|359|The device is in maintenance mode.|
|360|The specified operation is not supported on a DAX volume.|
|361|The volume has active DAX mappings.|
|362|The cloud file provider is not running.|
|363|The cloud file metadata is corrupt and unreadable.|
|364|The cloud file metadata is too large.|
|365|The cloud file property is too large.|
|366|The cloud file property is possibly corrupt. The on-disk checksum does not match the computed checksum.|
|367|The process creation has been blocked.|
|368|The storage device has lost data or persistence.|
|369|The provider that supports file system virtualization is temporarily unavailable.|
|370|The metadata for file system virtualization is corrupt and unreadable.|
|371|The provider that supports file system virtualization is too busy to complete this operation.|
|372|The provider that supports file system virtualization is unknown.|
|373|GDI handles were potentially leaked by the application.|
|374|The maximum number of cloud file properties has been reached.|
|375|The version of the cloud file property store is not supported.|
|376|The file is not a cloud file.|
|377|The file is not in sync with the cloud.|
|378|The cloud sync root is already connected with another cloud sync provider.|
|379|The operation is not supported by the cloud sync provider.|
|380|The cloud operation is invalid.|
|381|The cloud operation is not supported on a read-only volume.|
|382|The operation is reserved for a connected cloud sync provider.|
|383|The cloud sync provider failed to validate the downloaded data.|
|384|You can't connect to the file share because it's not secure. This share requires the obsolete SMB1 protocol, which is unsafe and could expose your system to attack.<br>Your system requires SMB2 or higher. For more info on resolving this issue, see: https://go.microsoft.com/fwlink/?linkid=852747|
|385|The virtualization operation is not allowed on the file in its current state.|
|386|The cloud sync provider failed user authentication.|
|387|The cloud sync provider failed to perform the operation due to low system resources.|
|388|The cloud sync provider failed to perform the operation due to network being unavailable.|
|389|The cloud operation was unsuccessful.|
|390|The operation is only supported on files under a cloud sync root.|
|391|The operation cannot be performed on cloud files in use.|
|392|The operation cannot be performed on pinned cloud files.|
|393|The cloud operation was aborted.|
|394|The cloud file's property store is corrupt.|
|395|Access to the cloud file is denied.|
|396|The cloud operation cannot be performed on a file with incompatible hardlinks.|
|397|The operation failed due to a conflicting cloud file property lock.|
|398|The cloud operation was canceled by user.|
|399|An externally encrypted syskey has been configured, but the system no longer supports this feature.  Please see https://go.microsoft.com/fwlink/?linkid=851152 for more information.|
|400|The thread is already in background processing mode.|
|401|The thread is not in background processing mode.|
|402|The process is already in background processing mode.|
|403|The process is not in background processing mode.|
|404|The cloud file provider exited unexpectedly.|
|405|The file is not a cloud sync root.|
|406|The read or write operation to an encrypted file could not be completed because the file can only be accessed when the device is unlocked.|
|407|The volume is not cluster aligned on the disk.|
|408|No physically aligned free space was found on the volume.|
|409|The APPX file can not be accessed because it is not encrypted as expected.|
|410|A read or write of raw encrypted data cannot be performed because the file is not encrypted.|
|411|An invalid file offset in the encrypted data info block was passed for read or write operation of file's raw encrypted data.|
|412|An invalid offset and length combination in the encrypted data info block was passed for read or write operation of file's raw encrypted data.|
|413|An invalid parameter in the encrypted data info block was passed for read or write operation of file's raw encrypted data.|
|414|The Windows Subsystem for Linux has not been enabled.|
|415|The specified data could not be read from any of the copies.|
|416|The specified storage reserve ID is invalid.|
|417|The specified storage reserve does not exist.|
|418|The specified storage reserve already exists.|
|419|The specified storage reserve is not empty.|
|420|This operation requires a DAX volume.|
|421|This stream is not DAX mappable.|
|422|Operation cannot be performed on a time critical thread.|
|423|User data protection is not supported for the current or provided user.|
|424|This directory contains entries whose names differ only in case.|
|425|The file cannot be safely opened because it is not supported by this version of Windows.|
|426|The cloud operation was not completed before the time-out period expired.|
|427|A task queue is required for this operation but none is available.|
|428|Failed loading a valid version of srcsrv.dll.|
|429|This operation is not supported with BTT enabled.|
|430|This operation cannot be performed because encryption is currently disabled.|
|431|This encryption operation cannot be performed on filesystem metadata.|
|432|Encryption cannot be cleared on this file/directory because it still has an encrypted attribute.|
|433|A device which does not exist was specified.|
|434|Dehydration of the cloud file is disallowed by the cloud sync provider.|
|435|A file snapshot operation was attempted when one is already in progress.|
|436|A snapshot of the file cannot be taken because a user-mapped section is present.|
|437|The file snapshot operation was terminated because one of the files was modified in a way incompatible with a snapshot operation.  Please try again.|
|438|An I/O request could not be coordinated with a file snapshot operation.|
|439|An unexpected error occurred while processing a file snapshot operation.|
|440|A file snapshot operation received an invalid parameter.|
|441|The operation could not be completed due to one or more unsatisfied dependencies.|
|442|The file cannot be opened because the path has a case-sensitive directory.|
|443|The filesystem couldn't handle one of the CacheManager's callback error codes.|
|444|WSL 2 requires an update to its kernel component. For information please visit https://aka.ms/wsl2kernel|
|445|This action is blocked, but you can choose to allow it. Please refer to the data loss prevention notification for further information.|
|446|This action is blocked. Please refer to the data loss prevention notification for further information.|
|447|Access is denied because the file contains potentially unwanted software or content the security administrator decided to block.|
|448|The path cannot be traversed because it contains an untrusted mount point.|
|449|This action is blocked. Please refer to the data loss prevention notification for further information.|
|450|Neither developer unlocked mode nor side loading mode is enabled on the device.|
|451|Can not change application type during upgrade or re-provision.|
|452|The application has not been provisioned.|
|453|The requested capability can not be authorized for this application.|
|454|There is no capability authorization policy on the device.|
|455|The capability authorization database has been corrupted.|
|456|The custom capability's SCCD has an invalid catalog.|
|457|None of the authorized entity elements in the SCCD matched the app being installed; either the PFNs don't match, or the element's signature hash doesn't validate.|
|458|The custom capability's SCCD failed to parse.|
|459|The custom capability's SCCD requires developer mode.|
|460|There not all declared custom capabilities are found in the SCCD.|
|470|The CimFS image is corrupt.|
|471|The system does not support this version of the CimFS image.|
|472|The storage stack returned STATUS_ACCESS_DENEID for the current operation.|
|473|Insufficient Virtual Address resources to complete the operation.|
|474|The specified index is beyond the bounds of valid range.|
|475|The cloud provider failed to acknowledge a message before the time-out expired.|
|480|The operation timed out waiting for this device to complete a PnP query-remove request due to a potential hang in its device stack. The system may need to be rebooted to complete the request.|
|481|The operation timed out waiting for this device to complete a PnP query-remove request due to a potential hang in the device stack of a related device. The system may need to be rebooted to complete the operation.|
|482|The operation timed out waiting for this device to complete a PnP query-remove request due to a potential hang in the device stack of an unrelated device. The system may need to be rebooted to complete the operation.|
|483|The request failed due to a fatal device hardware error.|
|487|Attempt to access invalid address.|
|488|The volume contains paging, crash dump or other system critical files.|
|489|The specified operation is not supported on an encrypted file.|
|490|The specified operation is not supported on a sparse file.|
|491|The specified operation is not supported on a pagefile.|
|492|The specified operation is not supported on a volume.|
|493|The specified operation is not supported on a BypassIO enabled file.|
|494|The specified driver does not support BypassIO operations.|
|495|The specified operation is not supported while encryption is enabled on the target object.|
|496|The specified operation is not supported while compression is enabled on the target object.|
|497|The specified operation is not supported while replication is enabled on the target object.|
|498|The specified operation is not supported while deduplication is enabled on the target object.|
|499|The specified operation is not supported while auditing is enabled on the target object.|
|500|User profile cannot be loaded.|
|501|The negotiated session key does not meet the minimum length requirement.|
|502|Access denied when accessing the user profile.|
|503|The specified operation is not supported while monitoring is enabled on the target object.|
|504|The specified operation is not supported while snapshot is enabled on the target object.|
|505|The specified operation is not supported while virtualization is enabled on the target object.|
|506|At least one minifilter does not support bypass IO.|
|507|The device needs to be reset.|
|508|The volume is opened for exclusive write access, preventing files from being opened for write access.|
|509|The specified operation is not supported on a file opened for cached IO.|
|510|The file system encountered a metadata file with inconsistent data.|
|511|A file system block being referenced has been modified after containing a weak reference.|
|512|The source file system block being referenced has been modified after containing a weak reference.|
|513|The target file system block being referenced has been modified after containing a weak reference.|
|514|The target file system block is shared between multiple extents.|
|534|Arithmetic result exceeded 32 bits.|
|535|There is a process on other end of the pipe.|
|536|Waiting for a process to open the other end of the pipe.|
|537|Application verifier has found an error in the current process.|
|538|An error occurred in the ABIOS subsystem.|
|539|A warning occurred in the WX86 subsystem.|
|540|An error occurred in the WX86 subsystem.|
|541|An attempt was made to cancel or set a timer that has an associated APC and the subject thread is not the thread that originally set the timer with an associated APC routine.|
|542|Unwind exception code.|
|543|An invalid or unaligned stack was encountered during an unwind operation.|
|544|An invalid unwind target was encountered during an unwind operation.|
|545|Invalid Object Attributes specified to NtCreatePort or invalid Port Attributes specified to NtConnectPort|
|546|Length of message passed to NtRequestPort or NtRequestWaitReplyPort was longer than the maximum message allowed by the port.|
|547|An attempt was made to lower a quota limit below the current usage.|
|548|An attempt was made to attach to a device that was already attached to another device.|
|549|An attempt was made to execute an instruction at an unaligned address and the host system does not support unaligned instruction references.|
|550|Profiling not started.|
|551|Profiling not stopped.|
|552|The passed ACL did not contain the minimum required information.|
|553|The number of active profiling objects is at the maximum and no more may be started.|
|554|Used to indicate that an operation cannot continue without blocking for I/O.|
|555|Indicates that a thread attempted to terminate itself by default (called NtTerminateThread with NULL) and it was the last thread in the current process.|
|556|If an MM error is returned which is not defined in the standard FsRtl filter, it is converted to one of the following errors which is guaranteed to be in the filter.<br>In this case information is lost, however, the filter correctly handles the exception.|
|557|If an MM error is returned which is not defined in the standard FsRtl filter, it is converted to one of the following errors which is guaranteed to be in the filter.<br>In this case information is lost, however, the filter correctly handles the exception.|
|558|If an MM error is returned which is not defined in the standard FsRtl filter, it is converted to one of the following errors which is guaranteed to be in the filter.<br>In this case information is lost, however, the filter correctly handles the exception.|
|559|A malformed function table was encountered during an unwind operation.|
|560|Indicates that an attempt was made to assign protection to a file system file or directory and one of the SIDs in the security descriptor could not be translated into a GUID that could be stored by the file system.<br>This causes the protection attempt to fail, which may cause a file creation attempt to fail.|
|561|Indicates that an attempt was made to grow an LDT by setting its size, or that the size was not an even number of selectors.|
|563|Indicates that the starting value for the LDT information was not an integral multiple of the selector size.|
|564|Indicates that the user supplied an invalid descriptor when trying to set up Ldt descriptors.|
|565|Indicates a process has too many threads to perform the requested action. For example, assignment of a primary token may only be performed when a process has zero or one threads.|
|566|An attempt was made to operate on a thread within a specific process, but the thread specified is not in the process specified.|
|567|Pagefile quota was exceeded.|
|568|The Netlogon service cannot start because another Netlogon service running in the domain conflicts with the specified role.|
|569|The SAM database on a Windows Server is significantly out of synchronization with the copy on the Domain Controller. A complete synchronization is required.|
|570|The NtCreateFile API failed. This error should never be returned to an application, it is a place holder for the Windows Lan Manager Redirector to use in its internal error mapping routines.|
|571|{Privilege Failed}<br>The I/O permissions for the process could not be changed.|
|572|{Application Exit by CTRL+C}<br>The application terminated as a result of a CTRL+C.|
|573|{Missing System File}<br>The required system file %hs is bad or missing.|
|574|{Application Error}<br>The exception %s (0x|
|575|{Application Error}<br>The application was unable to start correctly (0x%lx). Click OK to close the application.|
|576|{Unable to Create Paging File}<br>The creation of the paging file %hs failed (%lx). The requested size was %ld.|
|577|Windows cannot verify the digital signature for this file. A recent hardware or software change might have installed a file that is signed incorrectly or damaged, or that might be malicious software from an unknown source.|
|578|{No Paging File Specified}<br>No paging file was specified in the system configuration.|
|579|{EXCEPTION}<br>A real-mode application issued a floating-point instruction and floating-point hardware is not present.|
|580|An event pair synchronization operation was performed using the thread specific client/server event pair object, but no event pair object was associated with the thread.|
|581|A Windows Server has an incorrect configuration.|
|582|An illegal character was encountered. For a multi-byte character set this includes a lead byte without a succeeding trail byte. For the Unicode character set this includes the characters 0xFFFF and 0xFFFE.|
|583|The Unicode character is not defined in the Unicode character set installed on the system.|
|584|The paging file cannot be created on a floppy diskette.|
|585|The system BIOS failed to connect a system interrupt to the device or bus for which the device is connected.|
|586|This operation is only allowed for the Primary Domain Controller of the domain.|
|587|An attempt was made to acquire a mutant such that its maximum count would have been exceeded.|
|588|A volume has been accessed for which a file system driver is required that has not yet been loaded.|
|589|{Registry File Failure}<br>The registry cannot load the hive (file):<br>%hs<br>or its log or alternate.<br>It is corrupt, absent, or not writable.|
|590|{Unexpected Failure in DebugActiveProcess}<br>An unexpected failure occurred while processing a DebugActiveProcess API request. You may choose OK to terminate the process, or Cancel to ignore the error.|
|591|{Fatal System Error}<br>The %hs system process terminated unexpectedly with a status of 0x|
|592|{Data Not Accepted}<br>The TDI client could not handle the data received during an indication.|
|593|NTVDM encountered a hard error.|
|594|{Cancel Timeout}<br>The driver %hs failed to complete a cancelled I/O request in the allotted time.|
|595|{Reply Message Mismatch}<br>An attempt was made to reply to an LPC message, but the thread specified by the client ID in the message was not waiting on that message.|
|596|{Delayed Write Failed}<br>Windows was unable to save all the data for the file %hs. The data has been lost.<br>This error may be caused by a failure of your computer hardware or network connection. Please try to save this file elsewhere.|
|597|The parameter(s) passed to the server in the client/server shared memory window were invalid. Too much data may have been put in the shared memory window.|
|598|The stream is not a tiny stream.|
|599|The request must be handled by the stack overflow code.|
|600|Internal OFS status codes indicating how an allocation operation is handled. Either it is retried after the containing onode is moved or the extent stream is converted to a large stream.|
|601|The attempt to find the object found an object matching by ID on the volume but it is out of the scope of the handle used for the operation.|
|602|The bucket array must be grown. Retry transaction after doing so.|
|603|The user/kernel marshalling buffer has overflowed.|
|604|The supplied variant structure contains invalid data.|
|605|The specified buffer contains ill-formed data.|
|606|{Audit Failed}<br>An attempt to generate a security audit failed.|
|607|The timer resolution was not previously set by the current process.|
|608|There is insufficient account information to log you on.|
|609|{Invalid DLL Entrypoint}<br>The dynamic link library %hs is not written correctly. The stack pointer has been left in an inconsistent state.<br>The entrypoint should be declared as WINAPI or STDCALL. Select YES to fail the DLL load. Select NO to continue execution. Selecting NO may cause the application to operate incorrectly.|
|610|{Invalid Service Callback Entrypoint}<br>The %hs service is not written correctly. The stack pointer has been left in an inconsistent state.<br>The callback entrypoint should be declared as WINAPI or STDCALL. Selecting OK will cause the service to continue operation. However, the service process may operate incorrectly.|
|611|There is an IP address conflict with another system on the network|
|612|There is an IP address conflict with another system on the network|
|613|{Low On Registry Space}<br>The system has reached the maximum size allowed for the system part of the registry. Additional storage requests will be ignored.|
|614|A callback return system service cannot be executed when no callback is active.|
|615|The password provided is too short to meet the policy of your user account.<br>Please choose a longer password.|
|616|The policy of your user account does not allow you to change passwords too frequently.<br>This is done to prevent users from changing back to a familiar, but potentially discovered, password.<br>If you feel your password has been compromised then please contact your administrator immediately to have a new one assigned.|
|617|You have attempted to change your password to one that you have used in the past.<br>The policy of your user account does not allow this. Please select a password that you have not previously used.|
|618|The specified compression format is unsupported.|
|619|The specified hardware profile configuration is invalid.|
|620|The specified Plug and Play registry device path is invalid.|
|621|The specified quota list is internally inconsistent with its descriptor.|
|622|{Windows Evaluation Notification}<br>The evaluation period for this installation of Windows has expired. This system will shutdown in 1 hour. To restore access to this installation of Windows, please upgrade this installation using a licensed distribution of this product.|
|623|{Illegal System DLL Relocation}<br>The system DLL %hs was relocated in memory. The application will not run properly.<br>The relocation occurred because the DLL %hs occupied an address range reserved for Windows system DLLs. The vendor supplying the DLL should be contacted for a new DLL.|
|624|{DLL Initialization Failed}<br>The application failed to initialize because the window station is shutting down.|
|625|The validation process needs to continue on to the next step.|
|626|There are no more matches for the current index enumeration.|
|627|The range could not be added to the range list because of a conflict.|
|628|The server process is running under a SID different than that required by client.|
|629|A group marked use for deny only cannot be enabled.|
|630|{EXCEPTION}<br>Multiple floating point faults.|
|631|{EXCEPTION}<br>Multiple floating point traps.|
|632|The requested interface is not supported.|
|633|{System Standby Failed}<br>The driver %hs does not support standby mode. Updating this driver may allow the system to go to standby mode.|
|634|The system file %1 has become corrupt and has been replaced.|
|635|{Virtual Memory Minimum Too Low}<br>Your system is low on virtual memory. Windows is increasing the size of your virtual memory paging file.<br>During this process, memory requests for some applications may be denied. For more information, see Help.|
|636|A device was removed so enumeration must be restarted.|
|637|{Fatal System Error}<br>The system image %s is not properly signed.<br>The file has been replaced with the signed file.<br>The system has been shut down.|
|638|Device will not start without a reboot.|
|639|There is not enough power to complete the requested operation.|
|640|ERROR_MULTIPLE_FAULT_VIOLATION|
|641|The system is in the process of shutting down.|
|642|An attempt to remove a processes DebugPort was made, but a port was not already associated with the process.|
|643|This version of Windows is not compatible with the behavior version of directory forest, domain or domain controller.|
|644|The specified range could not be found in the range list.|
|646|The driver was not loaded because the system is booting into safe mode.|
|647|The driver was not loaded because it failed its initialization call.|
|648|The "%hs" encountered an error while applying power or reading the device configuration.<br>This may be caused by a failure of your hardware or by a poor connection.|
|649|The create operation failed because the name contained at least one mount point which resolves to a volume to which the specified device object is not attached.|
|650|The device object parameter is either not a valid device object or is not attached to the volume specified by the file name.|
|651|A Machine Check Error has occurred. Please check the system eventlog for additional information.|
|652|There was error [%2] processing the driver database.|
|653|System hive size has exceeded its limit.|
|654|The driver could not be loaded because a previous version of the driver is still in memory.|
|655|{Volume Shadow Copy Service}<br>Please wait while the Volume Shadow Copy Service prepares volume %hs for hibernation.|
|656|The system has failed to hibernate (The error code is %hs). Hibernation will be disabled until the system is restarted.|
|657|The password provided is too long to meet the policy of your user account.<br>Please choose a shorter password.|
|665|The requested operation could not be completed due to a file system limitation|
|668|An assertion failure has occurred.|
|669|An error occurred in the ACPI subsystem.|
|670|WOW Assertion Error.|
|671|A device is missing in the system BIOS MPS table. This device will not be used.<br>Please contact your system vendor for system BIOS update.|
|672|A translator failed to translate resources.|
|673|A IRQ translator failed to translate resources.|
|674|Driver %2 returned invalid ID for a child device (%3).|
|675|{Kernel Debugger Awakened}<br>the system debugger was awakened by an interrupt.|
|676|{Handles Closed}<br>Handles to objects have been automatically closed as a result of the requested operation.|
|677|{Too Much Information}<br>The specified access control list (ACL) contained more information than was expected.|
|678|This warning level status indicates that the transaction state already exists for the registry sub-tree, but that a transaction commit was previously aborted.<br>The commit has NOT been completed, but has not been rolled back either (so it may still be committed if desired).|
|679|{Media Changed}<br>The media may have changed.|
|680|{GUID Substitution}<br>During the translation of a global identifier (GUID) to a Windows security ID (SID), no administratively-defined GUID prefix was found.<br>A substitute prefix was used, which will not compromise system security. However, this may provide a more restrictive access than intended.|
|681|The create operation stopped after reaching a symbolic link|
|682|A long jump has been executed.|
|683|The Plug and Play query operation was not successful.|
|684|A frame consolidation has been executed.|
|685|{Registry Hive Recovered}<br>Registry hive (file):<br>%hs<br>was corrupted and it has been recovered. Some data might have been lost.|
|686|The application is attempting to run executable code from the module %hs. This may be insecure. An alternative, %hs, is available. Should the application use the secure module %hs?|
|687|The application is loading executable code from the module %hs. This is secure, but may be incompatible with previous releases of the operating system. An alternative, %hs, is available. Should the application use the secure module %hs?|
|688|Debugger did not handle the exception.|
|689|Debugger will reply later.|
|690|Debugger cannot provide handle.|
|691|Debugger terminated thread.|
|692|Debugger terminated process.|
|693|Debugger got control C.|
|694|Debugger printed exception on control C.|
|695|Debugger received RIP exception.|
|696|Debugger received control break.|
|697|Debugger command communication exception.|
|698|{Object Exists}<br>An attempt was made to create an object and the object name already existed.|
|699|{Thread Suspended}<br>A thread termination occurred while the thread was suspended. The thread was resumed, and termination proceeded.|
|700|{Image Relocated}<br>An image file could not be mapped at the address specified in the image file. Local fixups must be performed on this image.|
|701|This informational level status indicates that a specified registry sub-tree transaction state did not yet exist and had to be created.|
|702|{Segment Load}<br>A virtual DOS machine (VDM) is loading, unloading, or moving an MS-DOS or Win16 program segment image.<br>An exception is raised so a debugger can load, unload or track symbols and breakpoints within these 16-bit segments.|
|703|{Invalid Current Directory}<br>The process cannot switch to the startup current directory %hs.<br>Select OK to set current directory to %hs, or select CANCEL to exit.|
|704|{Redundant Read}<br>To satisfy a read request, the NT fault-tolerant file system successfully read the requested data from a redundant copy.<br>This was done because the file system encountered a failure on a member of the fault-tolerant volume, but was unable to reassign the failing area of the device.|
|705|{Redundant Write}<br>To satisfy a write request, the NT fault-tolerant file system successfully wrote a redundant copy of the information.<br>This was done because the file system encountered a failure on a member of the fault-tolerant volume, but was not able to reassign the failing area of the device.|
|706|{Machine Type Mismatch}<br>The image file %hs is valid, but is for a machine type other than the current machine. Select OK to continue, or CANCEL to fail the DLL load.|
|707|{Partial Data Received}<br>The network transport returned partial data to its client. The remaining data will be sent later.|
|708|{Expedited Data Received}<br>The network transport returned data to its client that was marked as expedited by the remote system.|
|709|{Partial Expedited Data Received}<br>The network transport returned partial data to its client and this data was marked as expedited by the remote system. The remaining data will be sent later.|
|710|{TDI Event Done}<br>The TDI indication has completed successfully.|
|711|{TDI Event Pending}<br>The TDI indication has entered the pending state.|
|712|Checking file system on %wZ|
|713|{Fatal Application Exit}<br>%hs|
|714|The specified registry key is referenced by a predefined handle.|
|715|{Page Unlocked}<br>The page protection of a locked page was changed to 'No Access' and the page was unlocked from memory and from the process.|
|716|%hs|
|717|{Page Locked}<br>One of the pages to lock was already locked.|
|718|Application popup: %1 : %2|
|719|ERROR_ALREADY_WIN32|
|720|{Machine Type Mismatch}<br>The image file %hs is valid, but is for a machine type other than the current machine.|
|721|A yield execution was performed and no thread was available to run.|
|722|The resumable flag to a timer API was ignored.|
|723|The arbiter has deferred arbitration of these resources to its parent|
|724|The inserted CardBus device cannot be started because of a configuration error on "%hs".|
|725|The CPUs in this multiprocessor system are not all the same revision level. To use all processors the operating system restricts itself to the features of the least capable processor in the system. Should problems occur with this system, contact the CPU manufacturer to see if this mix of processors is supported.|
|726|The system was put into hibernation.|
|727|The system was resumed from hibernation.|
|728|Windows has detected that the system firmware (BIOS) was updated [previous firmware date = %2, current firmware date %3].|
|729|A device driver is leaking locked I/O pages causing system degradation. The system has automatically enabled tracking code in order to try and catch the culprit.|
|730|The system has awoken|
|731|ERROR_WAIT_1|
|732|ERROR_WAIT_2|
|733|ERROR_WAIT_3|
|734|ERROR_WAIT_63|
|735|ERROR_ABANDONED_WAIT_0|
|736|ERROR_ABANDONED_WAIT_63|
|737|ERROR_USER_APC|
|738|ERROR_KERNEL_APC|
|739|ERROR_ALERTED|
|740|The requested operation requires elevation.|
|741|A reparse should be performed by the Object Manager since the name of the file resulted in a symbolic link.|
|742|An open/create operation completed while an oplock break is underway.|
|743|A new volume has been mounted by a file system.|
|744|This success level status indicates that the transaction state already exists for the registry sub-tree, but that a transaction commit was previously aborted.<br>The commit has now been completed.|
|745|This indicates that a notify change request has been completed due to closing the handle which made the notify change request.|
|746|{Connect Failure on Primary Transport}<br>An attempt was made to connect to the remote server %hs on the primary transport, but the connection failed.<br>The computer WAS able to connect on a secondary transport.|
|747|Page fault was a transition fault.|
|748|Page fault was a demand zero fault.|
|749|Page fault was a demand zero fault.|
|750|Page fault was a demand zero fault.|
|751|Page fault was satisfied by reading from a secondary storage device.|
|752|Cached page was locked during operation.|
|753|Crash dump exists in paging file.|
|754|Specified buffer contains all zeros.|
|755|A reparse should be performed by the Object Manager since the name of the file resulted in a symbolic link.|
|756|The device has succeeded a query-stop and its resource requirements have changed.|
|757|The translator has translated these resources into the global space and no further translations should be performed.|
|758|A process being terminated has no threads to terminate.|
|759|The specified process is not part of a job.|
|760|The specified process is part of a job.|
|761|{Volume Shadow Copy Service}<br>The system is now ready for hibernation.|
|762|A file system or file system filter driver has successfully completed an FsFilter operation.|
|763|The specified interrupt vector was already connected.|
|764|The specified interrupt vector is still connected.|
|765|An operation is blocked waiting for an oplock.|
|766|Debugger handled exception|
|767|Debugger continued|
|768|An exception occurred in a user mode callback and the kernel callback frame should be removed.|
|769|Compression is disabled for this volume.|
|770|The data provider cannot fetch backwards through a result set.|
|771|The data provider cannot scroll backwards through a result set.|
|772|The data provider requires that previously fetched data is released before asking for more data.|
|773|The data provider was not able to interpret the flags set for a column binding in an accessor.|
|774|One or more errors occurred while processing the request.|
|775|The implementation is not capable of performing the request.|
|776|The client of a component requested an operation which is not valid given the state of the component instance.|
|777|A version number could not be parsed.|
|778|The iterator's start position is invalid.|
|779|The hardware has reported an uncorrectable memory error.|
|780|The attempted operation required self healing to be enabled.|
|781|The Desktop heap encountered an error while allocating session memory. There is more information in the system event log.|
|782|The system power state is transitioning from %2 to %3.|
|783|The system power state is transitioning from %2 to %3 but could enter %4.|
|784|A thread is getting dispatched with MCA EXCEPTION because of MCA.|
|785|Access to %1 is monitored by policy rule %2.|
|786|Access to %1 has been restricted by your Administrator by policy rule %2.|
|787|A valid hibernation file has been invalidated and should be abandoned.|
|788|{Delayed Write Failed}<br>Windows was unable to save all the data for the file %hs; the data has been lost.<br>This error may be caused by network connectivity issues. Please try to save this file elsewhere.|
|789|{Delayed Write Failed}<br>Windows was unable to save all the data for the file %hs; the data has been lost.<br>This error was returned by the server on which the file exists. Please try to save this file elsewhere.|
|790|{Delayed Write Failed}<br>Windows was unable to save all the data for the file %hs; the data has been lost.<br>This error may be caused if the device has been removed or the media is write-protected.|
|791|The resources required for this device conflict with the MCFG table.|
|792|The volume repair could not be performed while it is online.<br>Please schedule to take the volume offline so that it can be repaired.|
|793|The volume repair was not successful.|
|794|One of the volume corruption logs is full. Further corruptions that may be detected won't be logged.|
|795|One of the volume corruption logs is internally corrupted and needs to be recreated. The volume may contain undetected corruptions and must be scanned.|
|796|One of the volume corruption logs is unavailable for being operated on.|
|797|One of the volume corruption logs was deleted while still having corruption records in them. The volume contains detected corruptions and must be scanned.|
|798|One of the volume corruption logs was cleared by chkdsk and no longer contains real corruptions.|
|799|Orphaned files exist on the volume but could not be recovered because no more new names could be created in the recovery directory. Files must be moved from the recovery directory.|
|800|The oplock that was associated with this handle is now associated with a different handle.|
|801|An oplock of the requested level cannot be granted.  An oplock of a lower level may be available.|
|802|The operation did not complete successfully because it would cause an oplock to be broken. The caller has requested that existing oplocks not be broken.|
|803|The handle with which this oplock was associated has been closed.  The oplock is now broken.|
|804|The specified access control entry (ACE) does not contain a condition.|
|805|The specified access control entry (ACE) contains an invalid condition.|
|806|Access to the specified file handle has been revoked.|
|807|{Image Relocated}<br>An image file was mapped at a different address from the one specified in the image file but fixups will still be automatically performed on the image.|
|808|The read or write operation to an encrypted file could not be completed because the file has not been opened for data access.|
|809|File metadata optimization is already in progress.|
|810|The requested operation failed due to quota operation is still in progress.|
|811|Access to the specified handle has been revoked.|
|812|The callback function must be invoked inline.|
|813|The specified CPU Set IDs are invalid.|
|814|The specified enclave has not yet been terminated.|
|815|An attempt was made to access protected memory in violation of its secure access policy.|
|816|Multiple mappings to shared resource(s) on a server, using more than one transport, are not allowed. Use a single transport for all mappings to a server and try again.|
|817|Multiple mappings to shared resource(s) on a server, using different certificate validation preferences, are not allowed. Use the same preference for all mappings to a server and try again.|
|818|The specified copy of the requested data could not be read.|
|819|The section creation request was failed because it would have been satisfied with a direct map and the caller explicitly signified this was not wanted.|
|994|Access to the extended attribute was denied.|
|995|The I/O operation has been aborted because of either a thread exit or an application request.|
|996|Overlapped I/O event is not in a signaled state.|
|997|Overlapped I/O operation is in progress.|
|998|Invalid access to memory location.|
|999|Error performing inpage operation.|
|1001|Recursion too deep; the stack overflowed.|
|1002|The window cannot act on the sent message.|
|1003|Cannot complete this function.|
|1004|Invalid flags.|
|1005|The volume does not contain a recognized file system.<br>Please make sure that all required file system drivers are loaded and that the volume is not corrupted.|
|1006|The volume for a file has been externally altered so that the opened file is no longer valid.|
|1007|The requested operation cannot be performed in full-screen mode.|
|1008|An attempt was made to reference a token that does not exist.|
|1009|The configuration registry database is corrupt.|
|1010|The configuration registry key is invalid.|
|1011|The configuration registry key could not be opened.|
|1012|The configuration registry key could not be read.|
|1013|The configuration registry key could not be written.|
|1014|One of the files in the registry database had to be recovered by use of a log or alternate copy. The recovery was successful.|
|1015|The registry is corrupted. The structure of one of the files containing registry data is corrupted, or the system's memory image of the file is corrupted, or the file could not be recovered because the alternate copy or log was absent or corrupted.|
|1016|An I/O operation initiated by the registry failed unrecoverably. The registry could not read in, or write out, or flush, one of the files that contain the system's image of the registry.|
|1017|The system has attempted to load or restore a file into the registry, but the specified file is not in a registry file format.|
|1018|Illegal operation attempted on a registry key that has been marked for deletion.|
|1019|System could not allocate the required space in a registry log.|
|1020|Cannot create a symbolic link in a registry key that already has subkeys or values.|
|1021|Cannot create a stable subkey under a volatile parent key.|
|1022|A notify change request is being completed and the information is not being returned in the caller's buffer. The caller now needs to enumerate the files to find the changes.|
|1051|A stop control has been sent to a service that other running services are dependent on.|
|1052|The requested control is not valid for this service.|
|1053|The service did not respond to the start or control request in a timely fashion.|
|1054|A thread could not be created for the service.|
|1055|The service database is locked.|
|1056|An instance of the service is already running.|
|1057|The account name is invalid or does not exist, or the password is invalid for the account name specified.|
|1058|The service cannot be started, either because it is disabled or because it has no enabled devices associated with it.|
|1059|Circular service dependency was specified.|
|1060|The specified service does not exist as an installed service.|
|1061|The service cannot accept control messages at this time.|
|1062|The service has not been started.|
|1063|The service process could not connect to the service controller.|
|1064|An exception occurred in the service when handling the control request.|
|1065|The database specified does not exist.|
|1066|The service has returned a service-specific error code.|
|1067|The process terminated unexpectedly.|
|1068|The dependency service or group failed to start.|
|1069|The service did not start due to a logon failure.|
|1070|After starting, the service hung in a start-pending state.|
|1071|The specified service database lock is invalid.|
|1072|The specified service has been marked for deletion.|
|1073|The specified service already exists.|
|1074|The system is currently running with the last-known-good configuration.|
|1075|The dependency service does not exist or has been marked for deletion.|
|1076|The current boot has already been accepted for use as the last-known-good control set.|
|1077|No attempts to start the service have been made since the last boot.|
|1078|The name is already in use as either a service name or a service display name.|
|1079|The account specified for this service is different from the account specified for other services running in the same process.|
|1080|Failure actions can only be set for Win32 services, not for drivers.|
|1081|This service runs in the same process as the service control manager.<br>Therefore, the service control manager cannot take action if this service's process terminates unexpectedly.|
|1082|No recovery program has been configured for this service.|
|1083|The executable program that this service is configured to run in does not implement the service.|
|1084|This service cannot be started in Safe Mode|
|1100|The physical end of the tape has been reached.|
|1101|A tape access reached a filemark.|
|1102|The beginning of the tape or a partition was encountered.|
|1103|A tape access reached the end of a set of files.|
|1104|No more data is on the tape.|
|1105|Tape could not be partitioned.|
|1106|When accessing a new tape of a multivolume partition, the current block size is incorrect.|
|1107|Tape partition information could not be found when loading a tape.|
|1108|Unable to lock the media eject mechanism.|
|1109|Unable to unload the media.|
|1110|The media in the drive may have changed.|
|1111|The I/O bus was reset.|
|1112|No media in drive.|
|1113|No mapping for the Unicode character exists in the target multi-byte code page.|
|1114|A dynamic link library (DLL) initialization routine failed.|
|1115|A system shutdown is in progress.|
|1116|Unable to abort the system shutdown because no shutdown was in progress.|
|1117|The request could not be performed because of an I/O device error.|
|1118|No serial device was successfully initialized. The serial driver will unload.|
|1119|Unable to open a device that was sharing an interrupt request (IRQ) with other devices. At least one other device that uses that IRQ was already opened.|
|1120|A serial I/O operation was completed by another write to the serial port.<br>(The IOCTL_SERIAL_XOFF_COUNTER reached zero.)|
|1121|A serial I/O operation completed because the timeout period expired.<br>(The IOCTL_SERIAL_XOFF_COUNTER did not reach zero.)|
|1122|No ID address mark was found on the floppy disk.|
|1123|Mismatch between the floppy disk sector ID field and the floppy disk controller track address.|
|1124|The floppy disk controller reported an error that is not recognized by the floppy disk driver.|
|1125|The floppy disk controller returned inconsistent results in its registers.|
|1126|While accessing the hard disk, a recalibrate operation failed, even after retries.|
|1127|While accessing the hard disk, a disk operation failed even after retries.|
|1128|While accessing the hard disk, a disk controller reset was needed, but even that failed.|
|1129|Physical end of tape encountered.|
|1130|Not enough server memory resources are available to process this command.|
|1131|A potential deadlock condition has been detected.|
|1132|The base address or the file offset specified does not have the proper alignment.|
|1140|An attempt to change the system power state was vetoed by another application or driver.|
|1141|The system BIOS failed an attempt to change the system power state.|
|1142|An attempt was made to create more links on a file than the file system supports.|
|1150|The specified program requires a newer version of Windows.|
|1151|The specified program is not a Windows or MS-DOS program.|
|1152|Cannot start more than one instance of the specified program.|
|1153|The specified program was written for an earlier version of Windows.|
|1154|One of the library files needed to run this application is damaged.|
|1155|No application is associated with the specified file for this operation.|
|1156|An error occurred in sending the command to the application.|
|1157|One of the library files needed to run this application cannot be found.|
|1158|The current process has used all of its system allowance of handles for Window Manager objects.|
|1159|The message can be used only with synchronous operations.|
|1160|The indicated source element has no media.|
|1161|The indicated destination element already contains media.|
|1162|The indicated element does not exist.|
|1163|The indicated element is part of a magazine that is not present.|
|1164|The indicated device requires reinitialization due to hardware errors.|
|1165|The device has indicated that cleaning is required before further operations are attempted.|
|1166|The device has indicated that its door is open.|
|1167|The device is not connected.|
|1168|Element not found.|
|1169|There was no match for the specified key in the index.|
|1170|The property set specified does not exist on the object.|
|1171|The point passed to GetMouseMovePoints is not in the buffer.|
|1172|The tracking (workstation) service is not running.|
|1173|The Volume ID could not be found.|
|1175|Unable to remove the file to be replaced.|
|1176|Unable to move the replacement file to the file to be replaced. The file to be replaced has retained its original name.|
|1177|Unable to move the replacement file to the file to be replaced. The file to be replaced has been renamed using the backup name.|
|1178|The volume change journal is being deleted.|
|1179|The volume change journal is not active.|
|1180|A file was found, but it may not be the correct file.|
|1181|The journal entry has been deleted from the journal.|
|1184|An attempt was made to access a partition that has begun termination.|
|1190|A system shutdown has already been scheduled.|
|1191|The system shutdown cannot be initiated because there are other users logged on to the computer.|
|1192|The system shutdown cannot safely proceed without enabling node maintenance mode for cluster node and waiting for the drain to complete.|
|1200|The specified device name is invalid.|
|1201|The device is not currently connected but it is a remembered connection.|
|1202|The local device name has a remembered connection to another network resource.|
|1203|The network path was either typed incorrectly, does not exist, or the network provider is not currently available. Please try retyping the path or contact your network administrator.|
|1204|The specified network provider name is invalid.|
|1205|Unable to open the network connection profile.|
|1206|The network connection profile is corrupted.|
|1207|Cannot enumerate a noncontainer.|
|1208|An extended error has occurred.|
|1209|The format of the specified group name is invalid.|
|1210|The format of the specified computer name is invalid.|
|1211|The format of the specified event name is invalid.|
|1212|The format of the specified domain name is invalid.|
|1213|The format of the specified service name is invalid.|
|1214|The format of the specified network name is invalid.|
|1215|The format of the specified share name is invalid.|
|1216|The format of the specified password is invalid.|
|1217|The format of the specified message name is invalid.|
|1218|The format of the specified message destination is invalid.|
|1219|Multiple connections to a server or shared resource by the same user, using more than one user name, are not allowed. Disconnect all previous connections to the server or shared resource and try again.|
|1220|An attempt was made to establish a session to a network server, but there are already too many sessions established to that server.|
|1221|The workgroup or domain name is already in use by another computer on the network.|
|1222|The network is not present or not started.|
|1223|The operation was canceled by the user.|
|1224|The requested operation cannot be performed on a file with a user-mapped section open.|
|1225|The remote computer refused the network connection.|
|1226|The network connection was gracefully closed.|
|1227|The network transport endpoint already has an address associated with it.|
|1228|An address has not yet been associated with the network endpoint.|
|1229|An operation was attempted on a nonexistent network connection.|
|1230|An invalid operation was attempted on an active network connection.|
|1231|The network location cannot be reached. For information about network troubleshooting, see Windows Help.|
|1232|The network location cannot be reached. For information about network troubleshooting, see Windows Help.|
|1233|The network location cannot be reached. For information about network troubleshooting, see Windows Help.|
|1234|No service is operating at the destination network endpoint on the remote system.|
|1235|The request was aborted.|
|1236|The network connection was aborted by the local system.|
|1237|The operation could not be completed. A retry should be performed.|
|1238|A connection to the server could not be made because the limit on the number of concurrent connections for this account has been reached.|
|1239|Attempting to log in during an unauthorized time of day for this account.|
|1240|The account is not authorized to log in from this station.|
|1241|The network address could not be used for the operation requested.|
|1242|The service is already registered.|
|1243|The specified service does not exist.|
|1244|The operation being requested was not performed because the user has not been authenticated.|
|1245|The operation being requested was not performed because the user has not logged on to the network. The specified service does not exist.|
|1246|Continue with work in progress.|
|1247|An attempt was made to perform an initialization operation when initialization has already been completed.|
|1248|No more local devices.|
|1249|The specified site does not exist.|
|1250|A domain controller with the specified name already exists.|
|1251|This operation is supported only when you are connected to the server.|
|1252|The group policy framework should call the extension even if there are no changes.|
|1253|The specified user does not have a valid profile.|
|1254|This operation is not supported on a computer running Windows Server 2003 for Small Business Server|
|1255|The server machine is shutting down.|
|1256|The remote system is not available. For information about network troubleshooting, see Windows Help.|
|1257|The security identifier provided is not from an account domain.|
|1258|The security identifier provided does not have a domain component.|
|1259|AppHelp dialog canceled thus preventing the application from starting.|
|1260|This program is blocked by group policy. For more information, contact your system administrator.|
|1261|A program attempt to use an invalid register value. Normally caused by an uninitialized register. This error is Itanium specific.|
|1262|The share is currently offline or does not exist.|
|1263|The Kerberos protocol encountered an error while validating the KDC certificate during smartcard logon. There is more information in the system event log.|
|1264|The Kerberos protocol encountered an error while attempting to utilize the smartcard subsystem.|
|1265|The system cannot contact a domain controller to service the authentication request. Please try again later.|
|1271|The machine is locked and cannot be shut down without the force option.|
|1272|You can't access this shared folder because your organization's security policies block unauthenticated guest access. These policies help protect your PC from unsafe or malicious devices on the network.|
|1273|An application-defined callback gave invalid data when called.|
|1274|The group policy framework should call the extension in the synchronous foreground policy refresh.|
|1275|This driver has been blocked from loading|
|1276|A dynamic link library (DLL) referenced a module that was neither a DLL nor the process's executable image.|
|1277|Windows cannot open this program since it has been disabled.|
|1278|Windows cannot open this program because the license enforcement system has been tampered with or become corrupted.|
|1279|A transaction recover failed.|
|1280|The current thread has already been converted to a fiber.|
|1281|The current thread has already been converted from a fiber.|
|1282|The system detected an overrun of a stack-based buffer in this application. This overrun could potentially allow a malicious user to gain control of this application.|
|1283|Data present in one of the parameters is more than the function can operate on.|
|1284|An attempt to do an operation on a debug object failed because the object is in the process of being deleted.|
|1285|An attempt to delay-load a .dll or get a function address in a delay-loaded .dll failed.|
|1286|%1 is a 16-bit application. You do not have permissions to execute 16-bit applications. Check your permissions with your system administrator.|
|1287|Insufficient information exists to identify the cause of failure.|
|1288|The parameter passed to a C runtime function is incorrect.|
|1289|The operation occurred beyond the valid data length of the file.|
|1290|The service start failed since one or more services in the same process have an incompatible service SID type setting. A service with restricted service SID type can only coexist in the same process with other services with a restricted SID type. If the service SID type for this service was just configured, the hosting process must be restarted in order to start this service.|
|1291|The process hosting the driver for this device has been terminated.|
|1292|An operation attempted to exceed an implementation-defined limit.|
|1293|Either the target process, or the target thread's containing process, is a protected process.|
|1294|The service notification client is lagging too far behind the current state of services in the machine.|
|1295|The requested file operation failed because the storage quota was exceeded.<br>To free up disk space, move files to a different location or delete unnecessary files. For more information, contact your system administrator.|
|1296|The requested file operation failed because the storage policy blocks that type of file. For more information, contact your system administrator.|
|1297|A privilege that the service requires to function properly does not exist in the service account configuration.<br>You may use the Services Microsoft Management Console (MMC) snap-in (services.msc) and the Local Security Settings MMC snap-in (secpol.msc) to view the service configuration and the account configuration.|
|1298|A thread involved in this operation appears to be unresponsive.|
|1299|Indicates a particular Security ID may not be assigned as the label of an object.|
|1300|Not all privileges or groups referenced are assigned to the caller.|
|1301|Some mapping between account names and security IDs was not done.|
|1302|No system quota limits are specifically set for this account.|
|1303|No encryption key is available. A well-known encryption key was returned.|
|1304|The password is too complex to be converted to a LAN Manager password. The LAN Manager password returned is a NULL string.|
|1305|The revision level is unknown.|
|1306|Indicates two revision levels are incompatible.|
|1307|This security ID may not be assigned as the owner of this object.|
|1308|This security ID may not be assigned as the primary group of an object.|
|1309|An attempt has been made to operate on an impersonation token by a thread that is not currently impersonating a client.|
|1310|The group may not be disabled.|
|1311|We can't sign you in with this credential because your domain isn't available. Make sure your device is connected to your organization's network and try again. If you previously signed in on this device with another credential, you can sign in with that credential.|
|1312|A specified logon session does not exist. It may already have been terminated.|
|1313|A specified privilege does not exist.|
|1314|A required privilege is not held by the client.|
|1315|The name provided is not a properly formed account name.|
|1316|The specified account already exists.|
|1317|The specified account does not exist.|
|1318|The specified group already exists.|
|1319|The specified group does not exist.|
|1320|Either the specified user account is already a member of the specified group, or the specified group cannot be deleted because it contains a member.|
|1321|The specified user account is not a member of the specified group account.|
|1322|This operation is disallowed as it could result in an administration account being disabled, deleted or unable to logon.|
|1323|Unable to update the password. The value provided as the current password is incorrect.|
|1324|Unable to update the password. The value provided for the new password contains values that are not allowed in passwords.|
|1325|Unable to update the password. The value provided for the new password does not meet the length, complexity, or history requirements of the domain.|
|1326|The user name or password is incorrect.|
|1327|Account restrictions are preventing this user from signing in. For example: blank passwords aren't allowed, sign-in times are limited, or a policy restriction has been enforced.|
|1328|Your account has time restrictions that keep you from signing in right now.|
|1329|This user isn't allowed to sign in to this computer.|
|1330|The password for this account has expired.|
|1331|This user can't sign in because this account is currently disabled.|
|1332|No mapping between account names and security IDs was done.|
|1333|Too many local user identifiers (LUIDs) were requested at one time.|
|1334|No more local user identifiers (LUIDs) are available.|
|1335|The subauthority part of a security ID is invalid for this particular use.|
|1336|The access control list (ACL) structure is invalid.|
|1337|The security ID structure is invalid.|
|1338|The security descriptor structure is invalid.|
|1340|The inherited access control list (ACL) or access control entry (ACE) could not be built.|
|1341|The server is currently disabled.|
|1342|The server is currently enabled.|
|1343|The value provided was an invalid value for an identifier authority.|
|1344|No more memory is available for security information updates.|
|1345|The specified attributes are invalid, or incompatible with the attributes for the group as a whole.|
|1346|Either a required impersonation level was not provided, or the provided impersonation level is invalid.|
|1347|Cannot open an anonymous level security token.|
|1348|The validation information class requested was invalid.|
|1349|The type of the token is inappropriate for its attempted use.|
|1350|Unable to perform a security operation on an object that has no associated security.|
|1351|Configuration information could not be read from the domain controller, either because the machine is unavailable, or access has been denied.|
|1352|The security account manager (SAM) or local security authority (LSA) server was in the wrong state to perform the security operation.|
|1353|The domain was in the wrong state to perform the security operation.|
|1354|This operation is only allowed for the Primary Domain Controller of the domain.|
|1355|The specified domain either does not exist or could not be contacted.|
|1356|The specified domain already exists.|
|1357|An attempt was made to exceed the limit on the number of domains per server.|
|1358|Unable to complete the requested operation because of either a catastrophic media failure or a data structure corruption on the disk.|
|1359|An internal error occurred.|
|1360|Generic access types were contained in an access mask which should already be mapped to nongeneric types.|
|1361|A security descriptor is not in the right format (absolute or self-relative).|
|1362|The requested action is restricted for use by logon processes only. The calling process has not registered as a logon process.|
|1363|Cannot start a new logon session with an ID that is already in use.|
|1364|A specified authentication package is unknown.|
|1365|The logon session is not in a state that is consistent with the requested operation.|
|1366|The logon session ID is already in use.|
|1367|A logon request contained an invalid logon type value.|
|1368|Unable to impersonate using a named pipe until data has been read from that pipe.|
|1369|The transaction state of a registry subtree is incompatible with the requested operation.|
|1370|An internal security database corruption has been encountered.|
|1371|Cannot perform this operation on built-in accounts.|
|1372|Cannot perform this operation on this built-in special group.|
|1373|Cannot perform this operation on this built-in special user.|
|1374|The user cannot be removed from a group because the group is currently the user's primary group.|
|1375|The token is already in use as a primary token.|
|1376|The specified local group does not exist.|
|1377|The specified account name is not a member of the group.|
|1378|The specified account name is already a member of the group.|
|1379|The specified local group already exists.|
|1380|Logon failure: the user has not been granted the requested logon type at this computer.|
|1381|The maximum number of secrets that may be stored in a single system has been exceeded.|
|1382|The length of a secret exceeds the maximum length allowed.|
|1383|The local security authority database contains an internal inconsistency.|
|1384|During a logon attempt, the user's security context accumulated too many security IDs.|
|1385|Logon failure: the user has not been granted the requested logon type at this computer.|
|1386|A cross-encrypted password is necessary to change a user password.|
|1387|A member could not be added to or removed from the local group because the member does not exist.|
|1388|A new member could not be added to a local group because the member has the wrong account type.|
|1389|Too many security IDs have been specified.|
|1390|A cross-encrypted password is necessary to change this user password.|
|1391|Indicates an ACL contains no inheritable components.|
|1392|The file or directory is corrupted and unreadable.|
|1393|The disk structure is corrupted and unreadable.|
|1394|There is no user session key for the specified logon session.|
|1395|The service being accessed is licensed for a particular number of connections. No more connections can be made to the service at this time because there are already as many connections as the service can accept.|
|1396|The target account name is incorrect.|
|1397|Mutual Authentication failed. The server's password is out of date at the domain controller.|
|1398|There is a time and/or date difference between the client and server.|
|1399|This operation cannot be performed on the current domain.|
|1400|Invalid window handle.|
|1401|Invalid menu handle.|
|1402|Invalid cursor handle.|
|1403|Invalid accelerator table handle.|
|1404|Invalid hook handle.|
|1405|Invalid handle to a multiple-window position structure.|
|1406|Cannot create a top-level child window.|
|1407|Cannot find window class.|
|1408|Invalid window; it belongs to other thread.|
|1409|Hot key is already registered.|
|1410|Class already exists.|
|1411|Class does not exist.|
|1412|Class still has open windows.|
|1413|Invalid index.|
|1414|Invalid icon handle.|
|1415|Using private DIALOG window words.|
|1416|The list box identifier was not found.|
|1417|No wildcards were found.|
|1418|Thread does not have a clipboard open.|
|1419|Hot key is not registered.|
|1420|The window is not a valid dialog window.|
|1421|Control ID not found.|
|1422|Invalid message for a combo box because it does not have an edit control.|
|1423|The window is not a combo box.|
|1424|Height must be less than 256.|
|1425|Invalid device context (DC) handle.|
|1426|Invalid hook procedure type.|
|1427|Invalid hook procedure.|
|1428|Cannot set nonlocal hook without a module handle.|
|1429|This hook procedure can only be set globally.|
|1430|The journal hook procedure is already installed.|
|1431|The hook procedure is not installed.|
|1432|Invalid message for single-selection list box.|
|1433|LB_SETCOUNT sent to non-lazy list box.|
|1434|This list box does not support tab stops.|
|1435|Cannot destroy object created by another thread.|
|1436|Child windows cannot have menus.|
|1437|The window does not have a system menu.|
|1438|Invalid message box style.|
|1439|Invalid system-wide (SPI_*) parameter.|
|1440|Screen already locked.|
|1441|All handles to windows in a multiple-window position structure must have the same parent.|
|1442|The window is not a child window.|
|1443|Invalid GW_* command.|
|1444|Invalid thread identifier.|
|1445|Cannot process a message from a window that is not a multiple document interface (MDI) window.|
|1446|Popup menu already active.|
|1447|The window does not have scroll bars.|
|1448|Scroll bar range cannot be greater than MAXLONG.|
|1449|Cannot show or remove the window in the way specified.|
|1450|Insufficient system resources exist to complete the requested service.|
|1451|Insufficient system resources exist to complete the requested service.|
|1452|Insufficient system resources exist to complete the requested service.|
|1453|Insufficient quota to complete the requested service.|
|1454|Insufficient quota to complete the requested service.|
|1455|The paging file is too small for this operation to complete.|
|1456|A menu item was not found.|
|1457|Invalid keyboard layout handle.|
|1458|Hook type not allowed.|
|1459|This operation requires an interactive window station.|
|1460|This operation returned because the timeout period expired.|
|1461|Invalid monitor handle.|
|1462|Incorrect size argument.|
|1463|The symbolic link cannot be followed because its type is disabled.|
|1464|This application does not support the current operation on symbolic links.|
|1465|Windows was unable to parse the requested XML data.|
|1466|An error was encountered while processing an XML digital signature.|
|1467|This application must be restarted.|
|1468|The caller made the connection request in the wrong routing compartment.|
|1469|There was an AuthIP failure when attempting to connect to the remote host.|
|1470|Insufficient NVRAM resources exist to complete the requested service. A reboot might be required.|
|1471|Unable to finish the requested operation because the specified process is not a GUI process.|
|1500|The event log file is corrupted.|
|1501|No event log file could be opened, so the event logging service did not start.|
|1502|The event log file is full.|
|1503|The event log file has changed between read operations.|
|1504|The specified Job already has a container assigned to it.|
|1505|The specified Job does not have a container assigned to it.|
|1550|The specified task name is invalid.|
|1551|The specified task index is invalid.|
|1552|The specified thread is already joining a task.|
|1601|The Windows Installer Service could not be accessed. This can occur if the Windows Installer is not correctly installed. Contact your support personnel for assistance.|
|1602|User cancelled installation.|
|1603|Fatal error during installation.|
|1604|Installation suspended, incomplete.|
|1605|This action is only valid for products that are currently installed.|
|1606|Feature ID not registered.|
|1607|Component ID not registered.|
|1608|Unknown property.|
|1609|Handle is in an invalid state.|
|1610|The configuration data for this product is corrupt. Contact your support personnel.|
|1611|Component qualifier not present.|
|1612|The installation source for this product is not available. Verify that the source exists and that you can access it.|
|1613|This installation package cannot be installed by the Windows Installer service. You must install a Windows service pack that contains a newer version of the Windows Installer service.|
|1614|Product is uninstalled.|
|1615|SQL query syntax invalid or unsupported.|
|1616|Record field does not exist.|
|1617|The device has been removed.|
|1618|Another installation is already in progress. Complete that installation before proceeding with this install.|
|1619|This installation package could not be opened. Verify that the package exists and that you can access it, or contact the application vendor to verify that this is a valid Windows Installer package.|
|1620|This installation package could not be opened. Contact the application vendor to verify that this is a valid Windows Installer package.|
|1621|There was an error starting the Windows Installer service user interface. Contact your support personnel.|
|1622|Error opening installation log file. Verify that the specified log file location exists and that you can write to it.|
|1623|The language of this installation package is not supported by your system.|
|1624|Error applying transforms. Verify that the specified transform paths are valid.|
|1625|This installation is forbidden by system policy. Contact your system administrator.|
|1626|Function could not be executed.|
|1627|Function failed during execution.|
|1628|Invalid or unknown table specified.|
|1629|Data supplied is of wrong type.|
|1630|Data of this type is not supported.|
|1631|The Windows Installer service failed to start. Contact your support personnel.|
|1632|The Temp folder is on a drive that is full or is inaccessible. Free up space on the drive or verify that you have write permission on the Temp folder.|
|1633|This installation package is not supported by this processor type. Contact your product vendor.|
|1634|Component not used on this computer.|
|1635|This update package could not be opened. Verify that the update package exists and that you can access it, or contact the application vendor to verify that this is a valid Windows Installer update package.|
|1636|This update package could not be opened. Contact the application vendor to verify that this is a valid Windows Installer update package.|
|1637|This update package cannot be processed by the Windows Installer service. You must install a Windows service pack that contains a newer version of the Windows Installer service.|
|1638|Another version of this product is already installed. Installation of this version cannot continue. To configure or remove the existing version of this product, use Add/Remove Programs on the Control Panel.|
|1639|Invalid command line argument. Consult the Windows Installer SDK for detailed command line help.|
|1640|Only administrators have permission to add, remove, or configure server software during a Terminal services remote session. If you want to install or configure software on the server, contact your network administrator.|
|1641|The requested operation completed successfully. The system will be restarted so the changes can take effect.|
|1642|The upgrade cannot be installed by the Windows Installer service because the program to be upgraded may be missing, or the upgrade may update a different version of the program. Verify that the program to be upgraded exists on your computer and that you have the correct upgrade.|
|1643|The update package is not permitted by software restriction policy.|
|1644|One or more customizations are not permitted by software restriction policy.|
|1645|The Windows Installer does not permit installation from a Remote Desktop Connection.|
|1646|Uninstallation of the update package is not supported.|
|1647|The update is not applied to this product.|
|1648|No valid sequence could be found for the set of updates.|
|1649|Update removal was disallowed by policy.|
|1650|The XML update data is invalid.|
|1651|Windows Installer does not permit updating of managed advertised products. At least one feature of the product must be installed before applying the update.|
|1652|The Windows Installer service is not accessible in Safe Mode. Please try again when your computer is not in Safe Mode or you can use System Restore to return your machine to a previous good state.|
|1653|A fail fast exception occurred. Exception handlers will not be invoked and the process will be terminated immediately.|
|1654|The app that you are trying to run is not supported on this version of Windows.|
|1655|The operation was blocked as the process prohibits dynamic code generation.|
|1656|The objects are not identical.|
|1657|The specified image file was blocked from loading because it does not enable a feature required by the process: Control Flow Guard.|
|1660|The thread context could not be updated because this has been restricted for the process.|
|1661|An invalid cross-partition private file/section access was attempted.|
|1662|A return address hijack is being attempted. This is supported by the operating system when user-mode shadow stacks are enabled.|
|1700|The string binding is invalid.|
|1701|The binding handle is not the correct type.|
|1702|The binding handle is invalid.|
|1703|The RPC protocol sequence is not supported.|
|1704|The RPC protocol sequence is invalid.|
|1705|The string universal unique identifier (UUID) is invalid.|
|1706|The endpoint format is invalid.|
|1707|The network address is invalid.|
|1708|No endpoint was found.|
|1709|The timeout value is invalid.|
|1710|The object universal unique identifier (UUID) was not found.|
|1711|The object universal unique identifier (UUID) has already been registered.|
|1712|The type universal unique identifier (UUID) has already been registered.|
|1713|The RPC server is already listening.|
|1714|No protocol sequences have been registered.|
|1715|The RPC server is not listening.|
|1716|The manager type is unknown.|
|1717|The interface is unknown.|
|1718|There are no bindings.|
|1719|There are no protocol sequences.|
|1720|The endpoint cannot be created.|
|1721|Not enough resources are available to complete this operation.|
|1722|The RPC server is unavailable.|
|1723|The RPC server is too busy to complete this operation.|
|1724|The network options are invalid.|
|1725|There are no remote procedure calls active on this thread.|
|1726|The remote procedure call failed.|
|1727|The remote procedure call failed and did not execute.|
|1728|A remote procedure call (RPC) protocol error occurred.|
|1729|Access to the HTTP proxy is denied.|
|1730|The transfer syntax is not supported by the RPC server.|
|1732|The universal unique identifier (UUID) type is not supported.|
|1733|The tag is invalid.|
|1734|The array bounds are invalid.|
|1735|The binding does not contain an entry name.|
|1736|The name syntax is invalid.|
|1737|The name syntax is not supported.|
|1739|No network address is available to use to construct a universal unique identifier (UUID).|
|1740|The endpoint is a duplicate.|
|1741|The authentication type is unknown.|
|1742|The maximum number of calls is too small.|
|1743|The string is too long.|
|1744|The RPC protocol sequence was not found.|
|1745|The procedure number is out of range.|
|1746|The binding does not contain any authentication information.|
|1747|The authentication service is unknown.|
|1748|The authentication level is unknown.|
|1749|The security context is invalid.|
|1750|The authorization service is unknown.|
|1751|The entry is invalid.|
|1752|The server endpoint cannot perform the operation.|
|1753|There are no more endpoints available from the endpoint mapper.|
|1754|No interfaces have been exported.|
|1755|The entry name is incomplete.|
|1756|The version option is invalid.|
|1757|There are no more members.|
|1758|There is nothing to unexport.|
|1759|The interface was not found.|
|1760|The entry already exists.|
|1761|The entry is not found.|
|1762|The name service is unavailable.|
|1763|The network address family is invalid.|
|1764|The requested operation is not supported.|
|1765|No security context is available to allow impersonation.|
|1766|An internal error occurred in a remote procedure call (RPC).|
|1767|The RPC server attempted an integer division by zero.|
|1768|An addressing error occurred in the RPC server.|
|1769|A floating-point operation at the RPC server caused a division by zero.|
|1770|A floating-point underflow occurred at the RPC server.|
|1771|A floating-point overflow occurred at the RPC server.|
|1772|The list of RPC servers available for the binding of auto handles has been exhausted.|
|1773|Unable to open the character translation table file.|
|1774|The file containing the character translation table has fewer than 512 bytes.|
|1775|A null context handle was passed from the client to the host during a remote procedure call.|
|1777|The context handle changed during a remote procedure call.|
|1778|The binding handles passed to a remote procedure call do not match.|
|1779|The stub is unable to get the remote procedure call handle.|
|1780|A null reference pointer was passed to the stub.|
|1781|The enumeration value is out of range.|
|1782|The byte count is too small.|
|1783|The stub received bad data.|
|1784|The supplied user buffer is not valid for the requested operation.|
|1785|The disk media is not recognized. It may not be formatted.|
|1786|The workstation does not have a trust secret.|
|1787|The security database on the server does not have a computer account for this workstation trust relationship.|
|1788|The trust relationship between the primary domain and the trusted domain failed.|
|1789|The trust relationship between this workstation and the primary domain failed.|
|1790|The network logon failed.|
|1791|A remote procedure call is already in progress for this thread.|
|1792|An attempt was made to logon, but the network logon service was not started.|
|1793|The user's account has expired.|
|1794|The redirector is in use and cannot be unloaded.|
|1795|The specified printer driver is already installed.|
|1796|The specified port is unknown.|
|1797|The printer driver is unknown.|
|1798|The print processor is unknown.|
|1799|The specified separator file is invalid.|
|1800|The specified priority is invalid.|
|1801|The printer name is invalid.|
|1802|The printer already exists.|
|1803|The printer command is invalid.|
|1804|The specified datatype is invalid.|
|1805|The environment specified is invalid.|
|1806|There are no more bindings.|
|1807|The account used is an interdomain trust account. Use your global user account or local user account to access this server.|
|1808|The account used is a computer account. Use your global user account or local user account to access this server.|
|1809|The account used is a server trust account. Use your global user account or local user account to access this server.|
|1810|The name or security ID (SID) of the domain specified is inconsistent with the trust information for that domain.|
|1811|The server is in use and cannot be unloaded.|
|1812|The specified image file did not contain a resource section.|
|1813|The specified resource type cannot be found in the image file.|
|1814|The specified resource name cannot be found in the image file.|
|1815|The specified resource language ID cannot be found in the image file.|
|1816|Not enough quota is available to process this command.|
|1817|No interfaces have been registered.|
|1818|The remote procedure call was cancelled.|
|1819|The binding handle does not contain all required information.|
|1820|A communications failure occurred during a remote procedure call.|
|1821|The requested authentication level is not supported.|
|1822|No principal name registered.|
|1823|The error specified is not a valid Windows RPC error code.|
|1824|A UUID that is valid only on this computer has been allocated.|
|1825|A security package specific error occurred.|
|1826|Thread is not canceled.|
|1827|Invalid operation on the encoding/decoding handle.|
|1828|Incompatible version of the serializing package.|
|1829|Incompatible version of the RPC stub.|
|1830|The RPC pipe object is invalid or corrupted.|
|1831|An invalid operation was attempted on an RPC pipe object.|
|1832|Unsupported RPC pipe version.|
|1833|HTTP proxy server rejected the connection because the cookie authentication failed.|
|1834|The RPC server is suspended, and could not be resumed for this request. The call did not execute.|
|1835|The RPC call contains too many handles to be transmitted in a single request.|
|1836|The RPC call contains a handle that differs from the declared handle type.|
|1898|The group member was not found.|
|1899|The endpoint mapper database entry could not be created.|
|1900|The object universal unique identifier (UUID) is the nil UUID.|
|1901|The specified time is invalid.|
|1902|The specified form name is invalid.|
|1903|The specified form size is invalid.|
|1904|The specified printer handle is already being waited on|
|1905|The specified printer has been deleted.|
|1906|The state of the printer is invalid.|
|1907|The user's password must be changed before signing in.|
|1908|Could not find the domain controller for this domain.|
|1909|The referenced account is currently locked out and may not be logged on to.|
|1910|The object exporter specified was not found.|
|1911|The object specified was not found.|
|1912|The object resolver set specified was not found.|
|1913|Some data remains to be sent in the request buffer.|
|1914|Invalid asynchronous remote procedure call handle.|
|1915|Invalid asynchronous RPC call handle for this operation.|
|1916|The RPC pipe object has already been closed.|
|1917|The RPC call completed before all pipes were processed.|
|1918|No more data is available from the RPC pipe.|
|1919|No site name is available for this machine.|
|1920|The file cannot be accessed by the system.|
|1921|The name of the file cannot be resolved by the system.|
|1922|The entry is not of the expected type.|
|1923|Not all object UUIDs could be exported to the specified entry.|
|1924|Interface could not be exported to the specified entry.|
|1925|The specified profile entry could not be added.|
|1926|The specified profile element could not be added.|
|1927|The specified profile element could not be removed.|
|1928|The group element could not be added.|
|1929|The group element could not be removed.|
|1930|The printer driver is not compatible with a policy enabled on your computer that blocks NT 4.0 drivers.|
|1931|The context has expired and can no longer be used.|
|1932|The current user's delegated trust creation quota has been exceeded.|
|1933|The total delegated trust creation quota has been exceeded.|
|1934|The current user's delegated trust deletion quota has been exceeded.|
|1935|The computer you are signing into is protected by an authentication firewall. The specified account is not allowed to authenticate to the computer.|
|1936|Remote connections to the Print Spooler are blocked by a policy set on your machine.|
|1937|Authentication failed because NTLM authentication has been disabled.|
|1938|Logon Failure: EAS policy requires that the user change their password before this operation can be performed.|
|1939|An administrator has restricted sign in. To sign in, make sure your device is connected to the Internet, and have your administrator sign in first.|
|2000|The pixel format is invalid.|
|2001|The specified driver is invalid.|
|2002|The window style or class attribute is invalid for this operation.|
|2003|The requested metafile operation is not supported.|
|2004|The requested transformation operation is not supported.|
|2005|The requested clipping operation is not supported.|
|2010|The specified color management module is invalid.|
|2011|The specified color profile is invalid.|
|2012|The specified tag was not found.|
|2013|A required tag is not present.|
|2014|The specified tag is already present.|
|2015|The specified color profile is not associated with the specified device.|
|2016|The specified color profile was not found.|
|2017|The specified color space is invalid.|
|2018|Image Color Management is not enabled.|
|2019|There was an error while deleting the color transform.|
|2020|The specified color transform is invalid.|
|2021|The specified transform does not match the bitmap's color space.|
|2022|The specified named color index is not present in the profile.|
|2023|The specified profile is intended for a device of a different type than the specified device.|
|2102|The workstation driver is not installed.|
|2103|The server could not be located.|
|2104|An internal error occurred.  The network cannot access a shared memory segment.|
|2105|A network resource shortage occurred .|
|2106|This operation is not supported on workstations.|
|2107|The device is not connected.|
|2108|The network connection was made successfully, but the user had to be prompted for a password other than the one originally specified.|
|2109|The network connection was made successfully using default credentials.|
|2114|The Server service is not started.|
|2115|The queue is empty.|
|2116|The device or directory does not exist.|
|2117|The operation is invalid on a redirected resource.|
|2118|The name has already been shared.|
|2119|The server is currently out of the requested resource.|
|2121|Requested addition of items exceeds the maximum allowed.|
|2122|The Peer service supports only two simultaneous users.|
|2123|The API return buffer is too small.|
|2127|A remote API error occurred.|
|2131|An error occurred when opening or reading the configuration file.|
|2136|A general network error occurred.|
|2137|The Workstation service is in an inconsistent state. Restart the computer before restarting the Workstation service.|
|2138|The Workstation service has not been started.|
|2139|The requested information is not available.|
|2140|An internal Windows error occurred.|
|2141|The server is not configured for transactions.|
|2142|The requested API is not supported on the remote server.|
|2143|The event name is invalid.|
|2144|The computer name already exists on the network. Change it and restart the computer.|
|2146|The specified component could not be found in the configuration information.|
|2147|The specified parameter could not be found in the configuration information.|
|2149|A line in the configuration file is too long.|
|2150|The printer does not exist.|
|2151|The print job does not exist.|
|2152|The printer destination cannot be found.|
|2153|The printer destination already exists.|
|2154|The printer queue already exists.|
|2155|No more printers can be added.|
|2156|No more print jobs can be added.|
|2157|No more printer destinations can be added.|
|2158|This printer destination is idle and cannot accept control operations.|
|2159|This printer destination request contains an invalid control function.|
|2160|The print processor is not responding.|
|2161|The spooler is not running.|
|2162|This operation cannot be performed on the print destination in its current state.|
|2163|This operation cannot be performed on the printer queue in its current state.|
|2164|This operation cannot be performed on the print job in its current state.|
|2165|A spooler memory allocation failure occurred.|
|2166|The device driver does not exist.|
|2167|The data type is not supported by the print processor.|
|2168|The print processor is not installed.|
|2180|The service database is locked.|
|2181|The service table is full.|
|2182|The requested service has already been started.|
|2183|The service does not respond to control actions.|
|2184|The service has not been started.|
|2185|The service name is invalid.|
|2186|The service is not responding to the control function.|
|2187|The service control is busy.|
|2188|The configuration file contains an invalid service program name.|
|2189|The service could not be controlled in its present state.|
|2190|The service ended abnormally.|
|2191|The requested pause, continue, or stop is not valid for this service.|
|2192|The service control dispatcher could not find the service name in the dispatch table.|
|2193|The service control dispatcher pipe read failed.|
|2194|A thread for the new service could not be created.|
|2200|This workstation is already logged on to the local-area network.|
|2201|The workstation is not logged on to the local-area network.|
|2202|The specified username is invalid.|
|2203|The password parameter is invalid.|
|2204|The logon processor did not add the message alias.|
|2205|The logon processor did not add the message alias.|
|2206|The logoff processor did not delete the message alias.|
|2207|The logoff processor did not delete the message alias.|
|2209|Network logons are paused.|
|2210|A centralized logon-server conflict occurred.|
|2211|The server is configured without a valid user path.|
|2212|An error occurred while loading or running the logon script.|
|2214|The logon server was not specified.  Your computer will be logged on as STANDALONE.|
|2215|The logon server could not be found.|
|2216|There is already a logon domain for this computer.|
|2217|The logon server could not validate the logon.|
|2219|The security database could not be found.|
|2220|The group name could not be found.|
|2221|The user name could not be found.|
|2222|The resource name could not be found.|
|2223|The group already exists.|
|2224|The account already exists.|
|2225|The resource permission list already exists.|
|2226|This operation is only allowed on the primary domain controller of the domain.|
|2227|The security database has not been started.|
|2228|There are too many names in the user accounts database.|
|2229|A disk I/O failure occurred.|
|2230|The limit of 64 entries per resource was exceeded.|
|2231|Deleting a user with a session is not allowed.|
|2232|The parent directory could not be located.|
|2233|Unable to add to the security database session cache segment.|
|2234|This operation is not allowed on this special group.|
|2235|This user is not cached in user accounts database session cache.|
|2236|The user already belongs to this group.|
|2237|The user does not belong to this group.|
|2238|This user account is undefined.|
|2239|This user account has expired.|
|2240|The user is not allowed to log on from this workstation.|
|2241|The user is not allowed to log on at this time.|
|2242|The password of this user has expired.|
|2243|The password of this user cannot change.|
|2244|This password cannot be used now.|
|2245|The password does not meet the password policy requirements. Check the minimum password length, password complexity and password history requirements.|
|2246|The password of this user is too recent to change.|
|2247|The security database is corrupted.|
|2248|No updates are necessary to this replicant network/local security database.|
|2249|This replicant database is outdated; synchronization is required.|
|2250|This network connection does not exist.|
|2251|This asg_type is invalid.|
|2252|This device is currently being shared.|
|2253|The user name may not be same as computer name.|
|2270|The computer name could not be added as a message alias.  The name may already exist on the network.|
|2271|The Messenger service is already started.|
|2272|The Messenger service failed to start.|
|2273|The message alias could not be found on the network.|
|2274|This message alias has already been forwarded.|
|2275|This message alias has been added but is still forwarded.|
|2276|This message alias already exists locally.|
|2277|The maximum number of added message aliases has been exceeded.|
|2278|The computer name could not be deleted.|
|2279|Messages cannot be forwarded back to the same workstation.|
|2280|An error occurred in the domain message processor.|
|2281|The message was sent, but the recipient has paused the Messenger service.|
|2282|The message was sent but not received.|
|2283|The message alias is currently in use. Try again later.|
|2284|The Messenger service has not been started.|
|2285|The name is not on the local computer.|
|2286|The forwarded message alias could not be found on the network.|
|2287|The message alias table on the remote station is full.|
|2288|Messages for this alias are not currently being forwarded.|
|2289|The broadcast message was truncated.|
|2294|This is an invalid device name.|
|2295|A write fault occurred.|
|2297|A duplicate message alias exists on the network.|
|2298|This message alias will be deleted later.|
|2299|The message alias was not successfully deleted from all networks.|
|2300|This operation is not supported on computers with multiple networks.|
|2310|This shared resource does not exist.|
|2311|This device is not shared.|
|2312|A session does not exist with that computer name.|
|2314|There is not an open file with that identification number.|
|2315|A failure occurred when executing a remote administration command.|
|2316|A failure occurred when opening a remote temporary file.|
|2317|The data returned from a remote administration command has been truncated to 64K.|
|2318|This device cannot be shared as both a spooled and a non-spooled resource.|
|2319|The information in the list of servers may be incorrect.|
|2320|The computer is not active in this domain.|
|2321|The share must be removed from the Distributed File System before it can be deleted.|
|2331|The operation is invalid for this device.|
|2332|This device cannot be shared.|
|2333|This device was not open.|
|2334|This device name list is invalid.|
|2335|The queue priority is invalid.|
|2337|There are no shared communication devices.|
|2338|The queue you specified does not exist.|
|2340|This list of devices is invalid.|
|2341|The requested device is invalid.|
|2342|This device is already in use by the spooler.|
|2343|This device is already in use as a communication device.|
|2351|This computer name is invalid.|
|2354|The string and prefix specified are too long.|
|2356|This path component is invalid.|
|2357|Could not determine the type of input.|
|2362|The buffer for types is not big enough.|
|2370|Profile files cannot exceed 64K.|
|2371|The start offset is out of range.|
|2372|The system cannot delete current connections to network resources.|
|2373|The system was unable to parse the command line in this file.|
|2374|An error occurred while loading the profile file.|
|2375|Errors occurred while saving the profile file.  The profile was partially saved.|
|2377|Log file %1 is full.|
|2378|This log file has changed between reads.|
|2379|Log file %1 is corrupt.|
|2380|The source path cannot be a directory.|
|2381|The source path is illegal.|
|2382|The destination path is illegal.|
|2383|The source and destination paths are on different servers.|
|2385|The Run server you requested is paused.|
|2389|An error occurred when communicating with a Run server.|
|2391|An error occurred when starting a background process.|
|2392|The shared resource you are connected to could not be found.|
|2400|The LAN adapter number is invalid.|
|2401|This network connection has files open or requests pending.|
|2402|Active connections still exist.|
|2403|This share name or password is invalid.|
|2404|The device is in use by an active process and cannot be disconnected.|
|2405|The drive letter is in use locally.|
|2430|The specified client is already registered for the specified event.|
|2431|The alert table is full.|
|2432|An invalid or nonexistent alert name was raised.|
|2433|The alert recipient is invalid.|
|2434|A user's session with this server has been deleted<br>because the user's logon hours are no longer valid.|
|2440|The log file does not contain the requested record number.|
|2450|The user accounts database is not configured correctly.|
|2451|This operation is not permitted when the Netlogon service is running.|
|2452|This operation is not allowed on the last administrative account.|
|2453|Could not find domain controller for this domain.|
|2454|Could not set logon information for this user.|
|2455|The Netlogon service has not been started.|
|2456|Unable to add to the user accounts database.|
|2457|This server's clock is not synchronized with the primary domain controller's clock.|
|2458|A password mismatch has been detected.|
|2460|The server identification does not specify a valid server.|
|2461|The session identification does not specify a valid session.|
|2462|The connection identification does not specify a valid connection.|
|2463|There is no space for another entry in the table of available servers.|
|2464|The server has reached the maximum number of sessions it supports.|
|2465|The server has reached the maximum number of connections it supports.|
|2466|The server cannot open more files because it has reached its maximum number.|
|2467|There are no alternate servers registered on this server.|
|2470|Try down-level (remote admin protocol) version of API instead.|
|2480|The UPS driver could not be accessed by the UPS service.|
|2481|The UPS service is not configured correctly.|
|2482|The UPS service could not access the specified Comm Port.|
|2483|The UPS indicated a line fail or low battery situation. Service not started.|
|2484|The UPS service failed to perform a system shut down.|
|2500|The program below returned an MS-DOS error code:|
|2501|The program below needs more memory:|
|2502|The program below called an unsupported MS-DOS function:|
|2503|The workstation failed to boot.|
|2504|The file below is corrupt.|
|2505|No loader is specified in the boot-block definition file.|
|2506|NetBIOS returned an error: The NCB and SMB are dumped above.|
|2507|A disk I/O error occurred.|
|2508|Image parameter substitution failed.|
|2509|Too many image parameters cross disk sector boundaries.|
|2510|The image was not generated from an MS-DOS diskette formatted with /S.|
|2511|Remote boot will be restarted later.|
|2512|The call to the Remoteboot server failed.|
|2513|Cannot connect to the Remoteboot server.|
|2514|Cannot open image file on the Remoteboot server.|
|2515|Connecting to the Remoteboot server...|
|2516|Connecting to the Remoteboot server...|
|2517|Remote boot service was stopped; check the error log for the cause of the problem.|
|2518|Remote boot startup failed; check the error log for the cause of the problem.|
|2519|A second connection to a Remoteboot resource is not allowed.|
|2550|The browser service was configured with MaintainServerList=No.|
|2610|Service failed to start since none of the network adapters started with this service.|
|2611|Service failed to start due to bad startup information in the registry.|
|2612|Service failed to start because its database is absent or corrupt.|
|2613|Service failed to start because RPLFILES share is absent.|
|2614|Service failed to start because RPLUSER group is absent.|
|2615|Cannot enumerate service records.|
|2616|Workstation record information has been corrupted.|
|2617|Workstation record was not found.|
|2618|Workstation name is in use by some other workstation.|
|2619|Profile record information has been corrupted.|
|2620|Profile record was not found.|
|2621|Profile name is in use by some other profile.|
|2622|There are workstations using this profile.|
|2623|Configuration record information has been corrupted.|
|2624|Configuration record was not found.|
|2625|Adapter id record information has been corrupted.|
|2626|An internal service error has occurred.|
|2627|Vendor id record information has been corrupted.|
|2628|Boot block record information has been corrupted.|
|2629|The user account for this workstation record is missing.|
|2630|The RPLUSER local group could not be found.|
|2631|Boot block record was not found.|
|2632|Chosen profile is incompatible with this workstation.|
|2633|Chosen network adapter id is in use by some other workstation.|
|2634|There are profiles using this configuration.|
|2635|There are workstations, profiles or configurations using this boot block.|
|2636|Service failed to backup Remoteboot database.|
|2637|Adapter record was not found.|
|2638|Vendor record was not found.|
|2639|Vendor name is in use by some other vendor record.|
|2640|(boot name, vendor id) is in use by some other boot block record.|
|2641|Configuration name is in use by some other configuration.|
|2660|The internal database maintained by the DFS service is corrupt|
|2661|One of the records in the internal DFS database is corrupt|
|2662|There is no DFS name whose entry path matches the input Entry Path|
|2663|A root or link with the given name already exists|
|2664|The server share specified is already shared in the DFS|
|2665|The indicated server share does not support the indicated DFS namespace|
|2666|The operation is not valid on this portion of the namespace|
|2667|The operation is not valid on this portion of the namespace|
|2668|The operation is ambiguous because the link has multiple servers|
|2669|Unable to create a link|
|2670|The server is not DFS Aware|
|2671|The specified rename target path is invalid|
|2672|The specified DFS link is offline|
|2673|The specified server is not a server for this link|
|2674|A cycle in the DFS name was detected|
|2675|The operation is not supported on a server-based DFS|
|2676|This link is already supported by the specified server-share|
|2677|Can't remove the last server-share supporting this root or link|
|2678|The operation is not supported for an Inter-DFS link|
|2679|The internal state of the DFS Service has become inconsistent|
|2680|The DFS Service has been installed on the specified server|
|2681|The DFS data being reconciled is identical|
|2682|The DFS root cannot be deleted - Uninstall DFS if required|
|2683|A child or parent directory of the share is already in a DFS|
|2690|DFS internal error|
|2691|This machine is already joined to a domain.|
|2692|This machine is not currently joined to a domain.|
|2693|This machine is a domain controller and cannot be unjoined from a domain.|
|2694|The destination domain controller does not support creating machine accounts in OUs.|
|2695|The specified workgroup name is invalid.|
|2696|The specified computer name is incompatible with the default language used on the domain controller.|
|2697|The specified computer account could not be found. Contact an administrator to verify the account is in the domain. If the account has been deleted unjoin, reboot, and rejoin the domain.|
|2698|This version of Windows cannot be joined to a domain.|
|2699|An attempt to resolve the DNS name of a domain controller in the domain being joined has failed.  Please verify this client is configured to reach a DNS server that can resolve DNS names in the target domain. For information about network troubleshooting, see Windows Help.|
|2700|This device is joined to Azure AD. To join an Active Directory domain, you must first go to settings and choose to disconnect your device from your work or school.|
|2701|Password must change at next logon|
|2702|Account is locked out|
|2703|Password is too long|
|2704|Password doesn't meet the complexity policy|
|2705|Password doesn't meet the requirements of the filter dll's|
|2709|Offline join completion information was not found.|
|2710|The offline join completion information was bad.|
|2711|Unable to create offline join information. Please ensure you have access to the specified path location and permissions to modify its contents. Running as an elevated administrator may be required.|
|2712|The domain join info being saved was incomplete or bad.|
|2713|Offline join operation successfully completed but a restart is needed.|
|2714|There was no offline join operation pending.|
|2715|Unable to set one or more requested machine or domain name values on the local computer.|
|2716|Could not verify the current machine's hostname against the saved value in the join completion information.|
|2717|Unable to load the specified offline registry hive. Please ensure you have access to the specified path location and permissions to modify its contents. Running as an elevated administrator may be required.|
|2718|The minimum session security requirements for this operation were not met.|
|2719|Computer account provisioning blob version is not supported.|
|2720|The specified domain controller does not meet the version requirement for this operation. Please select a domain controller capable of issuing claims.|
|2721|This operation requires a domain controller which supports LDAP. Please select an LDAP-capable domain controller.|
|2722|A domain controller which meets the version requirement for this operation could not be located. Please ensure that a domain controller capable of issuing claims is available.|
|2723|The Windows version of the specified image does not support provisioning.|
|2724|The machine name is blocked from joining the domain.|
|2725|The domain controller does not meet the version requirement for this operation. See http://go.microsoft.com/fwlink/?LinkId=294288 for more information.|
|2726|The local machine does not allow querying of LSA secrets in plain-text.|
|2727|Unable to leave the Azure AD domain that this machine is joined to. Check the event log for detailed error information.|
|2728|Unable to update hostname in Azure AD. Check the event log for detailed error information.|
|2729|The hostname is already taken by another device.|
|2730|The hostname is too long.|
|2731|Too many hostnames specified for the device.|
|2732|An account with the same name exists in Active Directory. Re-using the account was blocked by security policy.|
|2999|This is the last error in NERR range.|
|3000|The specified print monitor is unknown.|
|3001|The specified printer driver is currently in use.|
|3002|The spool file was not found.|
|3003|A StartDocPrinter call was not issued.|
|3004|An AddJob call was not issued.|
|3005|The specified print processor has already been installed.|
|3006|The specified print monitor has already been installed.|
|3007|The specified print monitor does not have the required functions.|
|3008|The specified print monitor is currently in use.|
|3009|The requested operation is not allowed when there are jobs queued to the printer.|
|3010|The requested operation is successful. Changes will not be effective until the system is rebooted.|
|3011|The requested operation is successful. Changes will not be effective until the service is restarted.|
|3012|No printers were found.|
|3013|The printer driver is known to be unreliable.|
|3014|The printer driver is known to harm the system.|
|3015|The specified printer driver package is currently in use.|
|3016|Unable to find a core driver package that is required by the printer driver package.|
|3017|The requested operation failed. A system reboot is required to roll back changes made.|
|3018|The requested operation failed. A system reboot has been initiated to roll back changes made.|
|3019|The specified printer driver was not found on the system and needs to be downloaded.|
|3020|The requested print job has failed to print. A print system update requires the job to be resubmitted.|
|3021|The printer driver does not contain a valid manifest, or contains too many manifests.|
|3022|The specified printer cannot be shared.|
|3023|The requested function requires SMB1 to be present and enabled.|
|3024|The user canceled the authentication prompt to a remote server. |
|3025|A defective sector on drive %1 has been replaced (hotfixed).<br>No data was lost.  You should run CHKDSK soon to restore full<br>performance and replenish the volume's spare sector pool.<br><br>The hotfix occurred while processing a remote request.|
|3026|A disk error occurred on the HPFS volume in drive %1.<br>The error occurred while processing a remote request.|
|3027|The user accounts database (NET.ACC) is corrupted.  The local security<br>system is replacing the corrupted NET.ACC with the backup<br>made on %1 at %2.<br>Any updates made to the database after this time are lost.<br>|
|3028|The user accounts database (NET.ACC) is missing. The local<br>security system is restoring the backup database<br>made on %1 at %2.<br>Any updates made to the database after this time are lost.<br>|
|3029|Local security could not be started because the user accounts database<br>(NET.ACC) was missing or corrupted, and no usable backup<br>database was present.<br><br>THE SYSTEM IS NOT SECURE.<br>|
|3030|The server cannot export directory %1, to client %2.<br>It is exported from another server.|
|3031|The replication server could not update directory %2 from the source<br>on %3 due to error %1.|
|3032|Master %1 did not send an update notice for directory %2 at the expected<br>time.|
|3033|User %1 has exceeded account limitation %2 on server %3.|
|3034|The primary domain controller for domain %1 failed.|
|3035|Failed to authenticate with %2, a Windows Domain Controller for<br>domain %1.|
|3036|The replicator attempted to log on at %2 as %1 and failed.|
|3037|@I *LOGON HOURS |
|3038|Replicator could not access %2<br>on %3 due to system error %1.|
|3039|Replicator limit for files in a directory has been exceeded.|
|3040|Replicator limit for tree depth has been exceeded.|
|3041|The replicator cannot update directory %1. It has tree integrity<br>and is the current directory for some process.|
|3042|Network error %1 occurred.|
|3045|System error %1 occurred.|
|3046|Cannot log on. User is currently logged on and argument TRYUSER<br>is set to NO.|
|3047|IMPORT path %1 cannot be found.|
|3048|EXPORT path %1 cannot be found.|
|3049|Replicated data has changed in directory %1.|
|3050|The operation was paused.|
|3051|The Registry or the information you just typed includes an illegal<br>value for "%1".|
|3052|The required parameter was not provided on the command<br>line or in the configuration file.|
|3053|LAN Manager does not recognize "%1" as a valid option.|
|3054|A request for resource could not be satisfied.|
|3055|A problem exists with the system configuration.|
|3056|A system error has occurred.|
|3057|An internal consistency error has occurred.|
|3058|The configuration file or the command line has an ambiguous option.|
|3059|The configuration file or the command line has a duplicate parameter.|
|3060|The condition supplied for the app execution request was not satisfied, so the request was not performed.|
|3061|The supplied handle has been invalidated and may not be used for the requested operation.|
|3062|The supplied host generation has been invalidated and may not be used for the requested operation.|
|3063|An attempt to register a process failed because the target host was not in a valid state to receive process registrations.|
|3064|The host is not in a valid state to support the execution request.|
|3065|The operation was not completed because a required resource donor was not found for the host.|
|3066|The operation was not completed because an unexpected host ID was encountered.|
|3067|The operation was not completed because the specified user was not known to the service.|
|3068|The application is blocked by app compat policy.|
|3069|The caller specified wait timed out before the operation completed.|
|3070|The caller specified wait timed out before the operation completed because a host termination is in queued.|
|3071|The caller specified wait timed out before the operation completed because a licensing operation is being performed.|
|3072|The caller specified wait timed out before the operation completed because resources are being acquired.|
|3073|process|
|3074|Security Failure. |
|3075|Bad or missing LAN Manager root directory.|
|3076|The network software is not installed.|
|3077|The server is not started.|
|3078|The server cannot access the user accounts database (NET.ACC).|
|3079|Incompatible files are installed in the LANMAN tree.|
|3080|Enabling driver verification from volatile command is currently not supported when both CFG and IO are enabled.|
|3081|Removal of current driver verification is not supported from volatile command.|
|3082|Enabling driver verification is not supported in safe mode.|
|3083|Enabling driver verification is not supported from volatile mode in current system.|
|3084|The specified rule class (a.k.a. flag) is not supported from volatile mode.|
|3085|The specified driver is protected and volatile verification is currently not supported.|
|3086|Enabling driver verification is not supported for a driver with  NMI callback(s) registered.|
|3087|Volatile verification settings cannot be changed when verification is enabled from boot or DIF volatile verification is enabled.|
|3088|View your error log for details.|
|3089|Unable to write to this file.|
|3090|ADDPAK file is corrupted.  Delete LANMAN\NETPROG\ADDPAK.SER<br>and reapply all ADDPAKs.|
|3091|The LM386 server cannot be started because CACHE.EXE is not running.|
|3092|There is no account for this computer in the security database.|
|3093|This computer is not a member of the group SERVERS.|
|3094|The group SERVERS is not present in the local security database.|
|3095|This computer is configured as a member of a workgroup, not as<br>a member of a domain. The Netlogon service does not need to run in this<br>configuration.|
|3096|The primary Domain Controller for this domain could not be located.|
|3097|This computer is configured to be the primary domain controller of its domain.<br>However, the computer %1 is currently claiming to be the primary domain controller<br>of the domain.|
|3098|The service failed to authenticate with the primary domain controller.|
|3099|There is a problem with the security database creation date or serial number.|
|3100|The operation failed because a network software error occurred.|
|3101|The system ran out of a resource controlled by the %1 option.|
|3102|The service failed to obtain a long-term lock on the<br>segment for network control blocks (NCBs). The error code is the data.|
|3103|The service failed to release the long-term lock on the<br>segment for network control blocks (NCBs). The error code is the data.|
|3104|There was an error stopping service %1.<br>The error code from NetServiceControl is the data.|
|3105|Initialization failed because of a system execution failure on<br>path %1. The system error code is the data.|
|3106|An unexpected network control block (NCB) was received. The NCB is the data.|
|3107|The network is not started.|
|3108|A DosDevIoctl or DosFsCtl to NETWKSTA.SYS failed.<br>The data shown is in this format:<br>DWORD  approx CS:IP of call to ioctl or fsctl<br>WORD   error code<br>WORD   ioctl or fsctl number|
|3109|Unable to create or open system semaphore %1.<br>The error code is the data.|
|3110|Initialization failed because of an open/create error on the<br>file %1. The system error code is the data.|
|3111|An unexpected NetBIOS error occurred.<br>The error code is the data.|
|3112|An illegal server message block (SMB) was received.<br>The SMB is the data.|
|3113|Initialization failed because the requested service %1<br>could not be started.|
|3114|Some entries in the error log were lost because of a buffer<br>overflow.|
|3120|Initialization parameters controlling resource usage other<br>than net buffers are sized so that too much memory is needed.|
|3121|The server cannot increase the size of a memory segment.|
|3122|Initialization failed because account file %1 is either incorrect<br>or not present.|
|3123|Initialization failed because network %1 was not started.|
|3124|The server failed to start. Either all three chdev<br>parameters must be zero or all three must be nonzero.|
|3125|A remote API request was halted due to the following<br>invalid description string: %1.|
|3126|The network %1 ran out of network control blocks (NCBs).  You may need to increase NCBs<br>for this network.  The following information includes the<br>number of NCBs submitted by the server when this error occurred:|
|3127|The server cannot create the %1 mailslot needed to send<br>the ReleaseMemory alert message.  The error received is:|
|3128|The server failed to register for the ReleaseMemory alert,<br>with recipient %1. The error code from<br>NetAlertStart is the data.|
|3129|The server cannot update the AT schedule file. The file<br>is corrupted.|
|3130|The server encountered an error when calling<br>NetIMakeLMFileName. The error code is the data.|
|3131|Initialization failed because of a system execution failure on<br>path %1. There is not enough memory to start the process.<br>The system error code is the data.|
|3132|Longterm lock of the server buffers failed.<br>Check swap disk's free space and restart the system to start the server.|
|3140|The service has stopped due to repeated consecutive<br>occurrences of a network control block (NCB) error.  The last bad NCB follows<br>in raw data.|
|3141|The Message server has stopped due to a lock on the<br>Message server shared data segment.|
|3150|A file system error occurred while opening or writing to the<br>system message log file %1. Message logging has been<br>switched off due to the error. The error code is the data.|
|3151|Unable to display message POPUP due to system VIO call error.<br>The error code is the data.|
|3152|An illegal server message block (SMB) was received.  The SMB is the data.|
|3160|The workstation information segment is bigger than 64K.<br>The size follows, in DWORD format:|
|3161|The workstation was unable to get the name-number of the computer.|
|3162|The workstation could not initialize the Async NetBIOS Thread.<br>The error code is the data.|
|3163|The workstation could not open the initial shared segment.<br>The error code is the data.|
|3164|The workstation host table is full.|
|3165|A bad mailslot server message block (SMB) was received.  The SMB is the data.|
|3166|The workstation encountered an error while trying to start the user accounts database.<br>The error code is the data.|
|3167|The workstation encountered an error while responding to an SSI revalidation request.<br>The function code and the error codes are the data.|
|3170|The Alerter service had a problem creating the list of<br>alert recipients.  The error code is %1.|
|3171|There was an error expanding %1 as a group name. Try<br>splitting the group into two or more smaller groups.|
|3172|There was an error sending %2 the alert message -<br>(<br>%3 )<br>The error code is %1.|
|3173|There was an error in creating or reading the alerter mailslot.<br>The error code is %1.|
|3174|The server could not read the AT schedule file.|
|3175|The server found an invalid AT schedule record.|
|3176|The server could not find an AT schedule file so it created one.|
|3177|The server could not access the %1 network with NetBiosOpen.|
|3178|The AT command processor could not run %1.|
|3180|WARNING:  Because of a lazy-write error, drive %1 now<br>contains some corrupted data.  The cache is stopped.|
|3181|A defective sector on drive %1 has been replaced (hotfixed).<br>No data was lost.  You should run CHKDSK soon to restore full<br>performance and replenish the volume's spare sector pool.<br><br>The hotfix occurred while processing a remote request.|
|3182|A disk error occurred on the HPFS volume in drive %1.<br>The error occurred while processing a remote request.|
|3183|The user accounts database (NET.ACC) is corrupted.  The local security<br>system is replacing the corrupted NET.ACC with the backup<br>made at %1.<br>Any updates made to the database after this time are lost.<br>|
|3184|The user accounts database (NET.ACC) is missing.  The local<br>security system is restoring the backup database<br>made at %1.<br>Any updates made to the database made after this time are lost.<br>|
|3185|Local security could not be started because the user accounts database<br>(NET.ACC) was missing or corrupted, and no usable backup<br>database was present.<br><br>THE SYSTEM IS NOT SECURE.|
|3186|Local security could not be started because an error<br>occurred during initialization. The error code returned is %1.<br><br>THE SYSTEM IS NOT SECURE.<br>|
|3190|The specified driver is not associated with driver object or driver extension.|
|3191|Verifier's internal data size exceeds the limit of live dump secondary data.|
|3192|Verification cannot start because an attempt to lock code or data section failed.|
|3193|DIF volatile verification is not supported for hotpatched driver.|
|3194|The passed system DIF information is invalid.|
|3195|DIF volatile verification only supports on loaded drivers.|
|3196|Currently no plugin is running.|
|3197|Currently running plugin must be removed before applying a new plugin.|
|3198|The plugin is not allowed to run in volatile mode.|
|3199|One or more DDI is not yet supported by DIF.|
|3204|The server could not create a thread.<br>The THREADS parameter in the CONFIG.SYS file should be increased.|
|3205|The server could not close %1.<br>The file is probably corrupted.|
|3206|The replicator cannot update directory %1. It has tree integrity<br>and is the current directory for some process.|
|3207|The server cannot export directory %1 to client %2.<br>It is exported from another server.|
|3208|The replication server could not update directory %2 from the source<br>on %3 due to error %1.|
|3209|Master %1 did not send an update notice for directory %2 at the expected<br>time.|
|3210|This computer could not authenticate with %2, a Windows domain controller<br>for domain %1, and therefore this computer might deny logon requests.<br>This inability to authenticate might be caused by another computer on the<br>same network using the same name or the password for this computer account<br>is not recognized. If this message appears again, contact your system<br>administrator.|
|3211|The replicator attempted to log on at %2 as %1 and failed.|
|3212|Network error %1 occurred.|
|3213|Replicator limit for files in a directory has been exceeded.|
|3214|Replicator limit for tree depth has been exceeded.|
|3215|Unrecognized message received in mailslot.|
|3216|System error %1 occurred.|
|3217|Cannot log on. User is currently logged on and argument TRYUSER<br>is set to NO.|
|3218|IMPORT path %1 cannot be found.|
|3219|EXPORT path %1 cannot be found.|
|3220|Replicator failed to update signal file in directory %2 due to<br>%1 system error.|
|3221|Disk Fault Tolerance Error<br><br>%1|
|3222|Replicator could not access %2<br>on %3 due to system error %1.|
|3223|The primary domain controller for domain %1 has apparently failed.|
|3224|Changing machine account password for account %1 failed with<br>the following error: <br>%2|
|3225|An error occurred while updating the logon or logoff information for %1.|
|3226|An error occurred while synchronizing with primary domain controller %1|
|3227|The session setup to the Windows Domain Controller %1 for the domain %2<br>failed because %1 does not support signing or sealing the Netlogon<br>session.<br><br>Either upgrade the Domain controller or set the RequireSignOrSeal<br>registry entry on this machine to 0.|
|3230|A power failure was detected at the server.|
|3231|The UPS service performed server shut down.|
|3232|The UPS service did not complete execution of the<br>user specified shut down command file.|
|3233|The UPS driver could not be opened.  The error code is<br>the data.|
|3234|Power has been restored.|
|3235|There is a problem with a configuration of user specified<br>shut down command file.|
|3236|The UPS service failed to execute a user specified shutdown<br>command file %1.  The error code is the data.|
|3250|Initialization failed because of an invalid or missing<br>parameter in the configuration file %1.|
|3251|Initialization failed because of an invalid line in the<br>configuration file %1. The invalid line is the data.|
|3252|Initialization failed because of an error in the configuration<br>file %1.|
|3253|The file %1 has been changed after initialization.<br>The boot-block loading was temporarily terminated.|
|3254|The files do not fit to the boot-block configuration<br>file %1. Change the BASE and ORG definitions or the order<br>of the files.|
|3255|Initialization failed because the dynamic-link<br>library %1 returned an incorrect version number.|
|3256|There was an unrecoverable error in the dynamic-<br>link library of the service.|
|3257|The system returned an unexpected error code.<br>The error code is the data.|
|3258|The fault-tolerance error log file, LANROOT\LOGS\FT.LOG,<br>is more than 64K.|
|3259|The fault-tolerance error-log file, LANROOT\LOGS\FT.LOG, had the<br>update in progress bit set upon opening, which means that the<br>system crashed while working on the error log.|
|3260|This computer has been successfully joined to domain '%1'.|
|3261|This computer has been successfully joined to workgroup '%1'.|
|3299|%1 %2 %3 %4 %5 %6 %7 %8 %9.|
|3301|Remote IPC |
|3302|Remote Admin |
|3303|Logon server share |
|3304|A network error occurred. |
|3400|There is not enough memory to start the Workstation service.|
|3401|An error occurred when reading the NETWORKS entry in the LANMAN.INI file.|
|3402|This is an invalid argument: %1.|
|3403|The %1 NETWORKS entry in the LANMAN.INI file has a<br>syntax error and will be ignored.|
|3404|There are too many NETWORKS entries in the LANMAN.INI file.|
|3406|An error occurred when opening network<br>device driver %1 = %2.|
|3407|Device driver %1 sent a bad BiosLinkage response.|
|3408|The program cannot be used with this operating system.|
|3409|The redirector is already installed.|
|3410|Installing NETWKSTA.SYS Version %1.%2.%3  (%4)<br>|
|3411|There was an error installing NETWKSTA.SYS.<br><br>Press ENTER to continue.|
|3412|Resolver linkage problem.|
|3413|Your logon time at %1 ends at %2.<br>Please clean up and log off.|
|3414|You will be automatically disconnected at %1.|
|3415|Your logon time at %1 has ended.|
|3416|Your logon time at %1 ended at %2.|
|3417|WARNING: You have until %1 to logoff. If you<br>have not logged off at this time, your session will be<br>disconnected, and any open files or devices you<br>have open may lose data.|
|3418|WARNING: You must log off at %1 now.  You have<br>two minutes to log off, or you will be disconnected.|
|3419|You have open files or devices, and a forced<br>disconnection may cause you to lose data.|
|3420|Default Share for Internal Use |
|3421|Messenger Service |
|3500|The command completed successfully.|
|3501|You used an invalid option.|
|3502|System error %1 has occurred.|
|3503|The command contains an invalid number of arguments.|
|3504|The command completed with one or more errors.|
|3505|You used an option with an invalid value.|
|3506|The option %1 is unknown.|
|3507|Option %1 is ambiguous.|
|3510|A command was used with conflicting switches.|
|3511|Could not find subprogram %1.|
|3512|The software requires a newer version of the operating<br>system.|
|3513|More data is available than can be returned by Windows.|
|3514|More help is available by typing NET HELPMSG %1.|
|3515|This command can be used only on a Windows Domain Controller.|
|3516|This command cannot be used on a Windows Domain Controller.|
|3520|These Windows services are started:|
|3521|The %1 service is not started.|
|3522|The %1 service is starting|
|3523|The %1 service could not be started.|
|3524|The %1 service was started successfully.|
|3525|Stopping the Workstation service also stops the Server service.|
|3526|The workstation has open files.|
|3527|The %1 service is stopping|
|3528|The %1 service could not be stopped.|
|3529|The %1 service was stopped successfully.|
|3530|The following services are dependent on the %1 service.<br>Stopping the %1 service will also stop these services.|
|3533|The service is starting or stopping.  Please try again later.|
|3534|The service did not report an error.|
|3535|An error occurred controlling the device.|
|3536|The %1 service was continued successfully.|
|3537|The %1 service was paused successfully.|
|3538|The %1 service failed to resume.|
|3539|The %1 service failed to pause.|
|3540|The %1 service continue is pending|
|3541|The %1 service pause is pending|
|3542|%1 was continued successfully.|
|3543|%1 was paused successfully.|
|3544|The %1 service has been started by another process and is pending.|
|3547|A service specific error occurred: %1.|
|3660|These workstations have sessions on this server:|
|3661|These workstations have sessions with open files on this server:|
|3666|The message alias is forwarded.|
|3670|You have these remote connections:|
|3671|Continuing will cancel the connections.|
|3675|The session from %1 has open files.|
|3676|New connections will be remembered.|
|3677|New connections will not be remembered.|
|3678|An error occurred while saving your profile : Access Denied. The state of your remembered connections has not changed.|
|3679|An error occurred while reading your profile.|
|3680|An error occurred while restoring the connection to %1.|
|3682|No network services are started.|
|3683|There are no entries in the list.|
|3688|Users have open files on %1.  Continuing the operation will force the files closed.|
|3689|The Workstation service is already running. Windows will ignore command options for the workstation.|
|3691|There are open files and/or incomplete directory searches pending on the connection to %1.|
|3693|The request will be processed at a domain controller for domain %1.|
|3694|The shared queue cannot be deleted while a print job is being spooled to the queue.|
|3695|%1 has a remembered connection to %2.|
|3710|An error occurred while opening the Help file.|
|3711|The Help file is empty.|
|3712|The Help file is corrupted.|
|3713|Could not find a domain controller for domain %1.|
|3714|This operation is privileged on systems with earlier<br>versions of the software.|
|3716|The device type is unknown.|
|3717|The log file has been corrupted.|
|3718|Program filenames must end with .EXE.|
|3719|A matching share could not be found so nothing was deleted.|
|3720|A bad value is in the units-per-week field of the user record.|
|3721|The password is invalid for %1.|
|3722|An error occurred while sending a message to %1.|
|3723|The password or user name is invalid for %1.|
|3725|An error occurred when the share was deleted.|
|3726|The user name is invalid.|
|3727|The password is invalid.|
|3728|The passwords do not match.|
|3729|Your persistent connections were not all restored.|
|3730|This is not a valid computer name or domain name.|
|3732|Default permissions cannot be set for that resource.|
|3734|A valid password was not entered.|
|3735|A valid name was not entered.|
|3736|The resource named cannot be shared.|
|3737|The permissions string contains invalid permissions.|
|3738|You can only perform this operation on printers and communication devices.|
|3742|%1 is an invalid user or group name.|
|3743|The server is not configured for remote administration.|
|3752|No users have sessions with this server.|
|3753|User %1 is not a member of group %2.|
|3754|User %1 is already a member of group %2.|
|3755|There is no such user: %1.|
|3756|This is an invalid response.|
|3757|No valid response was provided.|
|3758|The destination list provided does not match the destination list of the printer queue.|
|3759|Your password cannot be changed until %1.|
|3760|%1 is not a recognized day of the week.|
|3761|The time range specified ends before it starts.|
|3762|%1 is not a recognized hour.|
|3763|%1 is not a valid specification for minutes.|
|3764|Time supplied is not exactly on the hour.|
|3765|12 and 24 hour time formats may not be mixed.|
|3766|%1 is not a valid 12-hour suffix.|
|3767|An illegal date format has been supplied.|
|3768|An illegal day range has been supplied.|
|3769|An illegal time range has been supplied.|
|3770|Arguments to NET USER are invalid. Check the minimum password<br>length and/or arguments supplied.|
|3771|The value for ENABLESCRIPT must be YES.|
|3773|An illegal country/region code has been supplied.|
|3774|The user was successfully created but could not be added<br>to the USERS local group.|
|3775|The user context supplied is invalid.|
|3776|The dynamic-link library %1 could not be loaded, or an error<br>occurred while trying to use it.|
|3777|Sending files is no longer supported.|
|3778|You may not specify paths for ADMIN$ and IPC$ shares.|
|3779|User or group %1 is already a member of local group %2.|
|3780|There is no such user or group: %1.|
|3781|There is no such computer: %1.|
|3782|The computer %1 already exists.|
|3783|There is no such global user or group: %1.|
|3784|Only disk shares can be marked as cacheable|
|3790|The system could not find message: %1.|
|3802|This schedule date is invalid.|
|3803|The LANMAN root directory is unavailable.|
|3804|The SCHED.LOG file could not be opened.|
|3805|The Server service has not been started.|
|3806|The AT job ID does not exist.|
|3807|The AT schedule file is corrupted.|
|3808|The delete failed due to a problem with the AT schedule file.|
|3809|The command line cannot exceed 259 characters.|
|3810|The AT schedule file could not be updated because the disk is full.|
|3812|The AT schedule file is invalid.  Please delete the file and create a new one.|
|3813|The AT schedule file was deleted.|
|3814|The syntax of this command is:<br><br>AT [id] [/DELETE]<br>AT time [/EVERY:date | /NEXT:date] command<br><br>The AT command schedules a program command to run at a<br>later date and time on a server.  It also displays the<br>list of programs and commands scheduled to be run.<br><br>You can specify the date as M,T,W,Th,F,Sa,Su or 1-31<br>for the day of the month.<br><br>You can specify the time in the 24 hour HH:MM format.|
|3815|The AT command has timed-out.<br>Please try again later.|
|3816|The minimum password age for user accounts cannot be greater<br>than the maximum password age.|
|3817|You have specified a value that is incompatible<br>with servers with down-level software. Please specify a lower value.|
|3870|%1 is not a valid computer name.|
|3871|%1 is not a valid Windows network message number.|
|3900|Message from %1 to %2 on %3|
|3901|****|
|3902|**** unexpected end of message ****|
|3905|Press ESC to exit|
|3906|...|
|3910|Current time at %1 is %2|
|3911|The current local clock is %1<br>Do you want to set the local computer's time to match the<br>time at %2? %3: |
|3912|Could not locate a time-server.|
|3913|Could not find the domain controller for domain %1.|
|3914|Local time (GMT%3) at %1 is %2|
|3915|The user's home directory could not be determined.|
|3916|The user's home directory has not been specified.|
|3917|The name specified for the user's home directory (%1) is not a universal naming convention (UNC) name.|
|3918|Drive %1 is now connected to %2. Your home directory is %3\%4.|
|3919|Drive %1 is now connected to %2.|
|3920|There are no available drive letters left.|
|3932|%1 is not a valid domain or workgroup name.|
|3935|The current SNTP value is: %1|
|3936|This computer is not currently configured to use a specific SNTP server.|
|3937|This current autoconfigured SNTP value is: %1|
|3950|Reissue the given operation as a cached IO operation|
|3951|You specified too many values for the %1 option.|
|3952|You entered an invalid value for the %1 option.|
|3953|The syntax is incorrect.|
|3960|You specified an invalid file number.|
|3961|You specified an invalid print job number.|
|3963|The user or group account specified cannot be found.|
|3965|The user was added but could not be enabled for File and Print<br>Services for NetWare.|
|3966|File and Print Services for NetWare is not installed.|
|3967|Cannot set user properties for File and Print Services for NetWare.|
|3968|Password for %1 is: %2|
|3969|NetWare compatible logon|
|4000|WINS encountered an error while processing the command.|
|4001|The local WINS cannot be deleted.|
|4002|The importation from the file failed.|
|4003|The backup failed. Was a full backup done before?|
|4004|The backup failed. Check the directory to which you are backing the database.|
|4005|The name does not exist in the WINS database.|
|4006|Replication with a nonconfigured partner is not allowed.|
|4050|The version of the supplied content information is not supported.|
|4051|The supplied content information is malformed.|
|4052|The requested data cannot be found in local or peer caches.|
|4053|No more data is available or required.|
|4054|The supplied object has not been initialized.|
|4055|The supplied object has already been initialized.|
|4056|A shutdown operation is already in progress.|
|4057|The supplied object has already been invalidated.|
|4058|An element already exists and was not replaced.|
|4059|Can not cancel the requested operation as it has already been completed.|
|4060|Can not perform the requested operation because it has already been carried out.|
|4061|An operation accessed data beyond the bounds of valid data.|
|4062|The requested version is not supported.|
|4063|A configuration value is invalid.|
|4064|The SKU is not licensed.|
|4065|PeerDist Service is still initializing and will be available shortly.|
|4066|Communication with one or more computers will be temporarily blocked due to recent errors.|
|4100|The DHCP client has obtained an IP address that is already in use on the network. The local interface will be disabled until the DHCP client can obtain a new address.|
|4200|The GUID passed was not recognized as valid by a WMI data provider.|
|4201|The instance name passed was not recognized as valid by a WMI data provider.|
|4202|The data item ID passed was not recognized as valid by a WMI data provider.|
|4203|The WMI request could not be completed and should be retried.|
|4204|The WMI data provider could not be located.|
|4205|The WMI data provider references an instance set that has not been registered.|
|4206|The WMI data block or event notification has already been enabled.|
|4207|The WMI data block is no longer available.|
|4208|The WMI data service is not available.|
|4209|The WMI data provider failed to carry out the request.|
|4210|The WMI MOF information is not valid.|
|4211|The WMI registration information is not valid.|
|4212|The WMI data block or event notification has already been disabled.|
|4213|The WMI data item or data block is read only.|
|4214|The WMI data item or data block could not be changed.|
|4250|This operation is only valid in the context of an app container.|
|4251|This application can only run in the context of an app container.|
|4252|This functionality is not supported in the context of an app container.|
|4253|The length of the SID supplied is not a valid length for app container SIDs.|
|4300|The media identifier does not represent a valid medium.|
|4301|The library identifier does not represent a valid library.|
|4302|The media pool identifier does not represent a valid media pool.|
|4303|The drive and medium are not compatible or exist in different libraries.|
|4304|The medium currently exists in an offline library and must be online to perform this operation.|
|4305|The operation cannot be performed on an offline library.|
|4306|The library, drive, or media pool is empty.|
|4307|The library, drive, or media pool must be empty to perform this operation.|
|4308|No media is currently available in this media pool or library.|
|4309|A resource required for this operation is disabled.|
|4310|The media identifier does not represent a valid cleaner.|
|4311|The drive cannot be cleaned or does not support cleaning.|
|4312|The object identifier does not represent a valid object.|
|4313|Unable to read from or write to the database.|
|4314|The database is full.|
|4315|The medium is not compatible with the device or media pool.|
|4316|The resource required for this operation does not exist.|
|4317|The operation identifier is not valid.|
|4318|The media is not mounted or ready for use.|
|4319|The device is not ready for use.|
|4320|The operator or administrator has refused the request.|
|4321|The drive identifier does not represent a valid drive.|
|4322|Library is full. No slot is available for use.|
|4323|The transport cannot access the medium.|
|4324|Unable to load the medium into the drive.|
|4325|Unable to retrieve the drive status.|
|4326|Unable to retrieve the slot status.|
|4327|Unable to retrieve status about the transport.|
|4328|Cannot use the transport because it is already in use.|
|4329|Unable to open or close the inject/eject port.|
|4330|Unable to eject the medium because it is in a drive.|
|4331|A cleaner slot is already reserved.|
|4332|A cleaner slot is not reserved.|
|4333|The cleaner cartridge has performed the maximum number of drive cleanings.|
|4334|Unexpected on-medium identifier.|
|4335|The last remaining item in this group or resource cannot be deleted.|
|4336|The message provided exceeds the maximum size allowed for this parameter.|
|4337|The volume contains system or paging files.|
|4338|The media type cannot be removed from this library since at least one drive in the library reports it can support this media type.|
|4339|This offline media cannot be mounted on this system since no enabled drives are present which can be used.|
|4340|A cleaner cartridge is present in the tape library.|
|4341|Cannot use the inject/eject port because it is not empty.|
|4342|Error|
|4343|OK|
|4344|Y|
|4345|N|
|4346|Any|
|4347|A|
|4348|P|
|4349|(not found)|
|4350|This file is currently not available for use on this computer.|
|4351|The remote storage service is not operational at this time.|
|4352|The remote storage service encountered a media error.|
|4353|Read|
|4354|Change|
|4355|Full|
|4356|Please type the password: |
|4357|Type the password for %1: |
|4358|Type a password for the user: |
|4359|Type the password for the shared resource: |
|4360|Type your password: |
|4361|Retype the password to confirm: |
|4362|Type the user's old password: |
|4363|Type the user's new password: |
|4364|Type your new password: |
|4365|Type the Replicator service password: |
|4366|Type your user name, or press ENTER if it is %1: |
|4367|Type the domain or server where you want to change a password, or<br>press ENTER if it is for domain %1: |
|4368|Type your user name: |
|4369|Network statistics for \\%1|
|4370|Printing options for %1|
|4371|Communication-device queues accessing %1|
|4372|Print job detail|
|4373|Communication-device queues at \\%1|
|4374|Printers at %1|
|4375|Printers accessing %1|
|4376|Print jobs at %1:|
|4377|Shared resources at %1|
|4378|The following running services can be controlled:|
|4379|Statistics are available for the following running services:|
|4380|User accounts for \\%1|
|4381|The syntax of this command is:|
|4382|The options of this command are:|
|4383|Please enter the name of the Primary Domain Controller: |
|4384|The string you have entered is too long. The maximum<br>is %1, please reenter. |
|4385|Sunday|
|4386|Monday|
|4387|Tuesday|
|4388|Wednesday|
|4389|Thursday|
|4390|The file or directory is not a reparse point.|
|4391|The reparse point attribute cannot be set because it conflicts with an existing attribute.|
|4392|The data present in the reparse point buffer is invalid.|
|4393|The tag present in the reparse point buffer is invalid.|
|4394|There is a mismatch between the tag specified in the request and the tag present in the reparse point.|
|4395|The object manager encountered a reparse point while retrieving an object.|
|4396|Th|
|4397|F|
|4398|S|
|4399|Sa|
|4400|Fast Cache data not found.|
|4401|Fast Cache data expired.|
|4402|Fast Cache data corrupt.|
|4403|Fast Cache data has exceeded its max size and cannot be updated.|
|4404|Fast Cache has been ReArmed and requires a reboot until it can be updated.|
|4405|Aliases for \\%1|
|4406|Alias name|
|4407|Comment|
|4408|Members|
|4410|User Accounts for \\%1|
|4411|User name|
|4412|Full Name|
|4413|Comment|
|4414|User's comment|
|4415|Parameters|
|4416|Country/region code|
|4417|Privilege level|
|4418|Operator privileges|
|4419|Account active|
|4420|Secure Boot detected that rollback of protected data has been attempted.|
|4421|The value is protected by Secure Boot policy and cannot be modified or deleted.|
|4422|The Secure Boot policy is invalid.|
|4423|A new Secure Boot policy did not contain the current publisher on its update list.|
|4424|The Secure Boot policy is either not signed or is signed by a non-trusted signer.|
|4425|Secure Boot is not enabled on this machine.|
|4426|Secure Boot requires that certain files and drivers are not replaced by other files or drivers.|
|4427|The Secure Boot Supplemental Policy file was not authorized on this machine.|
|4428|The Supplemental Policy is not recognized on this device.|
|4429|The Antirollback version was not found in the Secure Boot Policy.|
|4430|The Platform ID specified in the Secure Boot policy does not match the Platform ID on this device.|
|4431|The Secure Boot policy file has an older Antirollback Version than this device.|
|4432|The Secure Boot policy file does not match the upgraded legacy policy.|
|4433|The Secure Boot policy file is required but could not be found.|
|4434|Supplemental Secure Boot policy file can not be loaded as a base Secure Boot policy.|
|4435|Base Secure Boot policy file can not be loaded as a Supplemental Secure Boot policy.|
|4436|Home directory|
|4437|Password required|
|4438|User may change password|
|4439|User profile|
|4440|The copy offload read operation is not supported by a filter.|
|4441|The copy offload write operation is not supported by a filter.|
|4442|The copy offload read operation is not supported for the file.|
|4443|The copy offload write operation is not supported for the file.|
|4444|This file is currently associated with a different stream id.|
|4445|The volume must undergo garbage collection.|
|4446|The WOF driver encountered a corruption in WIM image's Header.|
|4447|The WOF driver encountered a corruption in WIM image's Resource Table.|
|4448|The WOF driver encountered a corruption in the compressed file's Resource Table.|
|4449|The request cannot be completed as it requires modifying an immutable object.|
|4450|Computer name|
|4451|User name|
|4452|Software version|
|4453|Workstation active on|
|4454|Windows NT root directory|
|4455|Workstation domain|
|4456|Logon domain|
|4457|Other domain(s)|
|4458|COM Open Timeout (sec)|
|4459|COM Send Count (byte)|
|4460|COM Send Timeout (msec)|
|4461|DOS session print time-out (sec)|
|4462|Maximum error log size (K)|
|4463|Maximum cache memory (K)|
|4464|Number of network buffers|
|4465|Number of character buffers|
|4466|Size of network buffers|
|4467|Size of character buffers|
|4468|Full Computer name|
|4469|Workstation Domain DNS Name|
|4470|Windows 2002|
|4481|Server Name|
|4482|Server Comment|
|4483|Send administrative alerts to|
|4484|Software version|
|4485|Peer Server|
|4486|Windows NT|
|4487|Server Level|
|4488|Windows NT Server|
|4489|Server is active on|
|4492|Server hidden|
|4500|Single Instance Storage is not available on this volume.|
|4506|Maximum Logged On Users|
|4507|Maximum concurrent administrators|
|4508|Maximum resources shared|
|4509|Maximum connections to resources|
|4510|Maximum open files on server|
|4511|Maximum open files per session|
|4512|Maximum file locks|
|4520|Idle session time (min)|
|4526|Share-level|
|4527|User-level|
|4530|Unlimited Server|
|4550|System Integrity detected that policy rollback has been attempted.|
|4551|Your organization used Device Guard to block this app. Contact your support person for more info.|
|4552|The System Integrity policy is invalid.|
|4553|The System Integrity policy is either not signed or is signed by a non-trusted signer.|
|4554|The number of System Integrity policies is out of limit.|
|4555|The Code Integrity supplemental policy is not authorized by a Code Integrity base policy.|
|4556|System Integrity policy has been violated.  Malicious binary reputation.|
|4557|System Integrity policy has been violated.  Potentially unwanted application.|
|4558|System Integrity policy has been violated.  Dangerous file extension from the web.|
|4559|System Integrity policy has been violated.  Unable to contact reputation service for unknown file.|
|4560|Virtual Secure Mode (VSM) is not initialized. The hypervisor or VSM may not be present or enabled.|
|4561|The hypervisor is not protecting DMA because an IOMMU is not present or not enabled in the BIOS.|
|4570|The Platform Manifest file was not authorized on this machine.|
|4571|The Platform Manifest file was not valid.|
|4572|The file is not authorized on this platform because an entry was not found in the Platform Manifest.|
|4573|The catalog is not authorized on this platform because an entry was not found in the Platform Manifest.|
|4574|The file is not authorized on this platform because a Binary ID was not found in the embedded signature.|
|4575|No active Platform Manifest exists on this system.|
|4576|The Platform Manifest file was not properly signed.|
|4577|Primary Domain controller for workstation domain:|
|4578|Lockout threshold:|
|4579|Lockout duration (minutes):|
|4580|System Integrity policy has been violated.  Unfriendly file.|
|4581|System Integrity policy has been violated.  Failed to obtain file reputation because an infrastructure issue occurred. Try again later.|
|4582|System Integrity policy has been violated.  Explicit denied file.|
|4600|Statistics since|
|4601|Sessions accepted|
|4602|Sessions timed-out|
|4603|Sessions errored-out|
|4604|Kilobytes sent|
|4605|Kilobytes received|
|4606|Mean response time (msec)|
|4607|Network errors|
|4608|Files accessed|
|4609|Print jobs spooled|
|4610|System errors|
|4611|Password violations|
|4612|Permission violations|
|4613|Communication devices accessed|
|4614|Sessions started|
|4615|Sessions reconnected|
|4616|Sessions starts failed|
|4617|Sessions disconnected|
|4618|Network I/O's performed|
|4619|Files and pipes accessed|
|4620|Times buffers exhausted|
|4621|Big buffers|
|4622|Request buffers|
|4623|Workstation Statistics for \\%1|
|4624|Server Statistics for \\%1|
|4625|Statistics since %1|
|4626|Connections made|
|4627|Connections failed|
|4630|Bytes received|
|4631|Server Message Blocks (SMBs) received|
|4632|Bytes transmitted|
|4633|Server Message Blocks (SMBs) transmitted|
|4634|Read operations|
|4635|Write operations|
|4636|Raw reads denied|
|4637|Raw writes denied|
|4638|Network errors|
|4639|Connections made|
|4640|Reconnections made|
|4641|Server disconnects|
|4642|Sessions started|
|4643|Hung sessions|
|4644|Failed sessions|
|4645|Failed operations|
|4646|Use count|
|4647|Failed use count|
|4650|%1 was deleted successfully.|
|4651|%1 was used successfully.|
|4652|The message was successfully sent to %1.|
|4653|The message name %1 was forwarded successfully.|
|4654|The message name %1 was added successfully.|
|4655|The message name forwarding was successfully canceled.|
|4656|%1 was shared successfully.|
|4657|The server %1 successfully logged you on as %2.|
|4658|%1 was logged off successfully.|
|4659|%1 was successfully removed from the list of shares the Server creates<br>on startup.|
|4661|The password was changed successfully.|
|4662|%1 file(s) copied.|
|4663|%1 file(s) moved.|
|4664|The message was successfully sent to all users of the network.|
|4665|The message was successfully sent to domain %1.|
|4666|The message was successfully sent to all users of this server.|
|4667|The message was successfully sent to group *%1.|
|4695|Microsoft LAN Manager Version %1|
|4696|Windows NT Server|
|4697|Windows NT Workstation|
|4698|MS-DOS Enhanced Workstation|
|4699|Created at %1|
|4700|Server Name            Remark|
|4701|Cannot enumerate servers in non-default compartment.|
|4702|(UNC)|
|4703|...|
|4704|Domain|
|4705|Resources on %1|
|4706|Invalid network provider.  Available networks are:|
|4710|Disk|
|4711|Print|
|4712|Comm|
|4713|IPC|
|4714|Status       Local     Remote                    Network|
|4715|OK|
|4716|Dormant|
|4717|Paused|
|4718|Disconnected|
|4719|Error|
|4720|Connecting|
|4721|Reconnecting|
|4722|Status|
|4723|Local name|
|4724|Remote name|
|4725|Resource type|
|4726|# Opens|
|4727|# Connections|
|4728|Unavailable|
|4730|Share name   Resource                        Remark|
|4731|Share name|
|4732|Resource|
|4733|Spooled|
|4734|Permission|
|4735|Maximum users|
|4736|No limit|
|4737|Users|
|4738|The share name entered may not be accessible from some MS-DOS workstations.<br>Are you sure you want to use this share name? %1: |
|4739|Caching|
|4740|ID         Path                                    User name            # Locks|
|4741|File ID|
|4742|Locks|
|4743|Permissions|
|4744|Share name|
|4745|Type|
|4746|Used as|
|4747|Comment|
|4750|Computer               User name            Client Type       Opens Idle time|
|4751|Computer|
|4752|Sess time|
|4753|Idle time|
|4754|Share name     Type     # Opens|
|4755|Client type|
|4756|Guest logon|
|4770|Manual caching of documents|
|4771|Automatic caching of documents|
|4772|Automatic caching of programs and documents|
|4773|Manual caching of documents with BranchCache enabled|
|4774|Caching disabled|
|4775|Automatic|
|4776|Manual|
|4777|Documents|
|4778|Programs|
|4779|BranchCache|
|4780|None|
|4800|Name|
|4801|Forwarded to|
|4802|Forwarded to you from|
|4803|Users of this server|
|4804|Net Send has been interrupted by a Ctrl+Break from the user.|
|4810|Name                         Job #      Size            Status|
|4811|jobs|
|4812|Print|
|4813|Name|
|4814|Job #|
|4815|Size|
|4816|Status|
|4817|Separator file|
|4818|Comment|
|4819|Priority|
|4820|Print after|
|4821|Print until|
|4822|Print processor|
|4823|Additional info|
|4824|Parameters|
|4825|Print Devices|
|4826|Printer Active|
|4827|Printer held|
|4828|Printer error|
|4829|Printer being deleted|
|4830|Printer status unknown|
|4840|Held until %1|
|4841|Job #|
|4842|Submitting user|
|4843|Notify|
|4844|Job data type|
|4845|Job parameters|
|4846|Waiting|
|4847|Held in queue|
|4848|Spooling|
|4849|Paused|
|4850|Offline|
|4851|Error|
|4852|Out of paper|
|4853|Intervention required|
|4854|Printing|
|4855|on |
|4856|Paused on %1|
|4857|Offline on %1|
|4858|Error on%1|
|4859|Out of Paper on %1|
|4860|Check printer on %1|
|4861|Printing on %1|
|4862|Driver|
|4930|User name              Type                 Date|
|4931|Lockout|
|4932|Service|
|4933|Server|
|4934|Server started|
|4935|Server paused|
|4936|Server continued|
|4937|Server stopped|
|4938|Session|
|4939|Logon Guest|
|4940|Logon User|
|4941|Logon Administrator|
|4942|Logoff normal|
|4943|Logon|
|4944|Logoff error|
|4945|Logoff auto-disconnect|
|4946|Logoff administrator-disconnect|
|4947|Logoff forced by logon restrictions|
|4948|Service|
|4949|%1 Installed|
|4950|%1 Install Pending|
|4951|%1 Paused|
|4952|%1 Pause Pending|
|4953|%1 Continued|
|4954|%1 Continue Pending|
|4955|%1 Stopped|
|4956|%1 Stop Pending|
|4957|Account|
|4958|User account %1 was modified.|
|4959|Group account %1 was modified.|
|4960|User account %1 was deleted|
|4961|Group account %1 was deleted|
|4962|User account %1 was added|
|4963|Group account %1 was added|
|4964|Account system settings were modified|
|4965|Logon restriction|
|4966|Limit exceeded:  UNKNOWN|
|4967|Limit exceeded:  Logon hours|
|4968|Limit exceeded:  Account expired|
|4969|Limit exceeded:  Workstation ID invalid|
|4970|Limit exceeded:  Account disabled|
|4971|Limit exceeded:  Account deleted|
|4972|Share|
|4973|Use %1|
|4974|Unuse %1|
|4975|User's session disconnected %1|
|4976|Administrator stopped sharing resource %1|
|4977|User reached limit for %1|
|4978|Bad password|
|4979|Administrator privilege required|
|4980|Access|
|4981|%1 permissions added|
|4982|%1 permissions modified|
|4983|%1 permissions deleted|
|4984|Access denied|
|4985|Unknown|
|4986|Other|
|4987|Duration:|
|4988|Duration: Not available|
|4989|Duration: Less than one second|
|4990|(none)|
|4991|Closed %1|
|4992|Closed %1 (disconnected)|
|4993|Administrator closed %1|
|4994|Access ended|
|4995|Log on to network|
|4996|Logon denied|
|4997|Program             Message             Time|
|4998|Account locked due to %1 bad passwords|
|4999|Account unlocked by administrator|
|5000|Log off network|
|5001|The operation cannot be completed because other resources are dependent on this resource.|
|5002|The cluster resource dependency cannot be found.|
|5003|The cluster resource cannot be made dependent on the specified resource because it is already dependent.|
|5004|The cluster resource is not online.|
|5005|A cluster node is not available for this operation.|
|5006|The cluster resource is not available.|
|5007|The cluster resource could not be found.|
|5008|The cluster is being shut down.|
|5009|A cluster node cannot be evicted from the cluster unless the node is down or it is the last node.|
|5010|The object already exists.|
|5011|The object is already in the list.|
|5012|The cluster group is not available for any new requests.|
|5013|The cluster group could not be found.|
|5014|The operation could not be completed because the cluster group is not online.|
|5015|The operation failed because either the specified cluster node is not the owner of the resource, or the node is not a possible owner of the resource.|
|5016|The operation failed because either the specified cluster node is not the owner of the group, or the node is not a possible owner of the group.|
|5017|The cluster resource could not be created in the specified resource monitor.|
|5018|The cluster resource could not be brought online by the resource monitor.|
|5019|The operation could not be completed because the cluster resource is online.|
|5020|The cluster resource could not be deleted or brought offline because it is the quorum resource.|
|5021|The cluster could not make the specified resource a quorum resource because it is not capable of being a quorum resource.|
|5022|The cluster software is shutting down.|
|5023|The group or resource is not in the correct state to perform the requested operation.|
|5024|The properties were stored but not all changes will take effect until the next time the resource is brought online.|
|5025|The cluster could not make the specified resource a quorum resource because it does not belong to a shared storage class.|
|5026|The cluster resource could not be deleted since it is a core resource.|
|5027|The quorum resource failed to come online.|
|5028|The quorum log could not be created or mounted successfully.|
|5029|The cluster log is corrupt.|
|5030|The record could not be written to the cluster log since it exceeds the maximum size.|
|5031|The cluster log exceeds its maximum size.|
|5032|No checkpoint record was found in the cluster log.|
|5033|The minimum required disk space needed for logging is not available.|
|5034|The cluster node failed to take control of the quorum resource because the resource is owned by another active node.|
|5035|A cluster network is not available for this operation.|
|5036|A cluster node is not available for this operation.|
|5037|All cluster nodes must be running to perform this operation.|
|5038|A cluster resource failed.|
|5039|The cluster node is not valid.|
|5040|The cluster node already exists.|
|5041|A node is in the process of joining the cluster.|
|5042|The cluster node was not found.|
|5043|The cluster local node information was not found.|
|5044|The cluster network already exists.|
|5045|The cluster network was not found.|
|5046|The cluster network interface already exists.|
|5047|The cluster network interface was not found.|
|5048|The cluster request is not valid for this object.|
|5049|The cluster network provider is not valid.|
|5050|The cluster node is down.|
|5051|The cluster node is not reachable.|
|5052|The cluster node is not a member of the cluster.|
|5053|A cluster join operation is not in progress.|
|5054|The cluster network is not valid.|
|5055|Mar|
|5056|The cluster node is up.|
|5057|The cluster IP address is already in use.|
|5058|The cluster node is not paused.|
|5059|No cluster security context is available.|
|5060|The cluster network is not configured for internal cluster communication.|
|5061|The cluster node is already up.|
|5062|The cluster node is already down.|
|5063|The cluster network is already online.|
|5064|The cluster network is already offline.|
|5065|The cluster node is already a member of the cluster.|
|5066|The cluster network is the only one configured for internal cluster communication between two or more active cluster nodes. The internal communication capability cannot be removed from the network.|
|5067|One or more cluster resources depend on the network to provide service to clients. The client access capability cannot be removed from the network.|
|5068|This operation cannot currently be performed on the cluster group containing the quorum resource.|
|5069|The cluster quorum resource is not allowed to have any dependencies.|
|5070|The cluster node is paused.|
|5071|The cluster resource cannot be brought online. The owner node cannot run this resource.|
|5072|The cluster node is not ready to perform the requested operation.|
|5073|The cluster node is shutting down.|
|5074|The cluster join operation was aborted.|
|5075|The node failed to join the cluster because the joining node and other nodes in the cluster have incompatible operating system versions. To get more information about operating system versions of the cluster, run the Validate a Configuration Wizard or the Test-Cluster Windows PowerShell cmdlet.|
|5076|This resource cannot be created because the cluster has reached the limit on the number of resources it can monitor.|
|5077|The system configuration changed during the cluster join or form operation. The join or form operation was aborted.|
|5078|The specified resource type was not found.|
|5079|The specified node does not support a resource of this type. This may be due to version inconsistencies or due to the absence of the resource DLL on this node.|
|5080|The specified resource name is not supported by this resource DLL. This may be due to a bad (or changed) name supplied to the resource DLL.|
|5081|No authentication package could be registered with the RPC server.|
|5082|You cannot bring the group online because the owner of the group is not in the preferred list for the group. To change the owner node for the group, move the group.|
|5083|The join operation failed because the cluster database sequence number has changed or is incompatible with the locker node. This may happen during a join operation if the cluster database was changing during the join.|
|5084|The resource monitor will not allow the fail operation to be performed while the resource is in its current state. This may happen if the resource is in a pending state.|
|5085|A non locker code got a request to reserve the lock for making global updates.|
|5086|The quorum disk could not be located by the cluster service.|
|5087|The backed up cluster database is possibly corrupt.|
|5088|A DFS root already exists in this cluster node.|
|5089|An attempt to modify a resource property failed because it conflicts with another existing property.|
|5090|This operation is not supported on a cluster without an Administrator Access Point.|
|5091|Denmark|
|5092|Sweden|
|5093|Norway|
|5094|Germany|
|5095|Australia|
|5096|Japan|
|5097|Korea|
|5098|China (PRC)|
|5099|Taiwan|
|5100|Asia|
|5101|Portugal|
|5102|Finland|
|5103|Arabic|
|5104|Hebrew|
|5150|A power failure has occurred at %1.  Please terminate all activity with this server.|
|5151|Power has been restored at %1.  Normal operations have resumed.|
|5152|The UPS service is starting shut down at %1.|
|5153|The UPS service is about to perform final shut down.|
|5170|The Workstation must be started with the NET START command.|
|5175|Remote IPC|
|5176|Remote Admin|
|5177|Default share|
|5178|User Profiles|
|5280|The password entered is longer than 14 characters.  Computers<br>with Windows prior to Windows 2000 will not be able to use<br>this account. Do you want to continue this operation? %1: |
|5281|%1 has a remembered connection to %2. Do you<br>want to overwrite the remembered connection? %3: |
|5282|Do you want to resume loading the profile?  The command which<br>caused the error will be ignored. %1: |
|5284|Do you want to continue this operation? %1: |
|5285|Do you want to add this? %1: |
|5286|Do you want to continue this operation? %1: |
|5287|Is it OK to start it? %1: |
|5288|Do you want to start the Workstation service? %1: |
|5289|Is it OK to continue disconnecting and force them closed? %1: |
|5290|The printer does not exist.  Do you want to create it? %1: |
|5291|Never|
|5292|Never|
|5293|Never|
|5295|NET.HLP|
|5296|NET.HLP|
|5297|Deny|
|5300|The network control block (NCB) request completed successfully.<br>The NCB is the data.|
|5301|Illegal network control block (NCB) buffer length on SEND DATAGRAM,<br>SEND BROADCAST, ADAPTER STATUS, or SESSION STATUS.<br>The NCB is the data.|
|5302|The data descriptor array specified in the network control block (NCB) is<br>invalid.  The NCB is the data.|
|5303|The command specified in the network control block (NCB) is illegal.<br>The NCB is the data.|
|5304|The message correlator specified in the network control block (NCB) is<br>invalid.  The NCB is the data.|
|5305|A network control block (NCB) command timed-out.  The session may have<br>terminated abnormally.  The NCB is the data.|
|5306|An incomplete network control block (NCB) message was received.<br>The NCB is the data.|
|5307|The buffer address specified in the network control block (NCB) is illegal.<br>The NCB is the data.|
|5308|The session number specified in the network control block (NCB) is not active.<br>The NCB is the data.|
|5309|No resource was available in the network adapter.<br>The network control block (NCB) request was refused.  The NCB is the data.|
|5310|The session specified in the network control block (NCB) was closed.<br>The NCB is the data.|
|5311|The network control block (NCB) command was canceled.<br>The NCB is the data.|
|5312|The message segment specified in the network control block (NCB) is<br>illogical.  The NCB is the data.|
|5313|The name already exists in the local adapter name table.<br>The network control block (NCB) request was refused.  The NCB is the data.|
|5314|The network adapter name table is full.<br>The network control block (NCB) request was refused.  The NCB is the data.|
|5315|The network name has active sessions and is now de-registered.<br>The network control block (NCB) command completed.  The NCB is the data.|
|5316|A previously issued Receive Lookahead command is active<br>for this session.  The network control block (NCB) command was rejected.<br>The NCB is the data.|
|5317|The local session table is full. The network control block (NCB) request was refused.<br>The NCB is the data.|
|5318|A network control block (NCB) session open was rejected.  No LISTEN is outstanding<br>on the remote computer.  The NCB is the data.|
|5319|The name number specified in the network control block (NCB) is illegal.<br>The NCB is the data.|
|5320|The call name specified in the network control block (NCB) cannot be found or<br>did not answer.  The NCB is the data.|
|5321|The name specified in the network control block (NCB) was not found.  Cannot put '*' or<br>00h in the NCB name.  The NCB is the data.|
|5322|The name specified in the network control block (NCB) is in use on a remote adapter.<br>The NCB is the data.|
|5323|The name specified in the network control block (NCB) has been deleted.<br>The NCB is the data.|
|5324|The session specified in the network control block (NCB) ended abnormally.<br>The NCB is the data.|
|5325|The network protocol has detected two or more identical<br>names on the network.	The network control block (NCB) is the data.|
|5326|An unexpected protocol packet was received.  There may be an<br>incompatible remote device.  The network control block (NCB) is the data.|
|5333|The NetBIOS interface is busy.<br>The network control block (NCB) request was refused.  The NCB is the data.|
|5334|There are too many network control block (NCB) commands outstanding.<br>The NCB request was refused.  The NCB is the data.|
|5335|The adapter number specified in the network control block (NCB) is illegal.<br>The NCB is the data.|
|5336|The network control block (NCB) command completed while a cancel was occurring.<br>The NCB is the data.|
|5337|The name specified in the network control block (NCB) is reserved.<br>The NCB is the data.|
|5338|The network control block (NCB) command is not valid to cancel.<br>The NCB is the data.|
|5351|There are multiple network control block (NCB) requests for the same session.<br>The NCB request was refused.  The NCB is the data.|
|5352|There has been a network adapter error. The only NetBIOS<br>command that may be issued is an NCB RESET. The network control block (NCB) is<br>the data.|
|5354|The maximum number of applications was exceeded.<br>The network control block (NCB) request was refused.  The NCB is the data.|
|5356|The requested resources are not available.<br>The network control block (NCB) request was refused.  The NCB is the data.|
|5364|A system error has occurred.<br>The network control block (NCB) request was refused.  The NCB is the data.|
|5365|A ROM checksum failure has occurred.<br>The network control block (NCB) request was refused.  The NCB is the data.|
|5366|A RAM test failure has occurred.<br>The network control block (NCB) request was refused.  The NCB is the data.|
|5367|A digital loopback failure has occurred.<br>The network control block (NCB) request was refused.  The NCB is the data.|
|5368|An analog loopback failure has occurred.<br>The network control block (NCB) request was refused.  The NCB is the data.|
|5369|An interface failure has occurred.<br>The network control block (NCB) request was refused.  The NCB is the data.|
|5370|An unrecognized network control block (NCB) return code was received.<br>The NCB is the data.|
|5380|A network adapter malfunction has occurred.<br>The network control block (NCB) request was refused.  The NCB is the data.|
|5381|The network control block (NCB) command is still pending.<br>The NCB is the data.|
|5500|The update log on %1 is over 80%% capacity. The primary<br>domain controller %2 is not retrieving the updates.|
|5501|The update log on %1 is full, and no further updates<br>can be added until the primary domain controller %2<br>retrieves the updates.|
|5502|The time difference with the primary domain controller %1<br>exceeds the maximum allowed skew of %2 seconds.|
|5503|The account of user %1 has been locked out on %2<br>due to %3 bad password attempts.|
|5504|The %1 log file cannot be opened.|
|5505|The %1 log file is corrupted and will be cleared.|
|5506|The Application log file could not be opened.  %1 will be used as the<br>default log file.|
|5507|The %1 Log is full.  If this is the first time you have seen this<br>message, take the following steps:<br><br>1. Click Start, click Run, type "eventvwr", and then click OK.<br><br>2. Click %1, click the Action menu, click Clear All Events, and then click No.<br><br><br>If this dialog reappears, contact your helpdesk or system administrator.|
|5508|The security database full synchronization has been initiated by the server %1.|
|5509|Windows could not be started as configured.<br>A previous working configuration was used instead.|
|5510|The exception 0x%1 occurred in the application %2 at location 0x%3.|
|5511|The servers %1 and  %3 both claim to be an NT Domain Controller for<br>the %2 domain. One of the servers should be removed from the<br>domain because the servers have different security identifiers<br>(SID).|
|5512|The server %1 and %2 both claim to be the primary domain<br>controller for the %3 domain. One of the servers should be<br>demoted or removed from the domain.|
|5513|The computer %1 tried to connect to the server %2 using<br>the trust relationship established by the %3 domain. However, the<br>computer lost the correct security identifier (SID)<br>when the domain was reconfigured. Reestablish the trust<br>relationship.|
|5514|The computer has rebooted from a bugcheck.  The bugcheck was:<br>%1.<br>%2<br>A full dump was not saved.|
|5515|The computer has rebooted from a bugcheck.  The bugcheck was:<br>%1.<br>%2<br>A dump was saved in: %3.|
|5516|The computer or domain %1 trusts domain %2.  (This may be an indirect<br>trust.)  However, %1 and %2 have the same machine security identifier<br>(SID).  NT should be re-installed on either %1 or %2.|
|5517|The computer or domain %1 trusts domain %2.  (This may be an indirect<br>trust.)  However, %2 is not a valid name for a trusted domain.<br>The name of the trusted domain should be changed to a valid name.|
|5600|Could not share the User or Script path.|
|5601|The password for this computer is not found in the local security<br>database.|
|5602|An internal error occurred while accessing the computer's<br>local or network security database.|
|5700|The Netlogon service could not initialize the replication data<br>structures successfully. The service was terminated.  The following<br>error occurred: <br>%1|
|5701|The Netlogon service failed to update the domain trust list.  The<br>following error occurred: <br>%1|
|5702|The Netlogon service could not add the RPC interface.  The<br>service was terminated. The following error occurred: <br>%1|
|5703|The Netlogon service could not read a mailslot message from %1 due<br>to the following error: <br>%2|
|5704|The Netlogon service failed to register the service with the<br>service controller. The service was terminated. The following<br>error occurred: <br>%1|
|5705|The change log cache maintained by the Netlogon service for %1<br>database changes is inconsistent. The Netlogon service is resetting<br>the change log.|
|5706|The Netlogon service could not create server share %1.  The following<br>error occurred: <br>%2|
|5707|The down-level logon request for the user %1 from %2 failed.|
|5708|The down-level logoff request for the user %1 from %2 failed.|
|5709|The Windows NT or Windows 2000 %1 logon request for the user %2\%3 from %4 (via %5)<br>failed.|
|5710|The Windows NT or Windows 2000 %1 logoff request for the user %2\%3 from %4<br>failed.|
|5711|The partial synchronization request from the server %1 completed<br>successfully. %2 changes(s) has(have) been returned to the<br>caller.|
|5712|The partial synchronization request from the server %1 failed with<br>the following error: <br>%2|
|5713|The full synchronization request from the server %1 completed<br>successfully. %2 object(s) has(have) been returned to<br>the caller.|
|5714|The full synchronization request from the server %1 failed with<br>the following error: <br>%2|
|5715|The partial synchronization replication of the %1 database from the<br>primary domain controller %2 completed successfully. %3 change(s) is(are)<br>applied to the database.|
|5716|The partial synchronization replication of the %1 database from the<br>primary domain controller %2 failed with the following error: <br>%3|
|5717|The full synchronization replication of the %1 database from the<br>primary domain controller %2 completed successfully.|
|5718|The full synchronization replication of the %1 database from the<br>primary domain controller %2 failed with the following error: <br>%3|
|5719|This computer was not able to set up a secure session with a domain<br>controller in domain %1 due to the following: <br>%2<br><br>This may lead to authentication problems. Make sure that this<br>computer is connected to the network. If the problem persists,<br>please contact your domain administrator.<br><br><br><br>ADDITIONAL INFO<br><br>If this computer is a domain controller for the specified domain, it<br>sets up the secure session to the primary domain controller emulator in the specified<br>domain. Otherwise, this computer sets up the secure session to any domain controller<br>in the specified domain.|
|5720|The session setup to the Windows Domain Controller %1 for the domain %2<br>failed because the computer %3 does not have a local security database account.|
|5721|The session setup to the Windows Domain Controller %1 for the domain %2<br>failed because the Domain Controller did not have an account %4<br>needed to set up the session by this computer %3.<br><br><br><br>ADDITIONAL DATA<br><br>If this computer is a member of or a Domain Controller in the specified domain, the<br>aforementioned account is a computer account for this computer in the specified domain.<br>Otherwise, the account is an interdomain trust account with the specified domain.|
|5722|The session setup from the computer %1 failed to authenticate.<br>The name(s) of the account(s) referenced in the security database is<br>%2.  The following error occurred: <br>%3|
|5723|The session setup from computer '%1' failed because the security database<br>does not contain a trust account '%2' referenced by the specified computer.<br><br><br><br>USER ACTION<br><br><br>If this is the first occurrence of this event for the specified computer<br>and account, this may be a transient issue that doesn't require any action<br>at this time.<br><br>If this is a Read-Only Domain Controller and '%2' is a legitimate machine<br>account for the computer '%1' then '%1' should be marked cacheable for this<br>location if appropriate or otherwise ensure connectivity to a domain controller<br>capable of servicing the request (for example a writable domain controller).<br><br>Otherwise, the following steps may be taken to resolve this problem:<br><br><br><br>If '%2' is a legitimate machine account for the computer '%1', then '%1'<br>should be rejoined to the domain.<br><br><br><br>If '%2' is a legitimate interdomain trust account, then the trust should<br>be recreated.<br><br><br><br>Otherwise, assuming that '%2' is not a legitimate account, the following<br>action should be taken on '%1':<br><br><br><br>If '%1' is a Domain Controller, then the trust associated with '%2' should be deleted.<br><br><br><br>If '%1' is not a Domain Controller, it should be disjoined from the domain.|
|5724|Could not register control handler with service controller %1.|
|5725|Could not set service status with service controller %1.|
|5726|Could not find the computer name %1.|
|5727|Could not load %1 device driver.|
|5728|Could not load any transport.|
|5729|Replication of the %1 Domain Object "%2" from primary domain controller<br>%3 failed with the following error: <br>%4|
|5730|Replication of the %1 Global Group "%2" from primary domain controller<br>%3 failed with the following error: <br>%4|
|5731|Replication of the %1 Local Group "%2" from primary domain controller<br>%3 failed with the following error: <br>%4|
|5732|Replication of the %1 User "%2" from primary domain controller<br>%3 failed with the following error: <br>%4|
|5733|Replication of the %1 Policy Object "%2" from primary domain controller<br>%3 failed with the following error: <br>%4|
|5734|Replication of the %1 Trusted Domain Object "%2" from primary domain controller<br>%3 failed with the following error: <br>%4|
|5735|Replication of the %1 Account Object "%2" from primary domain controller<br>%3 failed with the following error: <br>%4|
|5736|Replication of the %1 Secret "%2" from primary domain controller<br>%3 failed with the following error: <br>%4|
|5737|The system returned the following unexpected error code: <br>%1|
|5738|Netlogon has detected two machine accounts for server "%1".<br>The server can be either a Windows 2000 Server that is a member of the<br>domain or the server can be a LAN Manager server with an account in the<br>SERVERS global group.  It cannot be both.|
|5739|This domain has more global groups than can be replicated to a LanMan<br>BDC.  Either delete some of your global groups or remove the LanMan<br>BDCs from the domain.|
|5740|The Browser driver returned the following error to Netlogon: <br>%1|
|5741|Netlogon could not register the %1<1B> name for the following reason: <br>%2|
|5742|Service failed to retrieve messages needed to boot remote boot clients.|
|5743|Service experienced a severe error and can no longer provide remote boot<br>for 3Com 3Start remote boot clients.|
|5744|Service experienced a severe system error and will shut itself down.|
|5745|Client with computer name %1 failed to acknowledge receipt of the<br>boot data.  Remote boot of this client was not completed.|
|5746|Client with computer name %1 was not booted due to an error in opening<br>file %2.|
|5747|Client with computer name %1 was not booted due to an error in reading<br>file %2.|
|5748|Client with computer name %1 was not booted due to insufficient memory<br>at the remote boot server.|
|5749|Client with computer name %1 will be booted without using checksums<br>because checksum for file %2 could not be calculated.|
|5750|Client with computer name %1 was not booted due to too many lines in<br>file %2.|
|5751|Client with computer name %1 was not booted because the boot block<br>configuration file %2 for this client does not contain boot block<br>line and/or loader line.|
|5752|Client with computer name %1 was not booted due to a bad size of<br>file %2.|
|5753|Client with computer name %1 was not booted due to remote boot<br>service internal error.|
|5754|Client with computer name %1 was not booted because file %2 has an<br>invalid boot header.|
|5755|Client with computer name %1 was not booted due to network error.|
|5756|Client with adapter id %1 was not booted due to lack of resources.|
|5757|Service experienced error copying file or directory %1.|
|5758|Service experienced error deleting file or directory %1.|
|5759|Service experienced error setting permissions on file or directory %1.|
|5760|Service experienced error evaluating RPL configurations.|
|5761|Service experienced error creating RPL profiles for all configurations.|
|5762|Service experienced error accessing registry.|
|5763|Service experienced error replacing possibly outdated RPLDISK.SYS.|
|5764|Service experienced error adding security accounts or setting<br>file permissions.  These accounts are the RPLUSER local group<br>and the user accounts for the individual RPL workstations.|
|5765|Service failed to back up its database.|
|5766|Service failed to initialize from its database.  The database may be<br>missing or corrupted.  Service will attempt restoring the database<br>from the backup.|
|5767|Service failed to restore its database from the backup.  Service<br>will not start.|
|5768|Service successfully restored its database from the backup.|
|5769|Service failed to initialize from its restored database.  Service<br>will not start.|
|5770|The session setup to the Windows Domain Controller %1 from computer<br>%2 using account %4 failed.  %2 is declared to be a BDC in domain %3.<br>However, %2 tried to connect as either a DC in a trusted domain,<br>a member workstation in domain %3, or as a server in domain %3.<br>Use the Active Directory Users and Computers tool or Server Manager to remove the BDC account for %2.|
|5771|The Remoteboot database was in NT 3.5 / NT 3.51 format and NT is<br>attempting to convert it to NT 4.0 format. The JETCONV converter<br>will write to the Application event log when it is finished.|
|5772|Global group SERVERS exists in domain %1 and has members.<br>This group defines Lan Manager BDCs in the domain.<br>Lan Manager BDCs are not permitted in NT domains.|
|5773|The following DNS server that is authoritative for the DNS domain controller<br>locator records of this domain controller does not support dynamic DNS updates:<br><br><br><br>DNS server IP address: %1<br><br>Returned Response Code (RCODE): %2<br><br>Returned Status Code: %3<br><br><br><br>USER ACTION<br><br><br>Configure the DNS server to allow dynamic DNS updates or manually add the DNS<br>records from the file '%SystemRoot%\System32\Config\Netlogon.dns' to the DNS database.|
|5774|The dynamic registration of the DNS record '%1' failed on the following DNS server:<br><br><br><br>DNS server IP address: %3<br><br>Returned Response Code (RCODE): %4<br><br>Returned Status Code: %5<br><br><br><br>For computers and users to locate this domain controller, this record must be<br>registered in DNS.<br><br><br><br>USER ACTION<br><br><br>Determine what might have caused this failure, resolve the problem, and initiate<br>registration of the DNS records by the domain controller. To determine what might<br>have caused this failure, run DCDiag.exe. To learn more about DCDiag.exe, see Help<br>and Support Center. To initiate registration of the DNS records by this domain<br>controller, run 'nltest.exe /dsregdns' from the command prompt on the domain controller<br>or restart Net Logon service. <br>  Or, you can manually add this record to DNS, but it<br>is not recommended.<br><br><br><br>ADDITIONAL DATA<br><br>Error Value: %2|
|5775|The dynamic deletion of the DNS record '%1' failed on the following DNS server:<br><br><br><br>DNS server IP address: %3<br><br>Returned Response Code (RCODE): %4<br><br>Returned Status Code: %5<br><br><br><br>USER ACTION<br><br><br>To prevent remote computers from connecting unnecessarily to the domain controller,<br>delete the record manually or troubleshoot the failure to dynamically delete the<br>record. To learn more about debugging DNS, see Help and Support Center.<br><br><br><br>ADDITIONAL DATA<br><br>Error Value: %2|
|5776|Failed to create/open file %1 with the following error: <br>%2|
|5777|Netlogon got the following error while trying to get the subnet to site<br>mapping information from the DS: <br>%1|
|5778|'%1' tried to determine its site by looking up its IP address ('%2')<br>in the Configuration\Sites\Subnets container in the DS.  No subnet matched<br>the IP address.  Consider adding a subnet object for this IP address.|
|5779|The site name for this computer is '%1'.  That site name is not a valid<br>site name.  A site name must be a valid DNS label.<br>Rename the site to be a valid name.|
|5780|The subnet object '%1' appears in the Configuration\Sites\Subnets<br>container in the DS.  The name is not syntactically valid.  The valid<br>syntax is xx.xx.xx.xx/yy where xx.xx.xx.xx is a valid IP subnet number<br>and yy is the number of bits in the subnet mask.<br><br>Correct the name of the subnet object.|
|5781|Dynamic registration or deletion of one or more DNS records associated with DNS<br>domain '%1' failed.  These records are used by other computers to locate this<br>server as a domain controller (if the specified domain is an Active Directory<br>domain) or as an LDAP server (if the specified domain is an application partition).<br><br><br><br>Possible causes of failure include:<br><br><br>- TCP/IP properties of the network connections of this computer contain wrong IP address(es) of the preferred and alternate DNS servers<br><br>- Specified preferred and alternate DNS servers are not running<br><br>- DNS server(s) primary for the records to be registered is not running<br><br>- Preferred or alternate DNS servers are configured with wrong root hints<br><br>- Parent DNS zone contains incorrect delegation to the child zone authoritative for the DNS records that failed registration<br><br><br><br>USER ACTION<br><br><br>Fix possible misconfiguration(s) specified above and initiate registration or deletion of<br>the DNS records by running 'nltest.exe /dsregdns' from the command prompt on the domain<br>controller or by restarting Net Logon service on the domain controller.|
|5782|Dynamic registration or deregistration of one or more DNS records failed with the following error: <br>%1|
|5783|The session setup to the Windows Domain Controller %1 for the domain %2<br>is not responsive.  The current RPC call from Netlogon on \\%3 to %1 has been cancelled.|
|5784|Site '%2' does not have any Domain Controllers for domain '%3'.<br>Domain Controllers in site '%1' have been automatically<br>selected to cover site '%2' for domain '%3' based on configured<br>Directory Server replication costs.|
|5785|This Domain Controller no longer automatically covers site '%1' for domain '%2'.|
|5786|Site '%2' does not have any Global Catalog servers for forest '%3'.<br>Global Catalog servers in site '%1' have been automatically<br>selected to cover site '%2' for forest '%3' based on configured<br>Directory Server replication costs.|
|5787|This Global Catalog server no longer automatically covers site '%1' for forest '%2'.|
|5788|Attempt to update HOST Service Principal Names (SPNs) of the computer<br>object in Active Directory failed. The updated values were '%1' and '%2'.<br>The following error occurred: <br>%3|
|5789|Attempt to update DNS Host Name of the computer object<br>in Active Directory failed. The updated value was '%1'.<br>The following error occurred: <br>%2|
|5790|No suitable Domain Controller is available for domain %1.<br>An NT4 or older domain controller is available but it cannot<br>be used for authentication purposes in the Windows 2000 or newer<br>domain that this computer is a member of.<br>The following error occurred:<br>%2|
|5791|The domain of this computer, %1 has been downgraded from Windows 2000<br>or newer to Windows NT4 or older. The computer cannot function properly<br>in this case for authentication purposes. This computer needs to rejoin<br>the domain.<br>The following error occurred:<br>%2|
|5792|Site '%2' does not have any LDAP servers for non-domain NC '%3'.<br>LDAP servers in site '%1' have been automatically selected to<br>cover site '%2' for non-domain NC '%3' based on configured<br>Directory Server replication costs.|
|5793|This LDAP server no longer automatically covers site '%1' for non-domain NC '%2'.|
|5794|Site '%2' is no longer manually configured in the registry as<br>covered by this Domain Controller for domain '%3'. As a result,<br>site '%2' does not have any Domain Controllers for domain '%3'.<br>Domain Controllers in site '%1' have been automatically<br>selected to cover site '%2' for domain '%3' based on configured<br>Directory Server replication costs.|
|5795|This Domain Controller no longer automatically covers site '%1' for domain '%2'.<br>However, site '%1' is still (manually) covered by this Domain Controller for<br>domain '%2' since this site has been manually configured in the registry.|
|5796|Site '%2' is no longer manually configured in the registry as<br>covered by this Global Catalog server for forest '%3'. As a result,<br>site '%2' does not have any Global Catalog servers for forest '%3'.<br>Global Catalog servers in site '%1' have been automatically<br>selected to cover site '%2' for forest '%3' based on configured<br>Directory Server replication costs.|
|5797|This Global Catalog server no longer automatically covers site '%1' for forest '%2'.<br>However, site '%1' is still (manually) covered by this Global catalog for<br>forest '%2' since this site has been manually configured in the registry.|
|5798|Site '%2' is no longer manually configured in the registry as<br>covered by this LDAP server for non-domain NC '%3'. As a result,<br>site '%2' does not have any LDAP servers for non-domain NC '%3'.<br>LDAP servers in site '%1' have been automatically<br>selected to cover site '%2' for non-domain NC '%3' based on<br>configured Directory Server replication costs.|
|5799|This LDAP server no longer automatically covers site '%1' for non-domain NC '%2'.<br>However, site '%1' is still (manually) covered by this LDAP server for<br>non-domain NC '%2' since this site has been manually configured in the registry.|
|5800|Attempt to update DnsHostName and HOST Service Principal Name (SPN) attributes<br>of the computer object in Active Directory failed because the Domain Controller<br>'%1' had more than one account with the name '%2' corresponding to this computer.<br>Not having SPNs registered may result in authentication failures for this computer.<br>Contact your domain administrator who may need to manually resolve the account name<br>collision.|
|5801|Attempt to update DnsHostName and HOST Service Principal Name (SPN) attributes<br>of the computer object in Active Directory failed because this computer account<br>name, '%2' could not be mapped to the computer object on Domain Controller '%1'.<br>Not having SPNs registered may result in authentication failures for this computer.<br>Contact your domain administrator. The following technical information may be<br>useful for the resolution of this failure:<br><br>DsCrackNames status = 0x%3, crack error = 0x%4.|
|5802|None of the IP addresses (%2) of this Domain Controller map to the configured site '%1'.<br>While this may be a temporary situation due to IP address changes, it is generally<br>recommended that the IP address of the Domain Controller (accessible to machines in<br>its domain) maps to the Site which it services. If the above list of IP addresses is<br>stable, consider moving this server to a site (or create one if it does not already<br>exist) such that the above IP address maps to the selected site. This may require the<br>creation of a new subnet object (whose range includes the above IP address) which maps<br>to the selected site object.|
|5803|The following error occurred while reading a parameter '%2' in the<br>Netlogon %1 registry section:<br>%3|
|5804|The Netlogon %1 registry key contains an invalid value 0x%2 for parameter '%3'.<br>The minimum and maximum values allowed for this parameter are 0x%4 and 0x%5, respectively.<br>The value of 0x%6 has been assigned to this parameter.|
|5805|The session setup from the computer %1 failed to authenticate.<br>The following error occurred: <br>%2|
|5806|Dynamic DNS updates have been manually disabled on this domain controller.<br><br><br><br>USER ACTION<br><br><br>Reconfigure this domain controller to use dynamic DNS updates or manually add the DNS<br>records from the file '%SystemRoot%\System32\Config\Netlogon.dns' to the DNS database.|
|5807|During the past %1 hours there have been %2 connections to this Domain<br>Controller from client machines whose IP addresses don't map to any of<br>the existing sites in the enterprise. Those clients, therefore, have<br>undefined sites and may connect to any Domain Controller including<br>those that are in far distant locations from the clients. A client's site<br>is determined by the mapping of its subnet to one of the existing sites.<br>To move the above clients to one of the sites, please consider creating<br>subnet object(s) covering the above IP addresses with mapping to one of the<br>existing sites.  The names and IP addresses of the clients in question have<br>been logged on this computer in the following log file<br>'%SystemRoot%\debug\netlogon.log' and, potentially, in the log file<br>'%SystemRoot%\debug\netlogon.bak' created if the former log becomes full.<br>The log(s) may contain additional unrelated debugging information. To filter<br>out the needed information, please search for lines which contain text<br>'NO_CLIENT_SITE:'. The first word after this string is the client name and<br>the second word is the client IP address. The maximum size of the log(s) is<br>controlled by the following registry DWORD value<br>'HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Netlogon\Parameters\LogFileMaxSize';<br>the default is %3 bytes.  The current maximum size is %4 bytes.  To set a<br>different maximum size, create the above registry value and set the desired<br>maximum size in bytes.|
|5808|The deregistration of some DNS domain controller locator records was aborted<br>at the time of this domain controller demotion because the DNS deregistrations<br>took too long.<br><br><br><br>USER ACTION<br><br><br>Manually delete the DNS records listed in the file<br>'%SystemRoot%\System32\Config\Netlogon.dns' from the DNS database.|
|5809|The NetLogon service on this domain controller has been configured to use port %1<br>for incoming RPC connections over TCP/IP from remote machines. However, the<br>following error occurred when Netlogon attempted to register this port with the RPC<br>endpoint mapper service: <br>%2 <br>This will prevent the NetLogon service on remote<br>machines from connecting to this domain controller over TCP/IP that may result in<br>authentication problems.<br><br><br><br>USER ACTION<br><br><br>The specified port is configured via the Group Policy or via a registry value 'DcTcpipPort'<br>under the 'HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Netlogon\Parameters'<br>registry key; the value configured through the Group Policy takes precedence. If the<br>port specified is in error, reset it to a correct value. You can also remove this<br>configuration for the port in which case the port will be assigned dynamically by<br>the endpoint mapper at the time the NetLogon service on remote machines makes RPC connections<br>to this domain controller. After the misconfiguration is corrected, restart the NetLogon<br>service on this machine and verify that this event log no longer appears.|
|5810|During the past %1 hours, this domain controller has received %2 connections<br>from dual-stack IPv4/IPv6 clients with partial subnet-site mappings. A client<br>has a partial subnet-site mapping if its IPv4 address is mapped to a site but<br>its global IPv6 address is not mapped to a site, or vice versa. To ensure correct<br>behavior for applications running on member computers and servers that rely on<br>subnet-site mappings, dual-stack IPv4/IPv6 clients must have both IPv4 and global<br>IPv6 addresses mapped to the same site. If a partially mapped client attempts<br>to connect to this domain controller using its unmapped IP address, its mapped<br>address is used for the client's site mapping.<br><br><br><br>The log files %SystemRoot%\debug\netlogon.log or %SystemRoot%\debug\netlogon.bak<br>contain the name, unmapped IP address and mapped IP address for each partially<br>mapped client. The log files may also contain unrelated debugging information.<br>To locate the information pertaining to partial-subnet mappings, search for<br>lines that contain the text 'PARTIAL_CLIENT_SITE_MAPPING:'. The first word after<br>this text is the client name. Following the client name is the client's unmapped<br>IP address (the IP address that does not have a subnet-site mapping) and the<br>client's mapped IP address, which was used to return site information.<br><br><br><br>USER ACTION<br><br><br>Use the Active Directory Sites and Services management console (MMC) snap-in<br>to add the subnet mapping for the unmapped IP addresses to the same site being<br>used by the mapped IP addresses. When adding site mappings for IPv6 addresses,<br>you should use global IPv6 addresses and not for instance temporary, link-local<br>or site-local IPv6 addresses.<br><br><br><br>The default maximum size of the log files is %3 bytes. The current maximum<br>size is %4 bytes. To set a different maximum size, create the following registry<br>DWORD value to specify the maximum size in bytes:<br><br><br>HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Netlogon\Parameters\LogFileMaxSize|
|5811|The dynamic registration of the DNS record '%1' for the remote domain controller '%3'<br>failed on the following DNS server:<br><br><br><br>DNS server IP address: %4<br><br>Returned Response Code (RCODE): %5<br><br>Returned Status Code: %6<br><br><br><br>For computers and users to locate the domain controller '%3', this record must be<br>registered in DNS.<br><br><br><br>USER ACTION<br><br><br>Determine what might have caused this failure, resolve the problem, and initiate<br>registration of the DNS records by the domain controller '%3'. For help with determining<br>and resolving the problem, see Help and Support for information about troubleshooting<br>DNS. To initiate registration of the DNS records by the domain controller '%3', run<br>'nltest.exe /dsregdns' from the command prompt on the domain controller '%3' or restart<br>the Net Logon service on the domain controller '%3'. Nltest.exe is a command line tool<br>that is built into Windows Server.<br><br> As a workaround, you can manually add this record to DNS, but it is not recommended<br>because you then must manually update any changes it requires hereafter.<br><br><br><br>ADDITIONAL DATA<br><br>Error Value: %2|
|5812|The dynamic deregistration of the DNS record '%1' for the remote domain controller<br>'%3' failed on the following DNS server:<br><br><br><br>DNS server IP address: %4<br><br>Returned Response Code (RCODE): %5<br><br>Returned Status Code: %6<br><br><br><br>USER ACTION<br><br><br>To prevent remote computers from attempting to connect to the domain controller '%3'<br>using an invalid record, delete the record '%1' manually or troubleshoot the root cause<br>behind the dynamic deregistration failure. To learn more about troubleshooting DNS, see<br>Help and Support.<br><br><br><br>ADDITIONAL DATA<br><br>Error Value: %2|
|5813|The dynamic registration request for the DNS record '%1' has been rejected by the<br>remote domain controller '%2'. Error: '%3'<br><br><br><br>For computers and users to locate this domain controller, this record must be<br>registered in DNS. If the problem persists, please contact your domain administrator.|
|5814|The dynamic deregistration request of the DNS record '%1' has been rejected by the<br>remote domain controller '%2'. Error: '%3'<br><br><br><br>To prevent remote computers from connecting unnecessarily to this domain controller,<br>an administrator with sufficient privileges must manually delete the record on the DNS<br>server that hosts it.|
|5815|The remoting of the dynamic update request for the local domain controller's DNS records<br>through a secure session has failed with error '%1'.<br><br><br><br>For other computers and member servers to locate this domain controller, the appropriate<br>records must be registered in DNS. On this domain controller, look for events related to<br>failure to set up a secure session to determine why the request is failing. If the problem<br>persists, please contact your domain administrator.|
|5816|Netlogon has failed an authentication request of account %1 in domain %2. The request timed out before it<br>could be sent to domain controller %3 in domain %4. This is the first failure. If the problem continues,<br>consolidated events will be logged about every %5 minutes.<br>Please see http://support.microsoft.com/kb/2654097 for more information.|
|5817|Netlogon has failed an additional %1 authentication requests in the last %2 minutes.<br>The requests timed out before they could be sent to domain controller %3 in domain %4.<br>Please see http://support.microsoft.com/kb/2654097 for more information.|
|5818|Netlogon took more than %1 seconds for an authentication request of account %2 in domain %3, through<br>domain controller %4 in domain %5. This is the first warning. If the problem persists, a recurring event will be logged<br>every %6 minutes.<br>Please see http://support.microsoft.com/kb/2654097 for more information on this error.|
|5819|Netlogon took more than %1 seconds for %2 authentication requests through domain controller %3 in domain %4 in the last %5 minutes.<br>Please see http://support.microsoft.com/kb/2654097 for more information.|
|5820|The Netlogon service could not add the AuthZ RPC interface.  The<br>service was terminated. The following error occurred: '%1'|
|5821|The Netlogon service failed to initialize the AuthZ resource manager.<br>The service was terminated. The following error occurred: '%1'.|
|5822|The Netlogon service failed to initialize the security descriptor<br>for the Netlogon RPC interface.   The service was terminated. The<br>following error occurred: '%1'.|
|5823|The system successfully changed its password on the domain controller %1.<br><br>This event is logged when the password for the computer account is<br>changed by the system. It is logged on the computer that changed the<br>password.|
|5824|The system successfully changed the password for managed service account %1<br>on the domain controller %2.<br><br>This event is logged when the password for a standalone managed service<br>account is changed by the system. It is logged on the computer that<br>changed the password.|
|5825|The system failed to lowercase the currently configured host name. This<br>conversion failed with the error code below. This may affect the system's<br>ability to register SRV records, potentially affecting clients' ability<br>to locate domain controllers.<br><br>Error code: %1<br><br>More information is available at https://aka.ms/lowercasehostnamesrvrecord|
|5826|The Netlogon service detected a non-windows account using secure RPC.<br><br><br><br> Machine SamAccountName: %1<br><br> Domain: %2<br><br> Account Type: %3<br><br> Machine Os: %4<br><br> Machine Os Build Version: %5<br><br> Machine Os Service Pack: %6|
|5827|The Netlogon service denied a vulnerable Netlogon secure channel connection from a machine account.<br><br><br><br> Machine SamAccountName: %1<br><br> Domain: %2<br><br> Account Type: %3<br><br> Machine Operating System: %4<br><br> Machine Operating System Build: %5<br><br> Machine Operating System Service Pack: %6<br><br><br><br>For more information about why this was denied, please visit  https://go.microsoft.com/fwlink/?linkid=2133485.|
|5828|The Netlogon service denied a vulnerable Netlogon secure channel connection using a trust account.<br><br><br><br> Account Type: %1<br><br> Trust Name: %2<br><br> Trust Target: %3<br><br> Client IP Address: %4<br><br><br><br>For more information about why this was denied, please visit  https://go.microsoft.com/fwlink/?linkid=2133485.|
|5829|The Netlogon service allowed a vulnerable Netlogon secure channel connection.<br><br><br><br>Warning: This connection will be denied once the enforcement phase is released. To better understand the enforcement phase,<br>please visit  https://go.microsoft.com/fwlink/?linkid=2133485.<br><br><br><br> Machine SamAccountName: %1<br><br> Domain: %2<br><br> Account Type: %3<br><br> Machine Operating System: %4<br><br> Machine Operating System Build: %5<br><br> Machine Operating System Service Pack: %6<br>|
|5830|The Netlogon service allowed a vulnerable Netlogon secure channel connection because the machine account is allowed in the<br>"Domain controller: Allow vulnerable Netlogon secure channel connections" group policy.<br><br><br><br>Warning: Using vulnerable Netlogon secure channels will expose the domain-joined devices to attack. To protect your device from attack,<br>remove a machine account from "Domain controller: Allow vulnerable Netlogon secure channel connections" group policy after the third-party<br>Netlogon client has been updated. To better understand the risk of configuring machine accounts to be allowed to use vulnerable Netlogon<br>secure channel connections, please visit  https://go.microsoft.com/fwlink/?linkid=2133485.<br><br><br><br> Machine SamAccountName: %1<br><br> Domain: %2<br><br> Account Type: %3<br><br> Machine Os: %4<br><br> Machine Os Build Version: %5<br><br> Machine Os Service Pack: %6|
|5831|The Netlogon service allowed a vulnerable Netlogon secure channel connection because the trust account is allowed in the<br>"Domain controller: Allow vulnerable Netlogon secure channel connections" group policy.<br><br><br><br>Warning: Using vulnerable Netlogon secure channels will expose Active Directory forests to attack. To protect your<br>Active Directory forests from attack, all trusts must use secure RPC with Netlogon secure channel. Remove a trust account from<br>"Domain controller: Allow vulnerable Netlogon secure channel connections" group policy after the third-party Netlogon client on the domain controllers<br>have been updated. To better understand the risk of configuring trust accounts to be allowed to use vulnerable Netlogon secure channel connections,<br>please visit  https://go.microsoft.com/fwlink/?linkid=2133485.<br><br><br><br> Account Type: %1<br><br> Trust Name: %2<br><br> Trust Target: %3<br><br> Client IP Address: %4|
|5832|The Netlogon service allowed one or more unsecure pass-through NTLM authentication requests from trusted domains and/or forests<br>during the most recent event throttling window. These unsecure requests would normally be blocked but were allowed to proceed<br>due to the current trust configuration.<br><br><br><br><br><br>Warning: Allowing unsecure pass-through authentication requests will expose your Active Directory forest to attack.<br>For more information about this issue please visit https://go.microsoft.com/fwlink/?linkid=276811&.<br><br><br><br><br><br>Count of unsecure requests allowed due to administrative override: %1<br>|
|5833|The Netlogon service blocked one or more unsecure pass-through NTLM authentication requests from trusted clients, domains,<br>and/or forests during the most recent event throttling window. For more information about this issue, including how to enable<br>more verbose logging, please visit https://go.microsoft.com/fwlink/?linkid=276811&.<br><br><br><br><br><br>Count of unsecure requests blocked: %1<br>|
|5834|The Netlogon service allowed an unsecure pass-through NTLM authentication request from a trusted client, domain,<br>or forest. This unsecure request would normally be blocked but was allowed to proceed due to the current trust<br>configuration.<br><br><br><br><br><br>Warning: Allowing unsecure pass-through authentication requests will expose your Active Directory forest to attack.<br>For more information about this issue please visit https://go.microsoft.com/fwlink/?linkid=276811&.<br><br><br><br><br><br>Account name: %1<br><br>Trust name: %2<br><br>Trust type: %3<br><br>Client IP Address: %4<br><br>Block reason: %5<br><br>Resource server Netbios name: %6<br><br>Resource server DNS name: %7<br><br>Resource domain Netbios name: %8<br><br>Resource domain DNS name: %9<br>|
|5835|The Netlogon service blocked an unsecure pass-through NTLM authentication requests from a trusted client, domain,<br>or forest. For more information, please visit https://go.microsoft.com/fwlink/?linkid=276811&.<br><br><br><br><br><br>Account name: %1<br><br>Trust name: %2<br><br>Trust type: %3<br><br>Client IP Address: %4<br><br>Block reason: %5<br><br>Resource server Netbios name: %6<br><br>Resource server DNS name: %7<br><br>Resource domain Netbios name: %8<br><br>Resource domain DNS name: %9<br>|
|5836|The Netlogon service was able to bind to a TCP/IP port with the configured backlog size of %1.|
|5837|The Netlogon service tried to bind to a TCP/IP port with the configured backlog size of %1 but failed. <br><br><br><br>More information can be found in the following log file '%SystemRoot%\debug\netlogon.log' and, potentially, in the log file<br>'%SystemRoot%\debug\netlogon.bak' created if the former log becomes full. For steps in enabling the log, please visit<br>https://go.microsoft.com/fwlink/?linkid=2163327|
|5838|The Netlogon service encountered a client using RPC signing instead of RPC sealing.<br><br><br><br> Machine SamAccountName: %1<br><br> Domain: %2<br><br> Account Type: %3<br><br> Machine Operating System: %4<br><br> Machine Operating System Build: %5<br><br> Machine Operating System Service Pack: %6<br><br> Client IP Address: %7<br><br><br><br><br>For more information about the impact of this, please visit  https://go.microsoft.com/fwlink/?linkid=2209514.|
|5839|The Netlogon service encountered a trust using RPC signing instead of RPC sealing.<br><br><br><br> Account Type: %1<br><br> Trust Name: %2<br><br> Trust Target: %3<br><br> Client IP Address: %4<br><br><br><br>For more information about the impact of this, please visit  https://go.microsoft.com/fwlink/?linkid=2209514.|
|5840|The Netlogon service created a secure channel with a client with RC4.<br><br><br><br> Account Name: %1<br><br> Domain: %2<br><br> Account Type: %3<br><br> Client IP Address: %4<br><br> Negotiated Flags: %5<br><br><br><br>For more information about why this was logged, please visit  https://go.microsoft.com/fwlink/?linkid=2209514.|
|5841|The Netlogon service denied a client using RC4 due to the 'RejectMd5Clients' setting.<br><br><br><br> Account Name: %1<br><br> Domain: %2<br><br> Account Type: %3<br><br> Client IP Address: %4<br><br> Negotiated Flags: %5<br><br><br><br>For more information about why this was denied, please visit  https://go.microsoft.com/fwlink/?linkid=2209514.|
|5890|An operation was attempted that is incompatible with the current membership state of the node.|
|5891|The quorum resource does not contain the quorum log.|
|5892|The membership engine requested shutdown of the cluster service on this node.|
|5893|The join operation failed because the cluster instance ID of the joining node does not match the cluster instance ID of the sponsor node.|
|5894|A matching cluster network for the specified IP address could not be found.|
|5895|The actual data type of the property did not match the expected data type of the property.|
|5896|The cluster node was evicted from the cluster successfully, but the node was not cleaned up. To determine what cleanup steps failed and how to recover, see the Failover Clustering application event log using Event Viewer.|
|5897|Two or more parameter values specified for a resource's properties are in conflict.|
|5898|This computer cannot be made a member of a cluster.|
|5899|This computer cannot be made a member of a cluster because it does not have the correct version of Windows installed.|
|5900|A cluster cannot be created with the specified cluster name because that cluster name is already in use. Specify a different name for the cluster.|
|5901|The cluster configuration action has already been committed.|
|5902|The cluster configuration action could not be rolled back.|
|5903|The drive letter assigned to a system disk on one node conflicted with the drive letter assigned to a disk on another node.|
|5904|One or more nodes in the cluster are running a version of Windows that does not support this operation.|
|5905|The name of the corresponding computer account doesn't match the Network Name for this resource.|
|5906|No network adapters are available.|
|5907|The cluster node has been poisoned.|
|5908|The group is unable to accept the request since it is moving to another node.|
|5909|The resource type cannot accept the request since is too busy performing another operation.|
|5910|The call to the cluster resource DLL timed out.|
|5911|The address is not valid for an IPv6 Address resource. A global IPv6 address is required, and it must match a cluster network. Compatibility addresses are not permitted.|
|5912|An internal cluster error occurred. A call to an invalid function was attempted.|
|5913|A parameter value is out of acceptable range.|
|5914|A network error occurred while sending data to another node in the cluster. The number of bytes transmitted was less than required.|
|5915|An invalid cluster registry operation was attempted.|
|5916|An input string of characters is not properly terminated.|
|5917|An input string of characters is not in a valid format for the data it represents.|
|5918|An internal cluster error occurred. A cluster database transaction was attempted while a transaction was already in progress.|
|5919|An internal cluster error occurred. There was an attempt to commit a cluster database transaction while no transaction was in progress.|
|5920|An internal cluster error occurred. Data was not properly initialized.|
|5921|An error occurred while reading from a stream of data. An unexpected number of bytes was returned.|
|5922|An error occurred while writing to a stream of data. The required number of bytes could not be written.|
|5923|An error occurred while deserializing a stream of cluster data.|
|5924|One or more property values for this resource are in conflict with one or more property values associated with its dependent resource(s).|
|5925|A quorum of cluster nodes was not present to form a cluster.|
|5926|The cluster network is not valid for an IPv6 Address resource, or it does not match the configured address.|
|5927|The cluster network is not valid for an IPv6 Tunnel resource. Check the configuration of the IP Address resource on which the IPv6 Tunnel resource depends.|
|5928|Quorum resource cannot reside in the Available Storage group.|
|5929|The dependencies for this resource are nested too deeply.|
|5930|The call into the resource DLL raised an unhandled exception.|
|5931|The RHS process failed to initialize.|
|5932|The Failover Clustering feature is not installed on this node.|
|5933|The resources must be online on the same node for this operation|
|5934|A new node can not be added since this cluster is already at its maximum number of nodes.|
|5935|This cluster can not be created since the specified number of nodes exceeds the maximum allowed limit.|
|5936|An attempt to use the specified cluster name failed because an enabled computer object with the given name already exists in the domain.|
|5937|This cluster cannot be destroyed. It has non-core application groups which must be deleted before the cluster can be destroyed.|
|5938|File share associated with file share witness resource cannot be hosted by this cluster or any of its nodes.|
|5939|Eviction of this node is invalid at this time. Due to quorum requirements node eviction will result in cluster shutdown.<br>If it is the last node in the cluster, destroy cluster command should be used.|
|5940|Only one instance of this resource type is allowed in the cluster.|
|5941|Only one instance of this resource type is allowed per resource group.|
|5942|The resource failed to come online due to the failure of one or more provider resources.|
|5943|The resource has indicated that it cannot come online on any node.|
|5944|The current operation cannot be performed on this group at this time.|
|5945|The directory or file is not located on a cluster shared volume.|
|5946|The Security Descriptor does not meet the requirements for a cluster.|
|5947|There is one or more shared volumes resources configured in the cluster.<br>Those resources must be moved to available storage in order for operation to succeed.|
|5948|This group or resource cannot be directly manipulated.<br>Use shared volume APIs to perform desired operation.|
|5949|Back up is in progress. Please wait for backup completion before trying this operation again.|
|5950|The path does not belong to a cluster shared volume.|
|5951|The cluster shared volume is not locally mounted on this node.|
|5952|The cluster watchdog is terminating.|
|5953|A resource vetoed a move between two nodes because they are incompatible.|
|5954|The request is invalid either because node weight cannot be changed while the cluster is in disk-only quorum mode, or because changing the node weight would violate the minimum cluster quorum requirements.|
|5955|The resource vetoed the call.|
|5956|Resource could not start or run because it could not reserve sufficient system resources.|
|5957|A resource vetoed a move between two nodes because the destination currently does not have enough resources to complete the operation.|
|5958|<br>A resource vetoed a move between two nodes because the source currently does not have enough resources to complete the operation.|
|5959|<br>The requested operation can not be completed because the group is queued for an operation.|
|5960|<br>The requested operation can not be completed because a resource has locked status.|
|5961|<br>The resource cannot move to another node because a cluster shared volume vetoed the operation.|
|5962|<br>A node drain is already in progress.|
|5963|<br>Clustered storage is not connected to the node.|
|5964|<br>The disk is not configured in a way to be used with CSV. CSV disks must have at least one partition that is formatted with NTFS or REFS.|
|5965|<br>The resource must be part of the Available Storage group to complete this action.|
|5966|<br>CSVFS failed operation as volume is in redirected mode.|
|5967|<br>CSVFS failed operation as volume is not in redirected mode.|
|5968|<br>Cluster properties cannot be returned at this time.|
|5969|<br>The clustered disk resource contains software snapshot diff area that are not supported for Cluster Shared Volumes.|
|5970|<br>The operation cannot be completed because the resource is in maintenance mode.|
|5971|<br>The operation cannot be completed because of cluster affinity conflicts|
|5972|<br>The operation cannot be completed because the resource is a replica virtual machine.|
|5973|<br>The Cluster Functional Level could not be increased because not all nodes in the cluster support the updated version.|
|5974|<br>Updating the cluster functional level failed because the cluster is running in fix quorum mode.<br>Start additional nodes which are members of the cluster until the cluster reaches quorum and the cluster will automatically<br>switch out of fix quorum mode, or stop and restart the cluster without the FixQuorum switch. Once the cluster is out<br>of fix quorum mode retry the Update-ClusterFunctionalLevel PowerShell cmdlet to update the cluster functional level.|
|5975|<br>The cluster functional level has been successfully updated but not all features are available yet. Restart the cluster by<br>using the Stop-Cluster PowerShell cmdlet followed by the Start-Cluster PowerShell cmdlet and all cluster features will<br>be available.|
|5976|<br>The cluster is currently performing a version upgrade.|
|5977|<br>The cluster did not successfully complete the version upgrade.|
|5978|<br>The cluster node is in grace period.|
|5979|<br>The operation has failed because CSV volume was not able to recover in time specified on this file object.|
|5980|<br>The operation failed because the requested node is not currently part of active cluster membership.|
|5981|<br>The operation failed because the requested cluster resource is currently unmonitored.|
|5982|<br>The operation failed because a resource does not support running in an unmonitored state.|
|5983|<br>The operation cannot be completed because a resource participates in replication.|
|5984|<br>The operation failed because the requested cluster node has been isolated|
|5985|<br>The operation failed because the requested cluster node has been quarantined|
|5986|<br>The operation failed because the specified database update condition was not met|
|5987|<br>A clustered space is in a degraded condition and the requested action cannot be completed at this time.|
|5988|<br>The operation failed because token delegation for this control is not supported.|
|5989|<br>The operation has failed because CSV has invalidated this file object.|
|5990|<br>This operation is supported only on the CSV coordinator node.|
|5991|<br>The cluster group set is not available for any further requests.|
|5992|<br>The cluster group set could not be found.|
|5993|<br>The action cannot be completed at this time because the cluster group set would fall below quorum and not be able to act as a provider.|
|5994|<br>The specified parent fault domain is not found.|
|5995|<br>The fault domain cannot be a child of the parent specified.|
|5996|<br>Storage Spaces Direct has rejected the proposed fault domain changes because it impacts the fault tolerance of the storage.|
|5997|<br>Storage Spaces Direct has rejected the proposed fault domain changes because it reduces the storage connected to the system.|
|5998|<br>Cluster infrastructure file server creation failed because a valid non-empty file server name was not provided.|
|5999|<br>The action cannot be completed because the cluster set management cluster is unreachable.|
|6000|The specified file could not be encrypted.|
|6001|The specified file could not be decrypted.|
|6002|The specified file is encrypted and the user does not have the ability to decrypt it.|
|6003|There is no valid encryption recovery policy configured for this system.|
|6004|The required encryption driver is not loaded for this system.|
|6005|The file was encrypted with a different encryption driver than is currently loaded.|
|6006|There are no EFS keys defined for the user.|
|6007|The specified file is not encrypted.|
|6008|The specified file is not in the defined EFS export format.|
|6009|The specified file is read only.|
|6010|The directory has been disabled for encryption.|
|6011|The server is not trusted for remote encryption operation.|
|6012|Recovery policy configured for this system contains invalid recovery certificate.|
|6013|The encryption algorithm used on the source file needs a bigger key buffer than the one on the destination file.|
|6014|The disk partition does not support file encryption.|
|6015|This machine is disabled for file encryption.|
|6016|A newer system is required to decrypt this encrypted file.|
|6017|The remote server sent an invalid response for a file being opened with Client Side Encryption.|
|6018|Client Side Encryption is not supported by the remote server even though it claims to support it.|
|6019|File is encrypted and should be opened in Client Side Encryption mode.|
|6020|A new encrypted file is being created and a $EFS needs to be provided.|
|6021|The SMB client requested a CSE FSCTL on a non-CSE file.|
|6022|The requested operation was blocked by policy. For more information, contact your system administrator.|
|6023|The specified file could not be encrypted with Windows Information Protection.|
|6118|The list of servers for this workgroup is not currently available|
|6200|The Task Scheduler service must be configured to run in the System account to function properly. Individual tasks may be configured to run in other accounts.|
|6250|<br>The object cannot be deleted from the local cluster because it is registered with the cluster set.|
|6600|Log service encountered an invalid log sector.|
|6601|Log service encountered a log sector with invalid block parity.|
|6602|Log service encountered a remapped log sector.|
|6603|Log service encountered a partial or incomplete log block.|
|6604|Log service encountered an attempt access data outside the active log range.|
|6605|Log service user marshalling buffers are exhausted.|
|6606|Log service encountered an attempt read from a marshalling area with an invalid read context.|
|6607|Log service encountered an invalid log restart area.|
|6608|Log service encountered an invalid log block version.|
|6609|Log service encountered an invalid log block.|
|6610|Log service encountered an attempt to read the log with an invalid read mode.|
|6611|Log service encountered a log stream with no restart area.|
|6612|Log service encountered a corrupted metadata file.|
|6613|Log service encountered a metadata file that could not be created by the log file system.|
|6614|Log service encountered a metadata file with inconsistent data.|
|6615|Log service encountered an attempt to erroneous allocate or dispose reservation space.|
|6616|Log service cannot delete log file or file system container.|
|6617|Log service has reached the maximum allowable containers allocated to a log file.|
|6618|Log service has attempted to read or write backward past the start of the log.|
|6619|Log policy could not be installed because a policy of the same type is already present.|
|6620|Log policy in question was not installed at the time of the request.|
|6621|The installed set of policies on the log is invalid.|
|6622|A policy on the log in question prevented the operation from completing.|
|6623|Log space cannot be reclaimed because the log is pinned by the archive tail.|
|6624|Log record is not a record in the log file.|
|6625|Number of reserved log records or the adjustment of the number of reserved log records is invalid.|
|6626|Reserved log space or the adjustment of the log space is invalid.|
|6627|An new or existing archive tail or base of the active log is invalid.|
|6628|Log space is exhausted.|
|6629|The log could not be set to the requested size.|
|6630|Log is multiplexed, no direct writes to the physical log is allowed.|
|6631|The operation failed because the log is a dedicated log.|
|6632|The operation requires an archive context.|
|6633|Log archival is in progress.|
|6634|The operation requires a non-ephemeral log, but the log is ephemeral.|
|6635|The log must have at least two containers before it can be read from or written to.|
|6636|A log client has already registered on the stream.|
|6637|A log client has not been registered on the stream.|
|6638|A request has already been made to handle the log full condition.|
|6639|Log service encountered an error when attempting to read from a log container.|
|6640|Log service encountered an error when attempting to write to a log container.|
|6641|Log service encountered an error when attempting open a log container.|
|6642|Log service encountered an invalid container state when attempting a requested action.|
|6643|Log service is not in the correct state to perform a requested action.|
|6644|Log space cannot be reclaimed because the log is pinned.|
|6645|Log metadata flush failed.|
|6646|Security on the log and its containers is inconsistent.|
|6647|Records were appended to the log or reservation changes were made, but the log could not be flushed.|
|6648|The log is pinned due to reservation consuming most of the log space. Free some reserved records to make space available.|
|6700|The transaction handle associated with this operation is not valid.|
|6701|The requested operation was made in the context of a transaction that is no longer active.|
|6702|The requested operation is not valid on the Transaction object in its current state.|
|6703|The caller has called a response API, but the response is not expected because the TM did not issue the corresponding request to the caller.|
|6704|It is too late to perform the requested operation, since the Transaction has already been aborted.|
|6705|It is too late to perform the requested operation, since the Transaction has already been committed.|
|6706|The Transaction Manager was unable to be successfully initialized. Transacted operations are not supported.|
|6707|The specified ResourceManager made no changes or updates to the resource under this transaction.|
|6708|The resource manager has attempted to prepare a transaction that it has not successfully joined.|
|6709|The Transaction object already has a superior enlistment, and the caller attempted an operation that would have created a new superior. Only a single superior enlistment is allow.|
|6710|The RM tried to register a protocol that already exists.|
|6711|The attempt to propagate the Transaction failed.|
|6712|The requested propagation protocol was not registered as a CRM.|
|6713|The buffer passed in to PushTransaction or PullTransaction is not in a valid format.|
|6714|The current transaction context associated with the thread is not a valid handle to a transaction object.|
|6715|The specified Transaction object could not be opened, because it was not found.|
|6716|The specified ResourceManager object could not be opened, because it was not found.|
|6717|The specified Enlistment object could not be opened, because it was not found.|
|6718|The specified TransactionManager object could not be opened, because it was not found.|
|6719|The object specified could not be created or opened, because its associated TransactionManager is not online.  The TransactionManager must be brought fully Online by calling RecoverTransactionManager to recover to the end of its LogFile before objects in its Transaction or ResourceManager namespaces can be opened.  In addition, errors in writing records to its LogFile can cause a TransactionManager to go offline.|
|6720|The specified TransactionManager was unable to create the objects contained in its logfile in the Ob namespace. Therefore, the TransactionManager was unable to recover.|
|6721|The call to create a superior Enlistment on this Transaction object could not be completed, because the Transaction object specified for the enlistment is a subordinate branch of the Transaction. Only the root of the Transaction can be enlisted on as a superior.|
|6722|Because the associated transaction manager or resource manager has been closed, the handle is no longer valid.|
|6723|The specified operation could not be performed on this Superior enlistment, because the enlistment was not created with the corresponding completion response in the NotificationMask.|
|6724|The specified operation could not be performed, because the record that would be logged was too long. This can occur because of two conditions: either there are too many Enlistments on this Transaction, or the combined RecoveryInformation being logged on behalf of those Enlistments is too long.|
|6725|Implicit transaction are not supported.|
|6726|The kernel transaction manager had to abort or forget the transaction because it blocked forward progress.|
|6727|The TransactionManager identity that was supplied did not match the one recorded in the TransactionManager's log file.|
|6728|This snapshot operation cannot continue because a transactional resource manager cannot be frozen in its current state.  Please try again.|
|6729|The transaction cannot be enlisted on with the specified EnlistmentMask, because the transaction has already completed the PrePrepare phase.  In order to ensure correctness, the ResourceManager must switch to a write-through mode and cease caching data within this transaction.  Enlisting for only subsequent transaction phases may still succeed.|
|6730|The transaction does not have a superior enlistment.|
|6731|The attempt to commit the Transaction completed, but it is possible that some portion of the transaction tree did not commit successfully due to heuristics.  Therefore it is possible that some data modified in the transaction may not have committed, resulting in transactional inconsistency.  If possible, check the consistency of the associated data.|
|6800|The function attempted to use a name that is reserved for use by another transaction.|
|6801|Transaction support within the specified resource manager is not started or was shut down due to an error.|
|6802|The metadata of the RM has been corrupted. The RM will not function.|
|6803|The specified directory does not contain a resource manager.|
|6805|The remote server or share does not support transacted file operations.|
|6806|The requested log size is invalid.|
|6807|The object (file, stream, link) corresponding to the handle has been deleted by a Transaction Savepoint Rollback.|
|6808|The specified file miniversion was not found for this transacted file open.|
|6809|The specified file miniversion was found but has been invalidated. Most likely cause is a transaction savepoint rollback.|
|6810|A miniversion may only be opened in the context of the transaction that created it.|
|6811|It is not possible to open a miniversion with modify access.|
|6812|It is not possible to create any more miniversions for this stream.|
|6814|The remote server sent mismatching version number or Fid for a file opened with transactions.|
|6815|The handle has been invalidated by a transaction. The most likely cause is the presence of memory mapping on a file or an open handle when the transaction ended or rolled back to savepoint.|
|6816|There is no transaction metadata on the file.|
|6817|The log data is corrupt.|
|6818|The file can't be recovered because there is a handle still open on it.|
|6819|The transaction outcome is unavailable because the resource manager responsible for it has disconnected.|
|6820|The request was rejected because the enlistment in question is not a superior enlistment.|
|6821|The transactional resource manager is already consistent. Recovery is not needed.|
|6822|The transactional resource manager has already been started.|
|6823|The file cannot be opened transactionally, because its identity depends on the outcome of an unresolved transaction.|
|6824|The operation cannot be performed because another transaction is depending on the fact that this property will not change.|
|6825|The operation would involve a single file with two transactional resource managers and is therefore not allowed.|
|6826|The $Txf directory must be empty for this operation to succeed.|
|6827|The operation would leave a transactional resource manager in an inconsistent state and is therefore not allowed.|
|6828|The operation could not be completed because the transaction manager does not have a log.|
|6829|A rollback could not be scheduled because a previously scheduled rollback has already executed or been queued for execution.|
|6830|The transactional metadata attribute on the file or directory is corrupt and unreadable.|
|6831|The encryption operation could not be completed because a transaction is active.|
|6832|This object is not allowed to be opened in a transaction.|
|6833|An attempt to create space in the transactional resource manager's log failed. The failure status has been recorded in the event log.|
|6834|Memory mapping (creating a mapped section) a remote file under a transaction is not supported.|
|6835|Transaction metadata is already present on this file and cannot be superseded.|
|6836|A transaction scope could not be entered because the scope handler has not been initialized.|
|6837|Promotion was required in order to allow the resource manager to enlist, but the transaction was set to disallow it.|
|6838|This file is open for modification in an unresolved transaction and may be opened for execute only by a transacted reader.|
|6839|The request to thaw frozen transactions was ignored because transactions had not previously been frozen.|
|6840|Transactions cannot be frozen because a freeze is already in progress.|
|6841|The target volume is not a snapshot volume. This operation is only valid on a volume mounted as a snapshot.|
|6842|The savepoint operation failed because files are open on the transaction. This is not permitted.|
|6843|Windows has discovered corruption in a file, and that file has since been repaired. Data loss may have occurred.|
|6844|The sparse operation could not be completed because a transaction is active on the file.|
|6845|The call to create a TransactionManager object failed because the Tm Identity stored in the logfile does not match the Tm Identity that was passed in as an argument.|
|6846|I/O was attempted on a section object that has been floated as a result of a transaction ending. There is no valid data.|
|6847|The transactional resource manager cannot currently accept transacted work due to a transient condition such as low resources.|
|6848|The transactional resource manager had too many transactions outstanding that could not be aborted. The transactional resource manger has been shut down.|
|6849|The operation could not be completed due to bad clusters on disk.|
|6850|The compression operation could not be completed because a transaction is active on the file.|
|6851|The operation could not be completed because the volume is dirty. Please run chkdsk and try again.|
|6852|The link tracking operation could not be completed because a transaction is active.|
|6853|This operation cannot be performed in a transaction.|
|6854|The handle is no longer properly associated with its transaction.  It may have been opened in a transactional resource manager that was subsequently forced to restart.  Please close the handle and open a new one.|
|6855|The specified operation could not be performed because the resource manager is not enlisted in the transaction.|
|7001|The specified session name is invalid.|
|7002|The specified protocol driver is invalid.|
|7003|The specified protocol driver was not found in the system path.|
|7004|The specified terminal connection driver was not found in the system path.|
|7005|A registry key for event logging could not be created for this session.|
|7006|A service with the same name already exists on the system.|
|7007|A close operation is pending on the session.|
|7008|There are no free output buffers available.|
|7009|The MODEM.INF file was not found.|
|7010|The modem name was not found in MODEM.INF.|
|7011|The modem did not accept the command sent to it. Verify that the configured modem name matches the attached modem.|
|7012|The modem did not respond to the command sent to it. Verify that the modem is properly cabled and powered on.|
|7013|Carrier detect has failed or carrier has been dropped due to disconnect.|
|7014|Dial tone not detected within the required time. Verify that the phone cable is properly attached and functional.|
|7015|Busy signal detected at remote site on callback.|
|7016|Voice detected at remote site on callback.|
|7017|Transport driver error|
|7022|The specified session cannot be found.|
|7023|The specified session name is already in use.|
|7024|The task you are trying to do can't be completed because Remote Desktop Services is currently busy. Please try again in a few minutes. Other users should still be able to log on.|
|7025|An attempt has been made to connect to a session whose video mode is not supported by the current client.|
|7035|The application attempted to enable DOS graphics mode. DOS graphics mode is not supported.|
|7037|Your interactive logon privilege has been disabled. Please contact your administrator.|
|7038|The requested operation can be performed only on the system console. This is most often the result of a driver or system DLL requiring direct console access.|
|7040|The client failed to respond to the server connect message.|
|7041|Disconnecting the console session is not supported.|
|7042|Reconnecting a disconnected session to the console is not supported.|
|7044|The request to control another session remotely was denied.|
|7045|The requested session access is denied.|
|7049|The specified terminal connection driver is invalid.|
|7050|The requested session cannot be controlled remotely.<br>This may be because the session is disconnected or does not currently have a user logged on.|
|7051|The requested session is not configured to allow remote control.|
|7052|Your request to connect to this Terminal Server has been rejected. Your Terminal Server client license number is currently being used by another user. Please call your system administrator to obtain a unique license number.|
|7053|Your request to connect to this Terminal Server has been rejected. Your Terminal Server client license number has not been entered for this copy of the Terminal Server client. Please contact your system administrator.|
|7054|The number of connections to this computer is limited and all connections are in use right now. Try connecting later or contact your system administrator.|
|7055|The client you are using is not licensed to use this system. Your logon request is denied.|
|7056|The system license has expired. Your logon request is denied.|
|7057|Remote control could not be terminated because the specified session is not currently being remotely controlled.|
|7058|The remote control of the console was terminated because the display mode was changed. Changing the display mode in a remote control session is not supported.|
|7059|Activation has already been reset the maximum number of times for this installation. Your activation timer will not be cleared.|
|7060|Remote logins are currently disabled.|
|7061|You do not have the proper encryption level to access this Session.|
|7062|The user %s\\%s is currently logged on to this computer. Only the current user or an administrator can log on to this computer.|
|7063|The user %s\\%s is already logged on to the console of this computer. You do not have permission to log in at this time. To resolve this issue, contact %s\\%s and have them log off.|
|7064|Unable to log you on because of an account restriction.|
|7065|The RDP protocol component %2 detected an error in the protocol stream and has disconnected the client.|
|7066|The Client Drive Mapping Service Has Connected on Terminal Connection.|
|7067|The Client Drive Mapping Service Has Disconnected on Terminal Connection.|
|7068|The Terminal Server security layer detected an error in the protocol stream and has disconnected the client.|
|7069|The target session is incompatible with the current session.|
|7070|Windows can't connect to your session because a problem occurred in the Windows video subsystem. Try connecting again later, or contact the server administrator for assistance.|
|8001|The file replication service API was called incorrectly.|
|8002|The file replication service cannot be started.|
|8003|The file replication service cannot be stopped.|
|8004|The file replication service API terminated the request. The event log may have more information.|
|8005|The file replication service terminated the request. The event log may have more information.|
|8006|The file replication service cannot be contacted. The event log may have more information.|
|8007|The file replication service cannot satisfy the request because the user has insufficient privileges. The event log may have more information.|
|8008|The file replication service cannot satisfy the request because authenticated RPC is not available. The event log may have more information.|
|8009|The file replication service cannot satisfy the request because the user has insufficient privileges on the domain controller. The event log may have more information.|
|8010|The file replication service cannot satisfy the request because authenticated RPC is not available on the domain controller. The event log may have more information.|
|8011|The file replication service cannot communicate with the file replication service on the domain controller. The event log may have more information.|
|8012|The file replication service on the domain controller cannot communicate with the file replication service on this computer. The event log may have more information.|
|8013|The file replication service cannot populate the system volume because of an internal error. The event log may have more information.|
|8014|The file replication service cannot populate the system volume because of an internal timeout. The event log may have more information.|
|8015|The file replication service cannot process the request. The system volume is busy with a previous request.|
|8016|The file replication service cannot stop replicating the system volume because of an internal error. The event log may have more information.|
|8017|The file replication service detected an invalid parameter.|