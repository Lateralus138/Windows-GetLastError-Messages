# Windows GetLastError Messages

![Readme Card](https://github-readme-stats.vercel.app/api/pin/?username=Lateralus138&repo=Windows-GetLastError-Messages)

- [Windows GetLastError Messages](#windows-getlasterror-messages)
  - [Generation Code](#generation-code)
  - [Error list](#error-list)
    - [0x00000000 - 0x00003FFF (0 - 16383)](#0x00000000---0x00003fff-0---16383)


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
  for (DWORD index = 0x0000; index < 0x3FFF; index++)
  {
    SetLastError(index);
    std::string em = GetLastErrorAsString();
    if (!em.empty())
    {
      std::string message = "\t- ";
      message.append(std::to_string(index));
      message.append(": ");
      message.append(em);
      message.pop_back();
      std::cout << message;
    }
  }
}
```
---

## Error list

### 0x00000000 - 0x00003FFF (0 - 16383)

6559 entries in total. Not all values have strings.

	- 1: Incorrect function.
	- 2: The system cannot find the file specified.
	- 3: The system cannot find the path specified.
	- 4: The system cannot open the file.
	- 5: Access is denied.
	- 6: The handle is invalid.
	- 7: The storage control blocks were destroyed.
	- 8: Not enough memory resources are available to process this command.
	- 9: The storage control block address is invalid.
	- 10: The environment is incorrect.
	- 11: An attempt was made to load a program with an incorrect format.
	- 12: The access code is invalid.
	- 13: The data is invalid.
	- 14: Not enough memory resources are available to complete this operation.
	- 15: The system cannot find the drive specified.
	- 16: The directory cannot be removed.
	- 17: The system cannot move the file to a different disk drive.
	- 18: There are no more files.
	- 19: The media is write protected.
	- 20: The system cannot find the device specified.
	- 21: The device is not ready.
	- 22: The device does not recognize the command.
	- 23: Data error (cyclic redundancy check).
	- 24: The program issued a command but the command length is incorrect.
	- 25: The drive cannot locate a specific area or track on the disk.
	- 26: The specified disk or diskette cannot be accessed.
	- 27: The drive cannot find the sector requested.
	- 28: The printer is out of paper.
	- 29: The system cannot write to the specified device.
	- 30: The system cannot read from the specified device.
	- 31: A device attached to the system is not functioning.
	- 32: The process cannot access the file because it is being used by another process.
	- 33: The process cannot access the file because another process has locked a portion of the file.
	- 34: The wrong diskette is in the drive.
Insert %2 (Volume Serial Number: %3) into drive %1.
	- 36: Too many files opened for sharing.
	- 38: Reached the end of the file.
	- 39: The disk is full.
	- 50: The request is not supported.
	- 51: Windows cannot find the network path. Verify that the network path is correct and the destination computer is not busy or turned off. If Windows still cannot find the network path, contact your network administrator.
	- 52: You were not connected because a duplicate name exists on the network. If joining a domain, go to System in Control Panel to change the computer name and try again. If joining a workgroup, choose another workgroup name.
	- 53: The network path was not found.
	- 54: The network is busy.
	- 55: The specified network resource or device is no longer available.
	- 56: The network BIOS command limit has been reached.
	- 57: A network adapter hardware error occurred.
	- 58: The specified server cannot perform the requested operation.
	- 59: An unexpected network error occurred.
	- 60: The remote adapter is not compatible.
	- 61: The printer queue is full.
	- 62: Space to store the file waiting to be printed is not available on the server.
	- 63: Your file waiting to be printed was deleted.
	- 64: The specified network name is no longer available.
	- 65: Network access is denied.
	- 66: The network resource type is not correct.
	- 67: The network name cannot be found.
	- 68: The name limit for the local computer network adapter card was exceeded.
	- 69: The network BIOS session limit was exceeded.
	- 70: The remote server has been paused or is in the process of being started.
	- 71: No more connections can be made to this remote computer at this time because there are already as many connections as the computer can accept.
	- 72: The specified printer or disk device has been paused.
	- 80: The file exists.
	- 82: The directory or file cannot be created.
	- 83: Fail on INT 24.
	- 84: Storage to process this request is not available.
	- 85: The local device name is already in use.
	- 86: The specified network password is not correct.
	- 87: The parameter is incorrect.
	- 88: A write fault occurred on the network.
	- 89: The system cannot start another process at this time.
	- 100: Cannot create another system semaphore.
	- 101: The exclusive semaphore is owned by another process.
	- 102: The semaphore is set and cannot be closed.
	- 103: The semaphore cannot be set again.
	- 104: Cannot request exclusive semaphores at interrupt time.
	- 105: The previous ownership of this semaphore has ended.
	- 106: Insert the diskette for drive %1.
	- 107: The program stopped because an alternate diskette was not inserted.
	- 108: The disk is in use or locked by another process.
	- 109: The pipe has been ended.
	- 110: The system cannot open the device or file specified.
	- 111: The file name is too long.
	- 112: There is not enough space on the disk.
	- 113: No more internal file identifiers available.
	- 114: The target internal file identifier is incorrect.
	- 117: The IOCTL call made by the application program is not correct.
	- 118: The verify-on-write switch parameter value is not correct.
	- 119: The system does not support the command requested.
	- 120: This function is not supported on this system.
	- 121: The semaphore timeout period has expired.
	- 122: The data area passed to a system call is too small.
	- 123: The filename, directory name, or volume label syntax is incorrect.
	- 124: The system call level is not correct.
	- 125: The disk has no volume label.
	- 126: The specified module could not be found.
	- 127: The specified procedure could not be found.
	- 128: There are no child processes to wait for.
	- 129: The %1 application cannot be run in Win32 mode.
	- 130: Attempt to use a file handle to an open disk partition for an operation other than raw disk I/O.
	- 131: An attempt was made to move the file pointer before the beginning of the file.
	- 132: The file pointer cannot be set on the specified device or file.
	- 133: A JOIN or SUBST command cannot be used for a drive that contains previously joined drives.
	- 134: An attempt was made to use a JOIN or SUBST command on a drive that has already been joined.
	- 135: An attempt was made to use a JOIN or SUBST command on a drive that has already been substituted.
	- 136: The system tried to delete the JOIN of a drive that is not joined.
	- 137: The system tried to delete the substitution of a drive that is not substituted.
	- 138: The system tried to join a drive to a directory on a joined drive.
	- 139: The system tried to substitute a drive to a directory on a substituted drive.
	- 140: The system tried to join a drive to a directory on a substituted drive.
	- 141: The system tried to SUBST a drive to a directory on a joined drive.
	- 142: The system cannot perform a JOIN or SUBST at this time.
	- 143: The system cannot join or substitute a drive to or for a directory on the same drive.
	- 144: The directory is not a subdirectory of the root directory.
	- 145: The directory is not empty.
	- 146: The path specified is being used in a substitute.
	- 147: Not enough resources are available to process this command.
	- 148: The path specified cannot be used at this time.
	- 149: An attempt was made to join or substitute a drive for which a directory on the drive is the target of a previous substitute.
	- 150: System trace information was not specified in your CONFIG.SYS file, or tracing is disallowed.
	- 151: The number of specified semaphore events for DosMuxSemWait is not correct.
	- 152: DosMuxSemWait did not execute; too many semaphores are already set.
	- 153: The DosMuxSemWait list is not correct.
	- 154: The volume label you entered exceeds the label character limit of the target file system.
	- 155: Cannot create another thread.
	- 156: The recipient process has refused the signal.
	- 157: The segment is already discarded and cannot be locked.
	- 158: The segment is already unlocked.
	- 159: The address for the thread ID is not correct.
	- 160: One or more arguments are not correct.
	- 161: The specified path is invalid.
	- 162: A signal is already pending.
	- 164: No more threads can be created in the system.
	- 167: Unable to lock a region of a file.
	- 170: The requested resource is in use.
	- 171: Device's command support detection is in progress.
	- 173: A lock request was not outstanding for the supplied cancel region.
	- 174: The file system does not support atomic changes to the lock type.
	- 180: The system detected a segment number that was not correct.
	- 182: The operating system cannot run %1.
	- 183: Cannot create a file when that file already exists.
	- 186: The flag passed is not correct.
	- 187: The specified system semaphore name was not found.
	- 188: The operating system cannot run %1.
	- 189: The operating system cannot run %1.
	- 190: The operating system cannot run %1.
	- 191: Cannot run %1 in Win32 mode.
	- 192: The operating system cannot run %1.
	- 193: %1 is not a valid Win32 application.
	- 194: The operating system cannot run %1.
	- 195: The operating system cannot run %1.
	- 196: The operating system cannot run this application program.
	- 197: The operating system is not presently configured to run this application.
	- 198: The operating system cannot run %1.
	- 199: The operating system cannot run this application program.
	- 200: The code segment cannot be greater than or equal to 64K.
	- 201: The operating system cannot run %1.
	- 202: The operating system cannot run %1.
	- 203: The system could not find the environment option that was entered.
	- 205: No process in the command subtree has a signal handler.
	- 206: The filename or extension is too long.
	- 207: The ring 2 stack is in use.
	- 208: The global filename characters, * or ?, are entered incorrectly or too many global filename characters are specified.
	- 209: The signal being posted is not correct.
	- 210: The signal handler cannot be set.
	- 212: The segment is locked and cannot be reallocated.
	- 214: Too many dynamic-link modules are attached to this program or dynamic-link module.
	- 215: Cannot nest calls to LoadModule.
	- 216: This version of %1 is not compatible with the version of Windows you're running. Check your computer's system information and then contact the software publisher.
	- 217: The image file %1 is signed, unable to modify.
	- 218: The image file %1 is strong signed, unable to modify.
	- 220: This file is checked out or locked for editing by another user.
	- 221: The file must be checked out before saving changes.
	- 222: The file type being saved or retrieved has been blocked.
	- 223: The file size exceeds the limit allowed and cannot be saved.
	- 224: Access Denied. Before opening files in this location, you must first add the web site to your trusted sites list, browse to the web site, and select the option to login automatically.
	- 225: Operation did not complete successfully because the file contains a virus or potentially unwanted software.
	- 226: This file contains a virus or potentially unwanted software and cannot be opened. Due to the nature of this virus or potentially unwanted software, the file has been removed from this location.
	- 229: The pipe is local.
	- 230: The pipe state is invalid.
	- 231: All pipe instances are busy.
	- 232: The pipe is being closed.
	- 233: No process is on the other end of the pipe.
	- 234: More data is available.
	- 235: The action requested resulted in no work being done. Error-style clean-up has been performed.
	- 240: The session was canceled.
	- 254: The specified extended attribute name was invalid.
	- 255: The extended attributes are inconsistent.
	- 258: The wait operation timed out.
	- 259: No more data is available.
	- 266: The copy functions cannot be used.
	- 267: The directory name is invalid.
	- 275: The extended attributes did not fit in the buffer.
	- 276: The extended attribute file on the mounted file system is corrupt.
	- 277: The extended attribute table file is full.
	- 278: The specified extended attribute handle is invalid.
	- 282: The mounted file system does not support extended attributes.
	- 288: Attempt to release mutex not owned by caller.
	- 298: Too many posts were made to a semaphore.
	- 299: Only part of a ReadProcessMemory or WriteProcessMemory request was completed.
	- 300: The oplock request is denied.
	- 301: An invalid oplock acknowledgment was received by the system.
	- 302: The volume is too fragmented to complete this operation.
	- 303: The file cannot be opened because it is in the process of being deleted.
	- 304: Short name settings may not be changed on this volume due to the global registry setting.
	- 305: Short names are not enabled on this volume.
	- 306: The security stream for the given volume is in an inconsistent state.
Please run CHKDSK on the volume.
	- 307: A requested file lock operation cannot be processed due to an invalid byte range.
	- 308: The subsystem needed to support the image type is not present.
	- 309: The specified file already has a notification GUID associated with it.
	- 310: An invalid exception handler routine has been detected.
	- 311: Duplicate privileges were specified for the token.
	- 312: No ranges for the specified operation were able to be processed.
	- 313: Operation is not allowed on a file system internal file.
	- 314: The physical resources of this disk have been exhausted.
	- 315: The token representing the data is invalid.
	- 316: The device does not support the command feature.
	- 317: The system cannot find message text for message number 0x%1 in the message file for %2.
	- 318: The scope specified was not found.
	- 319: The Central Access Policy specified is not defined on the target machine.
	- 320: The Central Access Policy obtained from Active Directory is invalid.
	- 321: The device is unreachable.
	- 322: The target device has insufficient resources to complete the operation.
	- 323: A data integrity checksum error occurred. Data in the file stream is corrupt.
	- 324: An attempt was made to modify both a KERNEL and normal Extended Attribute (EA) in the same operation.
	- 326: Device does not support file-level TRIM.
	- 327: The command specified a data offset that does not align to the device's granularity/alignment.
	- 328: The command specified an invalid field in its parameter list.
	- 329: An operation is currently in progress with the device.
	- 330: An attempt was made to send down the command via an invalid path to the target device.
	- 331: The command specified a number of descriptors that exceeded the maximum supported by the device.
	- 332: Scrub is disabled on the specified file.
	- 333: The storage device does not provide redundancy.
	- 334: The specified operation is not supported on a resident file.
	- 335: The specified operation is not supported on a compressed file.
	- 336: The specified operation is not supported on a directory.
	- 337: The specified copy of the requested data could not be read.
	- 338: The specified data could not be written to any of the copies.
	- 339: One or more copies of data on this device may be out of sync. No writes may be performed until a data integrity scan is completed.
	- 340: The supplied kernel information version is invalid.
	- 341: The supplied PEP information version is invalid.
	- 342: This object is not externally backed by any provider.
	- 343: The external backing provider is not recognized.
	- 344: Compressing this object would not save space.
	- 345: The request failed due to a storage topology ID mismatch.
	- 346: The operation was blocked by parental controls.
	- 347: A file system block being referenced has already reached the maximum reference count and can't be referenced any further.
	- 348: The requested operation failed because the file stream is marked to disallow writes.
	- 349: The requested operation failed with an architecture-specific failure code.
	- 350: No action was taken as a system reboot is required.
	- 351: The shutdown operation failed.
	- 352: The restart operation failed.
	- 353: The maximum number of sessions has been reached.
	- 354: Windows Information Protection policy does not allow access to this network resource.
	- 355: The device hint name buffer is too small to receive the remaining name.
	- 356: The requested operation was blocked by Windows Information Protection policy. For more information, contact your system administrator.
	- 357: The requested operation cannot be performed because hardware or software configuration of the device does not comply with Windows Information Protection under Lock policy. Please, verify that user PIN has been created. For more information, contact your system administrator.
	- 358: The cloud sync root metadata is corrupted.
	- 359: The device is in maintenance mode.
	- 360: The specified operation is not supported on a DAX volume.
	- 361: The volume has active DAX mappings.
	- 362: The cloud file provider is not running.
	- 363: The cloud file metadata is corrupt and unreadable.
	- 364: The cloud file metadata is too large.
	- 365: The cloud file property is too large.
	- 366: The cloud file property is possibly corrupt. The on-disk checksum does not match the computed checksum.
	- 367: The process creation has been blocked.
	- 368: The storage device has lost data or persistence.
	- 369: The provider that supports file system virtualization is temporarily unavailable.
	- 370: The metadata for file system virtualization is corrupt and unreadable.
	- 371: The provider that supports file system virtualization is too busy to complete this operation.
	- 372: The provider that supports file system virtualization is unknown.
	- 373: GDI handles were potentially leaked by the application.
	- 374: The maximum number of cloud file properties has been reached.
	- 375: The version of the cloud file property store is not supported.
	- 376: The file is not a cloud file.
	- 377: The file is not in sync with the cloud.
	- 378: The cloud sync root is already connected with another cloud sync provider.
	- 379: The operation is not supported by the cloud sync provider.
	- 380: The cloud operation is invalid.
	- 381: The cloud operation is not supported on a read-only volume.
	- 382: The operation is reserved for a connected cloud sync provider.
	- 383: The cloud sync provider failed to validate the downloaded data.
	- 384: You can't connect to the file share because it's not secure. This share requires the obsolete SMB1 protocol, which is unsafe and could expose your system to attack.
Your system requires SMB2 or higher. For more info on resolving this issue, see: https://go.microsoft.com/fwlink/?linkid=852747
	- 385: The virtualization operation is not allowed on the file in its current state.
	- 386: The cloud sync provider failed user authentication.
	- 387: The cloud sync provider failed to perform the operation due to low system resources.
	- 388: The cloud sync provider failed to perform the operation due to network being unavailable.
	- 389: The cloud operation was unsuccessful.
	- 390: The operation is only supported on files under a cloud sync root.
	- 391: The operation cannot be performed on cloud files in use.
	- 392: The operation cannot be performed on pinned cloud files.
	- 393: The cloud operation was aborted.
	- 394: The cloud file's property store is corrupt.
	- 395: Access to the cloud file is denied.
	- 396: The cloud operation cannot be performed on a file with incompatible hardlinks.
	- 397: The operation failed due to a conflicting cloud file property lock.
	- 398: The cloud operation was canceled by user.
	- 399: An externally encrypted syskey has been configured, but the system no longer supports this feature.  Please see https://go.microsoft.com/fwlink/?linkid=851152 for more information.
	- 400: The thread is already in background processing mode.
	- 401: The thread is not in background processing mode.
	- 402: The process is already in background processing mode.
	- 403: The process is not in background processing mode.
	- 404: The cloud file provider exited unexpectedly.
	- 405: The file is not a cloud sync root.
	- 406: The read or write operation to an encrypted file could not be completed because the file can only be accessed when the device is unlocked.
	- 407: The volume is not cluster aligned on the disk.
	- 408: No physically aligned free space was found on the volume.
	- 409: The APPX file can not be accessed because it is not encrypted as expected.
	- 410: A read or write of raw encrypted data cannot be performed because the file is not encrypted.
	- 411: An invalid file offset in the encrypted data info block was passed for read or write operation of file's raw encrypted data.
	- 412: An invalid offset and length combination in the encrypted data info block was passed for read or write operation of file's raw encrypted data.
	- 413: An invalid parameter in the encrypted data info block was passed for read or write operation of file's raw encrypted data.
	- 414: The Windows Subsystem for Linux has not been enabled.
	- 415: The specified data could not be read from any of the copies.
	- 416: The specified storage reserve ID is invalid.
	- 417: The specified storage reserve does not exist.
	- 418: The specified storage reserve already exists.
	- 419: The specified storage reserve is not empty.
	- 420: This operation requires a DAX volume.
	- 421: This stream is not DAX mappable.
	- 422: Operation cannot be performed on a time critical thread.
	- 423: User data protection is not supported for the current or provided user.
	- 424: This directory contains entries whose names differ only in case.
	- 425: The file cannot be safely opened because it is not supported by this version of Windows.
	- 426: The cloud operation was not completed before the time-out period expired.
	- 427: A task queue is required for this operation but none is available.
	- 428: Failed loading a valid version of srcsrv.dll.
	- 429: This operation is not supported with BTT enabled.
	- 430: This operation cannot be performed because encryption is currently disabled.
	- 431: This encryption operation cannot be performed on filesystem metadata.
	- 432: Encryption cannot be cleared on this file/directory because it still has an encrypted attribute.
	- 433: A device which does not exist was specified.
	- 434: Dehydration of the cloud file is disallowed by the cloud sync provider.
	- 435: A file snapshot operation was attempted when one is already in progress.
	- 436: A snapshot of the file cannot be taken because a user-mapped section is present.
	- 437: The file snapshot operation was terminated because one of the files was modified in a way incompatible with a snapshot operation.  Please try again.
	- 438: An I/O request could not be coordinated with a file snapshot operation.
	- 439: An unexpected error occurred while processing a file snapshot operation.
	- 440: A file snapshot operation received an invalid parameter.
	- 441: The operation could not be completed due to one or more unsatisfied dependencies.
	- 442: The file cannot be opened because the path has a case-sensitive directory.
	- 443: The filesystem couldn't handle one of the CacheManager's callback error codes.
	- 444: WSL 2 requires an update to its kernel component. For information please visit https://aka.ms/wsl2kernel
	- 445: This action is blocked, but you can choose to allow it. Please refer to the data loss prevention notification for further information.
	- 446: This action is blocked. Please refer to the data loss prevention notification for further information.
	- 447: Access is denied because the file contains potentially unwanted software or content the security administrator decided to block.
	- 448: The path cannot be traversed because it contains an untrusted mount point.
	- 449: This action is blocked. Please refer to the data loss prevention notification for further information.
	- 450: Neither developer unlocked mode nor side loading mode is enabled on the device.
	- 451: Can not change application type during upgrade or re-provision.
	- 452: The application has not been provisioned.
	- 453: The requested capability can not be authorized for this application.
	- 454: There is no capability authorization policy on the device.
	- 455: The capability authorization database has been corrupted.
	- 456: The custom capability's SCCD has an invalid catalog.
	- 457: None of the authorized entity elements in the SCCD matched the app being installed; either the PFNs don't match, or the element's signature hash doesn't validate.
	- 458: The custom capability's SCCD failed to parse.
	- 459: The custom capability's SCCD requires developer mode.
	- 460: There not all declared custom capabilities are found in the SCCD.
	- 470: The CimFS image is corrupt.
	- 471: The system does not support this version of the CimFS image.
	- 472: The storage stack returned STATUS_ACCESS_DENEID for the current operation.
	- 473: Insufficient Virtual Address resources to complete the operation.
	- 474: The specified index is beyond the bounds of valid range.
	- 475: The cloud provider failed to acknowledge a message before the time-out expired.
	- 480: The operation timed out waiting for this device to complete a PnP query-remove request due to a potential hang in its device stack. The system may need to be rebooted to complete the request.
	- 481: The operation timed out waiting for this device to complete a PnP query-remove request due to a potential hang in the device stack of a related device. The system may need to be rebooted to complete the operation.
	- 482: The operation timed out waiting for this device to complete a PnP query-remove request due to a potential hang in the device stack of an unrelated device. The system may need to be rebooted to complete the operation.
	- 483: The request failed due to a fatal device hardware error.
	- 487: Attempt to access invalid address.
	- 488: The volume contains paging, crash dump or other system critical files.
	- 489: The specified operation is not supported on an encrypted file.
	- 490: The specified operation is not supported on a sparse file.
	- 491: The specified operation is not supported on a pagefile.
	- 492: The specified operation is not supported on a volume.
	- 493: The specified operation is not supported on a BypassIO enabled file.
	- 494: The specified driver does not support BypassIO operations.
	- 495: The specified operation is not supported while encryption is enabled on the target object.
	- 496: The specified operation is not supported while compression is enabled on the target object.
	- 497: The specified operation is not supported while replication is enabled on the target object.
	- 498: The specified operation is not supported while deduplication is enabled on the target object.
	- 499: The specified operation is not supported while auditing is enabled on the target object.
	- 500: User profile cannot be loaded.
	- 501: The negotiated session key does not meet the minimum length requirement.
	- 502: Access denied when accessing the user profile.
	- 503: The specified operation is not supported while monitoring is enabled on the target object.
	- 504: The specified operation is not supported while snapshot is enabled on the target object.
	- 505: The specified operation is not supported while virtualization is enabled on the target object.
	- 506: At least one minifilter does not support bypass IO.
	- 507: The device needs to be reset.
	- 508: The volume is opened for exclusive write access, preventing files from being opened for write access.
	- 509: The specified operation is not supported on a file opened for cached IO.
	- 510: The file system encountered a metadata file with inconsistent data.
	- 511: A file system block being referenced has been modified after containing a weak reference.
	- 512: The source file system block being referenced has been modified after containing a weak reference.
	- 513: The target file system block being referenced has been modified after containing a weak reference.
	- 514: The target file system block is shared between multiple extents.
	- 534: Arithmetic result exceeded 32 bits.
	- 535: There is a process on other end of the pipe.
	- 536: Waiting for a process to open the other end of the pipe.
	- 537: Application verifier has found an error in the current process.
	- 538: An error occurred in the ABIOS subsystem.
	- 539: A warning occurred in the WX86 subsystem.
	- 540: An error occurred in the WX86 subsystem.
	- 541: An attempt was made to cancel or set a timer that has an associated APC and the subject thread is not the thread that originally set the timer with an associated APC routine.
	- 542: Unwind exception code.
	- 543: An invalid or unaligned stack was encountered during an unwind operation.
	- 544: An invalid unwind target was encountered during an unwind operation.
	- 545: Invalid Object Attributes specified to NtCreatePort or invalid Port Attributes specified to NtConnectPort
	- 546: Length of message passed to NtRequestPort or NtRequestWaitReplyPort was longer than the maximum message allowed by the port.
	- 547: An attempt was made to lower a quota limit below the current usage.
	- 548: An attempt was made to attach to a device that was already attached to another device.
	- 549: An attempt was made to execute an instruction at an unaligned address and the host system does not support unaligned instruction references.
	- 550: Profiling not started.
	- 551: Profiling not stopped.
	- 552: The passed ACL did not contain the minimum required information.
	- 553: The number of active profiling objects is at the maximum and no more may be started.
	- 554: Used to indicate that an operation cannot continue without blocking for I/O.
	- 555: Indicates that a thread attempted to terminate itself by default (called NtTerminateThread with NULL) and it was the last thread in the current process.
	- 556: If an MM error is returned which is not defined in the standard FsRtl filter, it is converted to one of the following errors which is guaranteed to be in the filter.
In this case information is lost, however, the filter correctly handles the exception.
	- 557: If an MM error is returned which is not defined in the standard FsRtl filter, it is converted to one of the following errors which is guaranteed to be in the filter.
In this case information is lost, however, the filter correctly handles the exception.
	- 558: If an MM error is returned which is not defined in the standard FsRtl filter, it is converted to one of the following errors which is guaranteed to be in the filter.
In this case information is lost, however, the filter correctly handles the exception.
	- 559: A malformed function table was encountered during an unwind operation.
	- 560: Indicates that an attempt was made to assign protection to a file system file or directory and one of the SIDs in the security descriptor could not be translated into a GUID that could be stored by the file system.
This causes the protection attempt to fail, which may cause a file creation attempt to fail.
	- 561: Indicates that an attempt was made to grow an LDT by setting its size, or that the size was not an even number of selectors.
	- 563: Indicates that the starting value for the LDT information was not an integral multiple of the selector size.
	- 564: Indicates that the user supplied an invalid descriptor when trying to set up Ldt descriptors.
	- 565: Indicates a process has too many threads to perform the requested action. For example, assignment of a primary token may only be performed when a process has zero or one threads.
	- 566: An attempt was made to operate on a thread within a specific process, but the thread specified is not in the process specified.
	- 567: Pagefile quota was exceeded.
	- 568: The Netlogon service cannot start because another Netlogon service running in the domain conflicts with the specified role.
	- 569: The SAM database on a Windows Server is significantly out of synchronization with the copy on the Domain Controller. A complete synchronization is required.
	- 570: The NtCreateFile API failed. This error should never be returned to an application, it is a place holder for the Windows Lan Manager Redirector to use in its internal error mapping routines.
	- 571: {Privilege Failed}
The I/O permissions for the process could not be changed.
	- 572: {Application Exit by CTRL+C}
The application terminated as a result of a CTRL+C.
	- 573: {Missing System File}
The required system file %hs is bad or missing.
	- 574: {Application Error}
The exception %s (0	- 575: {Application Error}
The application was unable to start correctly (0x%lx). Click OK to close the application.
	- 576: {Unable to Create Paging File}
The creation of the paging file %hs failed (%lx). The requested size was %ld.
	- 577: Windows cannot verify the digital signature for this file. A recent hardware or software change might have installed a file that is signed incorrectly or damaged, or that might be malicious software from an unknown source.
	- 578: {No Paging File Specified}
No paging file was specified in the system configuration.
	- 579: {EXCEPTION}
A real-mode application issued a floating-point instruction and floating-point hardware is not present.
	- 580: An event pair synchronization operation was performed using the thread specific client/server event pair object, but no event pair object was associated with the thread.
	- 581: A Windows Server has an incorrect configuration.
	- 582: An illegal character was encountered. For a multi-byte character set this includes a lead byte without a succeeding trail byte. For the Unicode character set this includes the characters 0xFFFF and 0xFFFE.
	- 583: The Unicode character is not defined in the Unicode character set installed on the system.
	- 584: The paging file cannot be created on a floppy diskette.
	- 585: The system BIOS failed to connect a system interrupt to the device or bus for which the device is connected.
	- 586: This operation is only allowed for the Primary Domain Controller of the domain.
	- 587: An attempt was made to acquire a mutant such that its maximum count would have been exceeded.
	- 588: A volume has been accessed for which a file system driver is required that has not yet been loaded.
	- 589: {Registry File Failure}
The registry cannot load the hive (file):
%hs
or its log or alternate.
It is corrupt, absent, or not writable.
	- 590: {Unexpected Failure in DebugActiveProcess}
An unexpected failure occurred while processing a DebugActiveProcess API request. You may choose OK to terminate the process, or Cancel to ignore the error.
	- 591: {Fatal System Error}
The %hs system process terminated unexpectedly with a status of 0	- 592: {Data Not Accepted}
The TDI client could not handle the data received during an indication.
	- 593: NTVDM encountered a hard error.
	- 594: {Cancel Timeout}
The driver %hs failed to complete a cancelled I/O request in the allotted time.
	- 595: {Reply Message Mismatch}
An attempt was made to reply to an LPC message, but the thread specified by the client ID in the message was not waiting on that message.
	- 596: {Delayed Write Failed}
Windows was unable to save all the data for the file %hs. The data has been lost.
This error may be caused by a failure of your computer hardware or network connection. Please try to save this file elsewhere.
	- 597: The parameter(s) passed to the server in the client/server shared memory window were invalid. Too much data may have been put in the shared memory window.
	- 598: The stream is not a tiny stream.
	- 599: The request must be handled by the stack overflow code.
	- 600: Internal OFS status codes indicating how an allocation operation is handled. Either it is retried after the containing onode is moved or the extent stream is converted to a large stream.
	- 601: The attempt to find the object found an object matching by ID on the volume but it is out of the scope of the handle used for the operation.
	- 602: The bucket array must be grown. Retry transaction after doing so.
	- 603: The user/kernel marshalling buffer has overflowed.
	- 604: The supplied variant structure contains invalid data.
	- 605: The specified buffer contains ill-formed data.
	- 606: {Audit Failed}
An attempt to generate a security audit failed.
	- 607: The timer resolution was not previously set by the current process.
	- 608: There is insufficient account information to log you on.
	- 609: {Invalid DLL Entrypoint}
The dynamic link library %hs is not written correctly. The stack pointer has been left in an inconsistent state.
The entrypoint should be declared as WINAPI or STDCALL. Select YES to fail the DLL load. Select NO to continue execution. Selecting NO may cause the application to operate incorrectly.
	- 610: {Invalid Service Callback Entrypoint}
The %hs service is not written correctly. The stack pointer has been left in an inconsistent state.
The callback entrypoint should be declared as WINAPI or STDCALL. Selecting OK will cause the service to continue operation. However, the service process may operate incorrectly.
	- 611: There is an IP address conflict with another system on the network
	- 612: There is an IP address conflict with another system on the network
	- 613: {Low On Registry Space}
The system has reached the maximum size allowed for the system part of the registry. Additional storage requests will be ignored.
	- 614: A callback return system service cannot be executed when no callback is active.
	- 615: The password provided is too short to meet the policy of your user account.
Please choose a longer password.
	- 616: The policy of your user account does not allow you to change passwords too frequently.
This is done to prevent users from changing back to a familiar, but potentially discovered, password.
If you feel your password has been compromised then please contact your administrator immediately to have a new one assigned.
	- 617: You have attempted to change your password to one that you have used in the past.
The policy of your user account does not allow this. Please select a password that you have not previously used.
	- 618: The specified compression format is unsupported.
	- 619: The specified hardware profile configuration is invalid.
	- 620: The specified Plug and Play registry device path is invalid.
	- 621: The specified quota list is internally inconsistent with its descriptor.
	- 622: {Windows Evaluation Notification}
The evaluation period for this installation of Windows has expired. This system will shutdown in 1 hour. To restore access to this installation of Windows, please upgrade this installation using a licensed distribution of this product.
	- 623: {Illegal System DLL Relocation}
The system DLL %hs was relocated in memory. The application will not run properly.
The relocation occurred because the DLL %hs occupied an address range reserved for Windows system DLLs. The vendor supplying the DLL should be contacted for a new DLL.
	- 624: {DLL Initialization Failed}
The application failed to initialize because the window station is shutting down.
	- 625: The validation process needs to continue on to the next step.
	- 626: There are no more matches for the current index enumeration.
	- 627: The range could not be added to the range list because of a conflict.
	- 628: The server process is running under a SID different than that required by client.
	- 629: A group marked use for deny only cannot be enabled.
	- 630: {EXCEPTION}
Multiple floating point faults.
	- 631: {EXCEPTION}
Multiple floating point traps.
	- 632: The requested interface is not supported.
	- 633: {System Standby Failed}
The driver %hs does not support standby mode. Updating this driver may allow the system to go to standby mode.
	- 634: The system file %1 has become corrupt and has been replaced.
	- 635: {Virtual Memory Minimum Too Low}
Your system is low on virtual memory. Windows is increasing the size of your virtual memory paging file.
During this process, memory requests for some applications may be denied. For more information, see Help.
	- 636: A device was removed so enumeration must be restarted.
	- 637: {Fatal System Error}
The system image %s is not properly signed.
The file has been replaced with the signed file.
The system has been shut down.
	- 638: Device will not start without a reboot.
	- 639: There is not enough power to complete the requested operation.
	- 640: ERROR_MULTIPLE_FAULT_VIOLATION
	- 641: The system is in the process of shutting down.
	- 642: An attempt to remove a processes DebugPort was made, but a port was not already associated with the process.
	- 643: This version of Windows is not compatible with the behavior version of directory forest, domain or domain controller.
	- 644: The specified range could not be found in the range list.
	- 646: The driver was not loaded because the system is booting into safe mode.
	- 647: The driver was not loaded because it failed its initialization call.
	- 648: The "%hs" encountered an error while applying power or reading the device configuration.
This may be caused by a failure of your hardware or by a poor connection.
	- 649: The create operation failed because the name contained at least one mount point which resolves to a volume to which the specified device object is not attached.
	- 650: The device object parameter is either not a valid device object or is not attached to the volume specified by the file name.
	- 651: A Machine Check Error has occurred. Please check the system eventlog for additional information.
	- 652: There was error [%2] processing the driver database.
	- 653: System hive size has exceeded its limit.
	- 654: The driver could not be loaded because a previous version of the driver is still in memory.
	- 655: {Volume Shadow Copy Service}
Please wait while the Volume Shadow Copy Service prepares volume %hs for hibernation.
	- 656: The system has failed to hibernate (The error code is %hs). Hibernation will be disabled until the system is restarted.
	- 657: The password provided is too long to meet the policy of your user account.
Please choose a shorter password.
	- 665: The requested operation could not be completed due to a file system limitation
	- 668: An assertion failure has occurred.
	- 669: An error occurred in the ACPI subsystem.
	- 670: WOW Assertion Error.
	- 671: A device is missing in the system BIOS MPS table. This device will not be used.
Please contact your system vendor for system BIOS update.
	- 672: A translator failed to translate resources.
	- 673: A IRQ translator failed to translate resources.
	- 674: Driver %2 returned invalid ID for a child device (%3).
	- 675: {Kernel Debugger Awakened}
the system debugger was awakened by an interrupt.
	- 676: {Handles Closed}
Handles to objects have been automatically closed as a result of the requested operation.
	- 677: {Too Much Information}
The specified access control list (ACL) contained more information than was expected.
	- 678: This warning level status indicates that the transaction state already exists for the registry sub-tree, but that a transaction commit was previously aborted.
The commit has NOT been completed, but has not been rolled back either (so it may still be committed if desired).
	- 679: {Media Changed}
The media may have changed.
	- 680: {GUID Substitution}
During the translation of a global identifier (GUID) to a Windows security ID (SID), no administratively-defined GUID prefix was found.
A substitute prefix was used, which will not compromise system security. However, this may provide a more restrictive access than intended.
	- 681: The create operation stopped after reaching a symbolic link
	- 682: A long jump has been executed.
	- 683: The Plug and Play query operation was not successful.
	- 684: A frame consolidation has been executed.
	- 685: {Registry Hive Recovered}
Registry hive (file):
%hs
was corrupted and it has been recovered. Some data might have been lost.
	- 686: The application is attempting to run executable code from the module %hs. This may be insecure. An alternative, %hs, is available. Should the application use the secure module %hs?
	- 687: The application is loading executable code from the module %hs. This is secure, but may be incompatible with previous releases of the operating system. An alternative, %hs, is available. Should the application use the secure module %hs?
	- 688: Debugger did not handle the exception.
	- 689: Debugger will reply later.
	- 690: Debugger cannot provide handle.
	- 691: Debugger terminated thread.
	- 692: Debugger terminated process.
	- 693: Debugger got control C.
	- 694: Debugger printed exception on control C.
	- 695: Debugger received RIP exception.
	- 696: Debugger received control break.
	- 697: Debugger command communication exception.
	- 698: {Object Exists}
An attempt was made to create an object and the object name already existed.
	- 699: {Thread Suspended}
A thread termination occurred while the thread was suspended. The thread was resumed, and termination proceeded.
	- 700: {Image Relocated}
An image file could not be mapped at the address specified in the image file. Local fixups must be performed on this image.
	- 701: This informational level status indicates that a specified registry sub-tree transaction state did not yet exist and had to be created.
	- 702: {Segment Load}
A virtual DOS machine (VDM) is loading, unloading, or moving an MS-DOS or Win16 program segment image.
An exception is raised so a debugger can load, unload or track symbols and breakpoints within these 16-bit segments.
	- 703: {Invalid Current Directory}
The process cannot switch to the startup current directory %hs.
Select OK to set current directory to %hs, or select CANCEL to exit.
	- 704: {Redundant Read}
To satisfy a read request, the NT fault-tolerant file system successfully read the requested data from a redundant copy.
This was done because the file system encountered a failure on a member of the fault-tolerant volume, but was unable to reassign the failing area of the device.
	- 705: {Redundant Write}
To satisfy a write request, the NT fault-tolerant file system successfully wrote a redundant copy of the information.
This was done because the file system encountered a failure on a member of the fault-tolerant volume, but was not able to reassign the failing area of the device.
	- 706: {Machine Type Mismatch}
The image file %hs is valid, but is for a machine type other than the current machine. Select OK to continue, or CANCEL to fail the DLL load.
	- 707: {Partial Data Received}
The network transport returned partial data to its client. The remaining data will be sent later.
	- 708: {Expedited Data Received}
The network transport returned data to its client that was marked as expedited by the remote system.
	- 709: {Partial Expedited Data Received}
The network transport returned partial data to its client and this data was marked as expedited by the remote system. The remaining data will be sent later.
	- 710: {TDI Event Done}
The TDI indication has completed successfully.
	- 711: {TDI Event Pending}
The TDI indication has entered the pending state.
	- 712: Checking file system on %wZ
	- 713: {Fatal Application Exit}
%hs
	- 714: The specified registry key is referenced by a predefined handle.
	- 715: {Page Unlocked}
The page protection of a locked page was changed to 'No Access' and the page was unlocked from memory and from the process.
	- 716: %hs
	- 717: {Page Locked}
One of the pages to lock was already locked.
	- 718: Application popup: %1 : %2
	- 719: ERROR_ALREADY_WIN32
	- 720: {Machine Type Mismatch}
The image file %hs is valid, but is for a machine type other than the current machine.
	- 721: A yield execution was performed and no thread was available to run.
	- 722: The resumable flag to a timer API was ignored.
	- 723: The arbiter has deferred arbitration of these resources to its parent
	- 724: The inserted CardBus device cannot be started because of a configuration error on "%hs".
	- 725: The CPUs in this multiprocessor system are not all the same revision level. To use all processors the operating system restricts itself to the features of the least capable processor in the system. Should problems occur with this system, contact the CPU manufacturer to see if this mix of processors is supported.
	- 726: The system was put into hibernation.
	- 727: The system was resumed from hibernation.
	- 728: Windows has detected that the system firmware (BIOS) was updated [previous firmware date = %2, current firmware date %3].
	- 729: A device driver is leaking locked I/O pages causing system degradation. The system has automatically enabled tracking code in order to try and catch the culprit.
	- 730: The system has awoken
	- 731: ERROR_WAIT_1
	- 732: ERROR_WAIT_2
	- 733: ERROR_WAIT_3
	- 734: ERROR_WAIT_63
	- 735: ERROR_ABANDONED_WAIT_0
	- 736: ERROR_ABANDONED_WAIT_63
	- 737: ERROR_USER_APC
	- 738: ERROR_KERNEL_APC
	- 739: ERROR_ALERTED
	- 740: The requested operation requires elevation.
	- 741: A reparse should be performed by the Object Manager since the name of the file resulted in a symbolic link.
	- 742: An open/create operation completed while an oplock break is underway.
	- 743: A new volume has been mounted by a file system.
	- 744: This success level status indicates that the transaction state already exists for the registry sub-tree, but that a transaction commit was previously aborted.
The commit has now been completed.
	- 745: This indicates that a notify change request has been completed due to closing the handle which made the notify change request.
	- 746: {Connect Failure on Primary Transport}
An attempt was made to connect to the remote server %hs on the primary transport, but the connection failed.
The computer WAS able to connect on a secondary transport.
	- 747: Page fault was a transition fault.
	- 748: Page fault was a demand zero fault.
	- 749: Page fault was a demand zero fault.
	- 750: Page fault was a demand zero fault.
	- 751: Page fault was satisfied by reading from a secondary storage device.
	- 752: Cached page was locked during operation.
	- 753: Crash dump exists in paging file.
	- 754: Specified buffer contains all zeros.
	- 755: A reparse should be performed by the Object Manager since the name of the file resulted in a symbolic link.
	- 756: The device has succeeded a query-stop and its resource requirements have changed.
	- 757: The translator has translated these resources into the global space and no further translations should be performed.
	- 758: A process being terminated has no threads to terminate.
	- 759: The specified process is not part of a job.
	- 760: The specified process is part of a job.
	- 761: {Volume Shadow Copy Service}
The system is now ready for hibernation.
	- 762: A file system or file system filter driver has successfully completed an FsFilter operation.
	- 763: The specified interrupt vector was already connected.
	- 764: The specified interrupt vector is still connected.
	- 765: An operation is blocked waiting for an oplock.
	- 766: Debugger handled exception
	- 767: Debugger continued
	- 768: An exception occurred in a user mode callback and the kernel callback frame should be removed.
	- 769: Compression is disabled for this volume.
	- 770: The data provider cannot fetch backwards through a result set.
	- 771: The data provider cannot scroll backwards through a result set.
	- 772: The data provider requires that previously fetched data is released before asking for more data.
	- 773: The data provider was not able to interpret the flags set for a column binding in an accessor.
	- 774: One or more errors occurred while processing the request.
	- 775: The implementation is not capable of performing the request.
	- 776: The client of a component requested an operation which is not valid given the state of the component instance.
	- 777: A version number could not be parsed.
	- 778: The iterator's start position is invalid.
	- 779: The hardware has reported an uncorrectable memory error.
	- 780: The attempted operation required self healing to be enabled.
	- 781: The Desktop heap encountered an error while allocating session memory. There is more information in the system event log.
	- 782: The system power state is transitioning from %2 to %3.
	- 783: The system power state is transitioning from %2 to %3 but could enter %4.
	- 784: A thread is getting dispatched with MCA EXCEPTION because of MCA.
	- 785: Access to %1 is monitored by policy rule %2.
	- 786: Access to %1 has been restricted by your Administrator by policy rule %2.
	- 787: A valid hibernation file has been invalidated and should be abandoned.
	- 788: {Delayed Write Failed}
Windows was unable to save all the data for the file %hs; the data has been lost.
This error may be caused by network connectivity issues. Please try to save this file elsewhere.
	- 789: {Delayed Write Failed}
Windows was unable to save all the data for the file %hs; the data has been lost.
This error was returned by the server on which the file exists. Please try to save this file elsewhere.
	- 790: {Delayed Write Failed}
Windows was unable to save all the data for the file %hs; the data has been lost.
This error may be caused if the device has been removed or the media is write-protected.
	- 791: The resources required for this device conflict with the MCFG table.
	- 792: The volume repair could not be performed while it is online.
Please schedule to take the volume offline so that it can be repaired.
	- 793: The volume repair was not successful.
	- 794: One of the volume corruption logs is full. Further corruptions that may be detected won't be logged.
	- 795: One of the volume corruption logs is internally corrupted and needs to be recreated. The volume may contain undetected corruptions and must be scanned.
	- 796: One of the volume corruption logs is unavailable for being operated on.
	- 797: One of the volume corruption logs was deleted while still having corruption records in them. The volume contains detected corruptions and must be scanned.
	- 798: One of the volume corruption logs was cleared by chkdsk and no longer contains real corruptions.
	- 799: Orphaned files exist on the volume but could not be recovered because no more new names could be created in the recovery directory. Files must be moved from the recovery directory.
	- 800: The oplock that was associated with this handle is now associated with a different handle.
	- 801: An oplock of the requested level cannot be granted.  An oplock of a lower level may be available.
	- 802: The operation did not complete successfully because it would cause an oplock to be broken. The caller has requested that existing oplocks not be broken.
	- 803: The handle with which this oplock was associated has been closed.  The oplock is now broken.
	- 804: The specified access control entry (ACE) does not contain a condition.
	- 805: The specified access control entry (ACE) contains an invalid condition.
	- 806: Access to the specified file handle has been revoked.
	- 807: {Image Relocated}
An image file was mapped at a different address from the one specified in the image file but fixups will still be automatically performed on the image.
	- 808: The read or write operation to an encrypted file could not be completed because the file has not been opened for data access.
	- 809: File metadata optimization is already in progress.
	- 810: The requested operation failed due to quota operation is still in progress.
	- 811: Access to the specified handle has been revoked.
	- 812: The callback function must be invoked inline.
	- 813: The specified CPU Set IDs are invalid.
	- 814: The specified enclave has not yet been terminated.
	- 815: An attempt was made to access protected memory in violation of its secure access policy.
	- 816: Multiple mappings to shared resource(s) on a server, using more than one transport, are not allowed. Use a single transport for all mappings to a server and try again.
	- 817: Multiple mappings to shared resource(s) on a server, using different certificate validation preferences, are not allowed. Use the same preference for all mappings to a server and try again.
	- 818: The specified copy of the requested data could not be read.
	- 819: The section creation request was failed because it would have been satisfied with a direct map and the caller explicitly signified this was not wanted.
	- 994: Access to the extended attribute was denied.
	- 995: The I/O operation has been aborted because of either a thread exit or an application request.
	- 996: Overlapped I/O event is not in a signaled state.
	- 997: Overlapped I/O operation is in progress.
	- 998: Invalid access to memory location.
	- 999: Error performing inpage operation.
	- 1001: Recursion too deep; the stack overflowed.
	- 1002: The window cannot act on the sent message.
	- 1003: Cannot complete this function.
	- 1004: Invalid flags.
	- 1005: The volume does not contain a recognized file system.
Please make sure that all required file system drivers are loaded and that the volume is not corrupted.
	- 1006: The volume for a file has been externally altered so that the opened file is no longer valid.
	- 1007: The requested operation cannot be performed in full-screen mode.
	- 1008: An attempt was made to reference a token that does not exist.
	- 1009: The configuration registry database is corrupt.
	- 1010: The configuration registry key is invalid.
	- 1011: The configuration registry key could not be opened.
	- 1012: The configuration registry key could not be read.
	- 1013: The configuration registry key could not be written.
	- 1014: One of the files in the registry database had to be recovered by use of a log or alternate copy. The recovery was successful.
	- 1015: The registry is corrupted. The structure of one of the files containing registry data is corrupted, or the system's memory image of the file is corrupted, or the file could not be recovered because the alternate copy or log was absent or corrupted.
	- 1016: An I/O operation initiated by the registry failed unrecoverably. The registry could not read in, or write out, or flush, one of the files that contain the system's image of the registry.
	- 1017: The system has attempted to load or restore a file into the registry, but the specified file is not in a registry file format.
	- 1018: Illegal operation attempted on a registry key that has been marked for deletion.
	- 1019: System could not allocate the required space in a registry log.
	- 1020: Cannot create a symbolic link in a registry key that already has subkeys or values.
	- 1021: Cannot create a stable subkey under a volatile parent key.
	- 1022: A notify change request is being completed and the information is not being returned in the caller's buffer. The caller now needs to enumerate the files to find the changes.
	- 1051: A stop control has been sent to a service that other running services are dependent on.
	- 1052: The requested control is not valid for this service.
	- 1053: The service did not respond to the start or control request in a timely fashion.
	- 1054: A thread could not be created for the service.
	- 1055: The service database is locked.
	- 1056: An instance of the service is already running.
	- 1057: The account name is invalid or does not exist, or the password is invalid for the account name specified.
	- 1058: The service cannot be started, either because it is disabled or because it has no enabled devices associated with it.
	- 1059: Circular service dependency was specified.
	- 1060: The specified service does not exist as an installed service.
	- 1061: The service cannot accept control messages at this time.
	- 1062: The service has not been started.
	- 1063: The service process could not connect to the service controller.
	- 1064: An exception occurred in the service when handling the control request.
	- 1065: The database specified does not exist.
	- 1066: The service has returned a service-specific error code.
	- 1067: The process terminated unexpectedly.
	- 1068: The dependency service or group failed to start.
	- 1069: The service did not start due to a logon failure.
	- 1070: After starting, the service hung in a start-pending state.
	- 1071: The specified service database lock is invalid.
	- 1072: The specified service has been marked for deletion.
	- 1073: The specified service already exists.
	- 1074: The system is currently running with the last-known-good configuration.
	- 1075: The dependency service does not exist or has been marked for deletion.
	- 1076: The current boot has already been accepted for use as the last-known-good control set.
	- 1077: No attempts to start the service have been made since the last boot.
	- 1078: The name is already in use as either a service name or a service display name.
	- 1079: The account specified for this service is different from the account specified for other services running in the same process.
	- 1080: Failure actions can only be set for Win32 services, not for drivers.
	- 1081: This service runs in the same process as the service control manager.
Therefore, the service control manager cannot take action if this service's process terminates unexpectedly.
	- 1082: No recovery program has been configured for this service.
	- 1083: The executable program that this service is configured to run in does not implement the service.
	- 1084: This service cannot be started in Safe Mode
	- 1100: The physical end of the tape has been reached.
	- 1101: A tape access reached a filemark.
	- 1102: The beginning of the tape or a partition was encountered.
	- 1103: A tape access reached the end of a set of files.
	- 1104: No more data is on the tape.
	- 1105: Tape could not be partitioned.
	- 1106: When accessing a new tape of a multivolume partition, the current block size is incorrect.
	- 1107: Tape partition information could not be found when loading a tape.
	- 1108: Unable to lock the media eject mechanism.
	- 1109: Unable to unload the media.
	- 1110: The media in the drive may have changed.
	- 1111: The I/O bus was reset.
	- 1112: No media in drive.
	- 1113: No mapping for the Unicode character exists in the target multi-byte code page.
	- 1114: A dynamic link library (DLL) initialization routine failed.
	- 1115: A system shutdown is in progress.
	- 1116: Unable to abort the system shutdown because no shutdown was in progress.
	- 1117: The request could not be performed because of an I/O device error.
	- 1118: No serial device was successfully initialized. The serial driver will unload.
	- 1119: Unable to open a device that was sharing an interrupt request (IRQ) with other devices. At least one other device that uses that IRQ was already opened.
	- 1120: A serial I/O operation was completed by another write to the serial port.
(The IOCTL_SERIAL_XOFF_COUNTER reached zero.)
	- 1121: A serial I/O operation completed because the timeout period expired.
(The IOCTL_SERIAL_XOFF_COUNTER did not reach zero.)
	- 1122: No ID address mark was found on the floppy disk.
	- 1123: Mismatch between the floppy disk sector ID field and the floppy disk controller track address.
	- 1124: The floppy disk controller reported an error that is not recognized by the floppy disk driver.
	- 1125: The floppy disk controller returned inconsistent results in its registers.
	- 1126: While accessing the hard disk, a recalibrate operation failed, even after retries.
	- 1127: While accessing the hard disk, a disk operation failed even after retries.
	- 1128: While accessing the hard disk, a disk controller reset was needed, but even that failed.
	- 1129: Physical end of tape encountered.
	- 1130: Not enough server memory resources are available to process this command.
	- 1131: A potential deadlock condition has been detected.
	- 1132: The base address or the file offset specified does not have the proper alignment.
	- 1140: An attempt to change the system power state was vetoed by another application or driver.
	- 1141: The system BIOS failed an attempt to change the system power state.
	- 1142: An attempt was made to create more links on a file than the file system supports.
	- 1150: The specified program requires a newer version of Windows.
	- 1151: The specified program is not a Windows or MS-DOS program.
	- 1152: Cannot start more than one instance of the specified program.
	- 1153: The specified program was written for an earlier version of Windows.
	- 1154: One of the library files needed to run this application is damaged.
	- 1155: No application is associated with the specified file for this operation.
	- 1156: An error occurred in sending the command to the application.
	- 1157: One of the library files needed to run this application cannot be found.
	- 1158: The current process has used all of its system allowance of handles for Window Manager objects.
	- 1159: The message can be used only with synchronous operations.
	- 1160: The indicated source element has no media.
	- 1161: The indicated destination element already contains media.
	- 1162: The indicated element does not exist.
	- 1163: The indicated element is part of a magazine that is not present.
	- 1164: The indicated device requires reinitialization due to hardware errors.
	- 1165: The device has indicated that cleaning is required before further operations are attempted.
	- 1166: The device has indicated that its door is open.
	- 1167: The device is not connected.
	- 1168: Element not found.
	- 1169: There was no match for the specified key in the index.
	- 1170: The property set specified does not exist on the object.
	- 1171: The point passed to GetMouseMovePoints is not in the buffer.
	- 1172: The tracking (workstation) service is not running.
	- 1173: The Volume ID could not be found.
	- 1175: Unable to remove the file to be replaced.
	- 1176: Unable to move the replacement file to the file to be replaced. The file to be replaced has retained its original name.
	- 1177: Unable to move the replacement file to the file to be replaced. The file to be replaced has been renamed using the backup name.
	- 1178: The volume change journal is being deleted.
	- 1179: The volume change journal is not active.
	- 1180: A file was found, but it may not be the correct file.
	- 1181: The journal entry has been deleted from the journal.
	- 1184: An attempt was made to access a partition that has begun termination.
	- 1190: A system shutdown has already been scheduled.
	- 1191: The system shutdown cannot be initiated because there are other users logged on to the computer.
	- 1192: The system shutdown cannot safely proceed without enabling node maintenance mode for cluster node and waiting for the drain to complete.
	- 1200: The specified device name is invalid.
	- 1201: The device is not currently connected but it is a remembered connection.
	- 1202: The local device name has a remembered connection to another network resource.
	- 1203: The network path was either typed incorrectly, does not exist, or the network provider is not currently available. Please try retyping the path or contact your network administrator.
	- 1204: The specified network provider name is invalid.
	- 1205: Unable to open the network connection profile.
	- 1206: The network connection profile is corrupted.
	- 1207: Cannot enumerate a noncontainer.
	- 1208: An extended error has occurred.
	- 1209: The format of the specified group name is invalid.
	- 1210: The format of the specified computer name is invalid.
	- 1211: The format of the specified event name is invalid.
	- 1212: The format of the specified domain name is invalid.
	- 1213: The format of the specified service name is invalid.
	- 1214: The format of the specified network name is invalid.
	- 1215: The format of the specified share name is invalid.
	- 1216: The format of the specified password is invalid.
	- 1217: The format of the specified message name is invalid.
	- 1218: The format of the specified message destination is invalid.
	- 1219: Multiple connections to a server or shared resource by the same user, using more than one user name, are not allowed. Disconnect all previous connections to the server or shared resource and try again.
	- 1220: An attempt was made to establish a session to a network server, but there are already too many sessions established to that server.
	- 1221: The workgroup or domain name is already in use by another computer on the network.
	- 1222: The network is not present or not started.
	- 1223: The operation was canceled by the user.
	- 1224: The requested operation cannot be performed on a file with a user-mapped section open.
	- 1225: The remote computer refused the network connection.
	- 1226: The network connection was gracefully closed.
	- 1227: The network transport endpoint already has an address associated with it.
	- 1228: An address has not yet been associated with the network endpoint.
	- 1229: An operation was attempted on a nonexistent network connection.
	- 1230: An invalid operation was attempted on an active network connection.
	- 1231: The network location cannot be reached. For information about network troubleshooting, see Windows Help.
	- 1232: The network location cannot be reached. For information about network troubleshooting, see Windows Help.
	- 1233: The network location cannot be reached. For information about network troubleshooting, see Windows Help.
	- 1234: No service is operating at the destination network endpoint on the remote system.
	- 1235: The request was aborted.
	- 1236: The network connection was aborted by the local system.
	- 1237: The operation could not be completed. A retry should be performed.
	- 1238: A connection to the server could not be made because the limit on the number of concurrent connections for this account has been reached.
	- 1239: Attempting to log in during an unauthorized time of day for this account.
	- 1240: The account is not authorized to log in from this station.
	- 1241: The network address could not be used for the operation requested.
	- 1242: The service is already registered.
	- 1243: The specified service does not exist.
	- 1244: The operation being requested was not performed because the user has not been authenticated.
	- 1245: The operation being requested was not performed because the user has not logged on to the network. The specified service does not exist.
	- 1246: Continue with work in progress.
	- 1247: An attempt was made to perform an initialization operation when initialization has already been completed.
	- 1248: No more local devices.
	- 1249: The specified site does not exist.
	- 1250: A domain controller with the specified name already exists.
	- 1251: This operation is supported only when you are connected to the server.
	- 1252: The group policy framework should call the extension even if there are no changes.
	- 1253: The specified user does not have a valid profile.
	- 1254: This operation is not supported on a computer running Windows Server 2003 for Small Business Server
	- 1255: The server machine is shutting down.
	- 1256: The remote system is not available. For information about network troubleshooting, see Windows Help.
	- 1257: The security identifier provided is not from an account domain.
	- 1258: The security identifier provided does not have a domain component.
	- 1259: AppHelp dialog canceled thus preventing the application from starting.
	- 1260: This program is blocked by group policy. For more information, contact your system administrator.
	- 1261: A program attempt to use an invalid register value. Normally caused by an uninitialized register. This error is Itanium specific.
	- 1262: The share is currently offline or does not exist.
	- 1263: The Kerberos protocol encountered an error while validating the KDC certificate during smartcard logon. There is more information in the system event log.
	- 1264: The Kerberos protocol encountered an error while attempting to utilize the smartcard subsystem.
	- 1265: The system cannot contact a domain controller to service the authentication request. Please try again later.
	- 1271: The machine is locked and cannot be shut down without the force option.
	- 1272: You can't access this shared folder because your organization's security policies block unauthenticated guest access. These policies help protect your PC from unsafe or malicious devices on the network.
	- 1273: An application-defined callback gave invalid data when called.
	- 1274: The group policy framework should call the extension in the synchronous foreground policy refresh.
	- 1275: This driver has been blocked from loading
	- 1276: A dynamic link library (DLL) referenced a module that was neither a DLL nor the process's executable image.
	- 1277: Windows cannot open this program since it has been disabled.
	- 1278: Windows cannot open this program because the license enforcement system has been tampered with or become corrupted.
	- 1279: A transaction recover failed.
	- 1280: The current thread has already been converted to a fiber.
	- 1281: The current thread has already been converted from a fiber.
	- 1282: The system detected an overrun of a stack-based buffer in this application. This overrun could potentially allow a malicious user to gain control of this application.
	- 1283: Data present in one of the parameters is more than the function can operate on.
	- 1284: An attempt to do an operation on a debug object failed because the object is in the process of being deleted.
	- 1285: An attempt to delay-load a .dll or get a function address in a delay-loaded .dll failed.
	- 1286: %1 is a 16-bit application. You do not have permissions to execute 16-bit applications. Check your permissions with your system administrator.
	- 1287: Insufficient information exists to identify the cause of failure.
	- 1288: The parameter passed to a C runtime function is incorrect.
	- 1289: The operation occurred beyond the valid data length of the file.
	- 1290: The service start failed since one or more services in the same process have an incompatible service SID type setting. A service with restricted service SID type can only coexist in the same process with other services with a restricted SID type. If the service SID type for this service was just configured, the hosting process must be restarted in order to start this service.
	- 1291: The process hosting the driver for this device has been terminated.
	- 1292: An operation attempted to exceed an implementation-defined limit.
	- 1293: Either the target process, or the target thread's containing process, is a protected process.
	- 1294: The service notification client is lagging too far behind the current state of services in the machine.
	- 1295: The requested file operation failed because the storage quota was exceeded.
To free up disk space, move files to a different location or delete unnecessary files. For more information, contact your system administrator.
	- 1296: The requested file operation failed because the storage policy blocks that type of file. For more information, contact your system administrator.
	- 1297: A privilege that the service requires to function properly does not exist in the service account configuration.
You may use the Services Microsoft Management Console (MMC) snap-in (services.msc) and the Local Security Settings MMC snap-in (secpol.msc) to view the service configuration and the account configuration.
	- 1298: A thread involved in this operation appears to be unresponsive.
	- 1299: Indicates a particular Security ID may not be assigned as the label of an object.
	- 1300: Not all privileges or groups referenced are assigned to the caller.
	- 1301: Some mapping between account names and security IDs was not done.
	- 1302: No system quota limits are specifically set for this account.
	- 1303: No encryption key is available. A well-known encryption key was returned.
	- 1304: The password is too complex to be converted to a LAN Manager password. The LAN Manager password returned is a NULL string.
	- 1305: The revision level is unknown.
	- 1306: Indicates two revision levels are incompatible.
	- 1307: This security ID may not be assigned as the owner of this object.
	- 1308: This security ID may not be assigned as the primary group of an object.
	- 1309: An attempt has been made to operate on an impersonation token by a thread that is not currently impersonating a client.
	- 1310: The group may not be disabled.
	- 1311: We can't sign you in with this credential because your domain isn't available. Make sure your device is connected to your organization's network and try again. If you previously signed in on this device with another credential, you can sign in with that credential.
	- 1312: A specified logon session does not exist. It may already have been terminated.
	- 1313: A specified privilege does not exist.
	- 1314: A required privilege is not held by the client.
	- 1315: The name provided is not a properly formed account name.
	- 1316: The specified account already exists.
	- 1317: The specified account does not exist.
	- 1318: The specified group already exists.
	- 1319: The specified group does not exist.
	- 1320: Either the specified user account is already a member of the specified group, or the specified group cannot be deleted because it contains a member.
	- 1321: The specified user account is not a member of the specified group account.
	- 1322: This operation is disallowed as it could result in an administration account being disabled, deleted or unable to logon.
	- 1323: Unable to update the password. The value provided as the current password is incorrect.
	- 1324: Unable to update the password. The value provided for the new password contains values that are not allowed in passwords.
	- 1325: Unable to update the password. The value provided for the new password does not meet the length, complexity, or history requirements of the domain.
	- 1326: The user name or password is incorrect.
	- 1327: Account restrictions are preventing this user from signing in. For example: blank passwords aren't allowed, sign-in times are limited, or a policy restriction has been enforced.
	- 1328: Your account has time restrictions that keep you from signing in right now.
	- 1329: This user isn't allowed to sign in to this computer.
	- 1330: The password for this account has expired.
	- 1331: This user can't sign in because this account is currently disabled.
	- 1332: No mapping between account names and security IDs was done.
	- 1333: Too many local user identifiers (LUIDs) were requested at one time.
	- 1334: No more local user identifiers (LUIDs) are available.
	- 1335: The subauthority part of a security ID is invalid for this particular use.
	- 1336: The access control list (ACL) structure is invalid.
	- 1337: The security ID structure is invalid.
	- 1338: The security descriptor structure is invalid.
	- 1340: The inherited access control list (ACL) or access control entry (ACE) could not be built.
	- 1341: The server is currently disabled.
	- 1342: The server is currently enabled.
	- 1343: The value provided was an invalid value for an identifier authority.
	- 1344: No more memory is available for security information updates.
	- 1345: The specified attributes are invalid, or incompatible with the attributes for the group as a whole.
	- 1346: Either a required impersonation level was not provided, or the provided impersonation level is invalid.
	- 1347: Cannot open an anonymous level security token.
	- 1348: The validation information class requested was invalid.
	- 1349: The type of the token is inappropriate for its attempted use.
	- 1350: Unable to perform a security operation on an object that has no associated security.
	- 1351: Configuration information could not be read from the domain controller, either because the machine is unavailable, or access has been denied.
	- 1352: The security account manager (SAM) or local security authority (LSA) server was in the wrong state to perform the security operation.
	- 1353: The domain was in the wrong state to perform the security operation.
	- 1354: This operation is only allowed for the Primary Domain Controller of the domain.
	- 1355: The specified domain either does not exist or could not be contacted.
	- 1356: The specified domain already exists.
	- 1357: An attempt was made to exceed the limit on the number of domains per server.
	- 1358: Unable to complete the requested operation because of either a catastrophic media failure or a data structure corruption on the disk.
	- 1359: An internal error occurred.
	- 1360: Generic access types were contained in an access mask which should already be mapped to nongeneric types.
	- 1361: A security descriptor is not in the right format (absolute or self-relative).
	- 1362: The requested action is restricted for use by logon processes only. The calling process has not registered as a logon process.
	- 1363: Cannot start a new logon session with an ID that is already in use.
	- 1364: A specified authentication package is unknown.
	- 1365: The logon session is not in a state that is consistent with the requested operation.
	- 1366: The logon session ID is already in use.
	- 1367: A logon request contained an invalid logon type value.
	- 1368: Unable to impersonate using a named pipe until data has been read from that pipe.
	- 1369: The transaction state of a registry subtree is incompatible with the requested operation.
	- 1370: An internal security database corruption has been encountered.
	- 1371: Cannot perform this operation on built-in accounts.
	- 1372: Cannot perform this operation on this built-in special group.
	- 1373: Cannot perform this operation on this built-in special user.
	- 1374: The user cannot be removed from a group because the group is currently the user's primary group.
	- 1375: The token is already in use as a primary token.
	- 1376: The specified local group does not exist.
	- 1377: The specified account name is not a member of the group.
	- 1378: The specified account name is already a member of the group.
	- 1379: The specified local group already exists.
	- 1380: Logon failure: the user has not been granted the requested logon type at this computer.
	- 1381: The maximum number of secrets that may be stored in a single system has been exceeded.
	- 1382: The length of a secret exceeds the maximum length allowed.
	- 1383: The local security authority database contains an internal inconsistency.
	- 1384: During a logon attempt, the user's security context accumulated too many security IDs.
	- 1385: Logon failure: the user has not been granted the requested logon type at this computer.
	- 1386: A cross-encrypted password is necessary to change a user password.
	- 1387: A member could not be added to or removed from the local group because the member does not exist.
	- 1388: A new member could not be added to a local group because the member has the wrong account type.
	- 1389: Too many security IDs have been specified.
	- 1390: A cross-encrypted password is necessary to change this user password.
	- 1391: Indicates an ACL contains no inheritable components.
	- 1392: The file or directory is corrupted and unreadable.
	- 1393: The disk structure is corrupted and unreadable.
	- 1394: There is no user session key for the specified logon session.
	- 1395: The service being accessed is licensed for a particular number of connections. No more connections can be made to the service at this time because there are already as many connections as the service can accept.
	- 1396: The target account name is incorrect.
	- 1397: Mutual Authentication failed. The server's password is out of date at the domain controller.
	- 1398: There is a time and/or date difference between the client and server.
	- 1399: This operation cannot be performed on the current domain.
	- 1400: Invalid window handle.
	- 1401: Invalid menu handle.
	- 1402: Invalid cursor handle.
	- 1403: Invalid accelerator table handle.
	- 1404: Invalid hook handle.
	- 1405: Invalid handle to a multiple-window position structure.
	- 1406: Cannot create a top-level child window.
	- 1407: Cannot find window class.
	- 1408: Invalid window; it belongs to other thread.
	- 1409: Hot key is already registered.
	- 1410: Class already exists.
	- 1411: Class does not exist.
	- 1412: Class still has open windows.
	- 1413: Invalid index.
	- 1414: Invalid icon handle.
	- 1415: Using private DIALOG window words.
	- 1416: The list box identifier was not found.
	- 1417: No wildcards were found.
	- 1418: Thread does not have a clipboard open.
	- 1419: Hot key is not registered.
	- 1420: The window is not a valid dialog window.
	- 1421: Control ID not found.
	- 1422: Invalid message for a combo box because it does not have an edit control.
	- 1423: The window is not a combo box.
	- 1424: Height must be less than 256.
	- 1425: Invalid device context (DC) handle.
	- 1426: Invalid hook procedure type.
	- 1427: Invalid hook procedure.
	- 1428: Cannot set nonlocal hook without a module handle.
	- 1429: This hook procedure can only be set globally.
	- 1430: The journal hook procedure is already installed.
	- 1431: The hook procedure is not installed.
	- 1432: Invalid message for single-selection list box.
	- 1433: LB_SETCOUNT sent to non-lazy list box.
	- 1434: This list box does not support tab stops.
	- 1435: Cannot destroy object created by another thread.
	- 1436: Child windows cannot have menus.
	- 1437: The window does not have a system menu.
	- 1438: Invalid message box style.
	- 1439: Invalid system-wide (SPI_*) parameter.
	- 1440: Screen already locked.
	- 1441: All handles to windows in a multiple-window position structure must have the same parent.
	- 1442: The window is not a child window.
	- 1443: Invalid GW_* command.
	- 1444: Invalid thread identifier.
	- 1445: Cannot process a message from a window that is not a multiple document interface (MDI) window.
	- 1446: Popup menu already active.
	- 1447: The window does not have scroll bars.
	- 1448: Scroll bar range cannot be greater than MAXLONG.
	- 1449: Cannot show or remove the window in the way specified.
	- 1450: Insufficient system resources exist to complete the requested service.
	- 1451: Insufficient system resources exist to complete the requested service.
	- 1452: Insufficient system resources exist to complete the requested service.
	- 1453: Insufficient quota to complete the requested service.
	- 1454: Insufficient quota to complete the requested service.
	- 1455: The paging file is too small for this operation to complete.
	- 1456: A menu item was not found.
	- 1457: Invalid keyboard layout handle.
	- 1458: Hook type not allowed.
	- 1459: This operation requires an interactive window station.
	- 1460: This operation returned because the timeout period expired.
	- 1461: Invalid monitor handle.
	- 1462: Incorrect size argument.
	- 1463: The symbolic link cannot be followed because its type is disabled.
	- 1464: This application does not support the current operation on symbolic links.
	- 1465: Windows was unable to parse the requested XML data.
	- 1466: An error was encountered while processing an XML digital signature.
	- 1467: This application must be restarted.
	- 1468: The caller made the connection request in the wrong routing compartment.
	- 1469: There was an AuthIP failure when attempting to connect to the remote host.
	- 1470: Insufficient NVRAM resources exist to complete the requested service. A reboot might be required.
	- 1471: Unable to finish the requested operation because the specified process is not a GUI process.
	- 1500: The event log file is corrupted.
	- 1501: No event log file could be opened, so the event logging service did not start.
	- 1502: The event log file is full.
	- 1503: The event log file has changed between read operations.
	- 1504: The specified Job already has a container assigned to it.
	- 1505: The specified Job does not have a container assigned to it.
	- 1550: The specified task name is invalid.
	- 1551: The specified task index is invalid.
	- 1552: The specified thread is already joining a task.
	- 1601: The Windows Installer Service could not be accessed. This can occur if the Windows Installer is not correctly installed. Contact your support personnel for assistance.
	- 1602: User cancelled installation.
	- 1603: Fatal error during installation.
	- 1604: Installation suspended, incomplete.
	- 1605: This action is only valid for products that are currently installed.
	- 1606: Feature ID not registered.
	- 1607: Component ID not registered.
	- 1608: Unknown property.
	- 1609: Handle is in an invalid state.
	- 1610: The configuration data for this product is corrupt. Contact your support personnel.
	- 1611: Component qualifier not present.
	- 1612: The installation source for this product is not available. Verify that the source exists and that you can access it.
	- 1613: This installation package cannot be installed by the Windows Installer service. You must install a Windows service pack that contains a newer version of the Windows Installer service.
	- 1614: Product is uninstalled.
	- 1615: SQL query syntax invalid or unsupported.
	- 1616: Record field does not exist.
	- 1617: The device has been removed.
	- 1618: Another installation is already in progress. Complete that installation before proceeding with this install.
	- 1619: This installation package could not be opened. Verify that the package exists and that you can access it, or contact the application vendor to verify that this is a valid Windows Installer package.
	- 1620: This installation package could not be opened. Contact the application vendor to verify that this is a valid Windows Installer package.
	- 1621: There was an error starting the Windows Installer service user interface. Contact your support personnel.
	- 1622: Error opening installation log file. Verify that the specified log file location exists and that you can write to it.
	- 1623: The language of this installation package is not supported by your system.
	- 1624: Error applying transforms. Verify that the specified transform paths are valid.
	- 1625: This installation is forbidden by system policy. Contact your system administrator.
	- 1626: Function could not be executed.
	- 1627: Function failed during execution.
	- 1628: Invalid or unknown table specified.
	- 1629: Data supplied is of wrong type.
	- 1630: Data of this type is not supported.
	- 1631: The Windows Installer service failed to start. Contact your support personnel.
	- 1632: The Temp folder is on a drive that is full or is inaccessible. Free up space on the drive or verify that you have write permission on the Temp folder.
	- 1633: This installation package is not supported by this processor type. Contact your product vendor.
	- 1634: Component not used on this computer.
	- 1635: This update package could not be opened. Verify that the update package exists and that you can access it, or contact the application vendor to verify that this is a valid Windows Installer update package.
	- 1636: This update package could not be opened. Contact the application vendor to verify that this is a valid Windows Installer update package.
	- 1637: This update package cannot be processed by the Windows Installer service. You must install a Windows service pack that contains a newer version of the Windows Installer service.
	- 1638: Another version of this product is already installed. Installation of this version cannot continue. To configure or remove the existing version of this product, use Add/Remove Programs on the Control Panel.
	- 1639: Invalid command line argument. Consult the Windows Installer SDK for detailed command line help.
	- 1640: Only administrators have permission to add, remove, or configure server software during a Terminal services remote session. If you want to install or configure software on the server, contact your network administrator.
	- 1641: The requested operation completed successfully. The system will be restarted so the changes can take effect.
	- 1642: The upgrade cannot be installed by the Windows Installer service because the program to be upgraded may be missing, or the upgrade may update a different version of the program. Verify that the program to be upgraded exists on your computer and that you have the correct upgrade.
	- 1643: The update package is not permitted by software restriction policy.
	- 1644: One or more customizations are not permitted by software restriction policy.
	- 1645: The Windows Installer does not permit installation from a Remote Desktop Connection.
	- 1646: Uninstallation of the update package is not supported.
	- 1647: The update is not applied to this product.
	- 1648: No valid sequence could be found for the set of updates.
	- 1649: Update removal was disallowed by policy.
	- 1650: The XML update data is invalid.
	- 1651: Windows Installer does not permit updating of managed advertised products. At least one feature of the product must be installed before applying the update.
	- 1652: The Windows Installer service is not accessible in Safe Mode. Please try again when your computer is not in Safe Mode or you can use System Restore to return your machine to a previous good state.
	- 1653: A fail fast exception occurred. Exception handlers will not be invoked and the process will be terminated immediately.
	- 1654: The app that you are trying to run is not supported on this version of Windows.
	- 1655: The operation was blocked as the process prohibits dynamic code generation.
	- 1656: The objects are not identical.
	- 1657: The specified image file was blocked from loading because it does not enable a feature required by the process: Control Flow Guard.
	- 1660: The thread context could not be updated because this has been restricted for the process.
	- 1661: An invalid cross-partition private file/section access was attempted.
	- 1662: A return address hijack is being attempted. This is supported by the operating system when user-mode shadow stacks are enabled.
	- 1700: The string binding is invalid.
	- 1701: The binding handle is not the correct type.
	- 1702: The binding handle is invalid.
	- 1703: The RPC protocol sequence is not supported.
	- 1704: The RPC protocol sequence is invalid.
	- 1705: The string universal unique identifier (UUID) is invalid.
	- 1706: The endpoint format is invalid.
	- 1707: The network address is invalid.
	- 1708: No endpoint was found.
	- 1709: The timeout value is invalid.
	- 1710: The object universal unique identifier (UUID) was not found.
	- 1711: The object universal unique identifier (UUID) has already been registered.
	- 1712: The type universal unique identifier (UUID) has already been registered.
	- 1713: The RPC server is already listening.
	- 1714: No protocol sequences have been registered.
	- 1715: The RPC server is not listening.
	- 1716: The manager type is unknown.
	- 1717: The interface is unknown.
	- 1718: There are no bindings.
	- 1719: There are no protocol sequences.
	- 1720: The endpoint cannot be created.
	- 1721: Not enough resources are available to complete this operation.
	- 1722: The RPC server is unavailable.
	- 1723: The RPC server is too busy to complete this operation.
	- 1724: The network options are invalid.
	- 1725: There are no remote procedure calls active on this thread.
	- 1726: The remote procedure call failed.
	- 1727: The remote procedure call failed and did not execute.
	- 1728: A remote procedure call (RPC) protocol error occurred.
	- 1729: Access to the HTTP proxy is denied.
	- 1730: The transfer syntax is not supported by the RPC server.
	- 1732: The universal unique identifier (UUID) type is not supported.
	- 1733: The tag is invalid.
	- 1734: The array bounds are invalid.
	- 1735: The binding does not contain an entry name.
	- 1736: The name syntax is invalid.
	- 1737: The name syntax is not supported.
	- 1739: No network address is available to use to construct a universal unique identifier (UUID).
	- 1740: The endpoint is a duplicate.
	- 1741: The authentication type is unknown.
	- 1742: The maximum number of calls is too small.
	- 1743: The string is too long.
	- 1744: The RPC protocol sequence was not found.
	- 1745: The procedure number is out of range.
	- 1746: The binding does not contain any authentication information.
	- 1747: The authentication service is unknown.
	- 1748: The authentication level is unknown.
	- 1749: The security context is invalid.
	- 1750: The authorization service is unknown.
	- 1751: The entry is invalid.
	- 1752: The server endpoint cannot perform the operation.
	- 1753: There are no more endpoints available from the endpoint mapper.
	- 1754: No interfaces have been exported.
	- 1755: The entry name is incomplete.
	- 1756: The version option is invalid.
	- 1757: There are no more members.
	- 1758: There is nothing to unexport.
	- 1759: The interface was not found.
	- 1760: The entry already exists.
	- 1761: The entry is not found.
	- 1762: The name service is unavailable.
	- 1763: The network address family is invalid.
	- 1764: The requested operation is not supported.
	- 1765: No security context is available to allow impersonation.
	- 1766: An internal error occurred in a remote procedure call (RPC).
	- 1767: The RPC server attempted an integer division by zero.
	- 1768: An addressing error occurred in the RPC server.
	- 1769: A floating-point operation at the RPC server caused a division by zero.
	- 1770: A floating-point underflow occurred at the RPC server.
	- 1771: A floating-point overflow occurred at the RPC server.
	- 1772: The list of RPC servers available for the binding of auto handles has been exhausted.
	- 1773: Unable to open the character translation table file.
	- 1774: The file containing the character translation table has fewer than 512 bytes.
	- 1775: A null context handle was passed from the client to the host during a remote procedure call.
	- 1777: The context handle changed during a remote procedure call.
	- 1778: The binding handles passed to a remote procedure call do not match.
	- 1779: The stub is unable to get the remote procedure call handle.
	- 1780: A null reference pointer was passed to the stub.
	- 1781: The enumeration value is out of range.
	- 1782: The byte count is too small.
	- 1783: The stub received bad data.
	- 1784: The supplied user buffer is not valid for the requested operation.
	- 1785: The disk media is not recognized. It may not be formatted.
	- 1786: The workstation does not have a trust secret.
	- 1787: The security database on the server does not have a computer account for this workstation trust relationship.
	- 1788: The trust relationship between the primary domain and the trusted domain failed.
	- 1789: The trust relationship between this workstation and the primary domain failed.
	- 1790: The network logon failed.
	- 1791: A remote procedure call is already in progress for this thread.
	- 1792: An attempt was made to logon, but the network logon service was not started.
	- 1793: The user's account has expired.
	- 1794: The redirector is in use and cannot be unloaded.
	- 1795: The specified printer driver is already installed.
	- 1796: The specified port is unknown.
	- 1797: The printer driver is unknown.
	- 1798: The print processor is unknown.
	- 1799: The specified separator file is invalid.
	- 1800: The specified priority is invalid.
	- 1801: The printer name is invalid.
	- 1802: The printer already exists.
	- 1803: The printer command is invalid.
	- 1804: The specified datatype is invalid.
	- 1805: The environment specified is invalid.
	- 1806: There are no more bindings.
	- 1807: The account used is an interdomain trust account. Use your global user account or local user account to access this server.
	- 1808: The account used is a computer account. Use your global user account or local user account to access this server.
	- 1809: The account used is a server trust account. Use your global user account or local user account to access this server.
	- 1810: The name or security ID (SID) of the domain specified is inconsistent with the trust information for that domain.
	- 1811: The server is in use and cannot be unloaded.
	- 1812: The specified image file did not contain a resource section.
	- 1813: The specified resource type cannot be found in the image file.
	- 1814: The specified resource name cannot be found in the image file.
	- 1815: The specified resource language ID cannot be found in the image file.
	- 1816: Not enough quota is available to process this command.
	- 1817: No interfaces have been registered.
	- 1818: The remote procedure call was cancelled.
	- 1819: The binding handle does not contain all required information.
	- 1820: A communications failure occurred during a remote procedure call.
	- 1821: The requested authentication level is not supported.
	- 1822: No principal name registered.
	- 1823: The error specified is not a valid Windows RPC error code.
	- 1824: A UUID that is valid only on this computer has been allocated.
	- 1825: A security package specific error occurred.
	- 1826: Thread is not canceled.
	- 1827: Invalid operation on the encoding/decoding handle.
	- 1828: Incompatible version of the serializing package.
	- 1829: Incompatible version of the RPC stub.
	- 1830: The RPC pipe object is invalid or corrupted.
	- 1831: An invalid operation was attempted on an RPC pipe object.
	- 1832: Unsupported RPC pipe version.
	- 1833: HTTP proxy server rejected the connection because the cookie authentication failed.
	- 1834: The RPC server is suspended, and could not be resumed for this request. The call did not execute.
	- 1835: The RPC call contains too many handles to be transmitted in a single request.
	- 1836: The RPC call contains a handle that differs from the declared handle type.
	- 1898: The group member was not found.
	- 1899: The endpoint mapper database entry could not be created.
	- 1900: The object universal unique identifier (UUID) is the nil UUID.
	- 1901: The specified time is invalid.
	- 1902: The specified form name is invalid.
	- 1903: The specified form size is invalid.
	- 1904: The specified printer handle is already being waited on
	- 1905: The specified printer has been deleted.
	- 1906: The state of the printer is invalid.
	- 1907: The user's password must be changed before signing in.
	- 1908: Could not find the domain controller for this domain.
	- 1909: The referenced account is currently locked out and may not be logged on to.
	- 1910: The object exporter specified was not found.
	- 1911: The object specified was not found.
	- 1912: The object resolver set specified was not found.
	- 1913: Some data remains to be sent in the request buffer.
	- 1914: Invalid asynchronous remote procedure call handle.
	- 1915: Invalid asynchronous RPC call handle for this operation.
	- 1916: The RPC pipe object has already been closed.
	- 1917: The RPC call completed before all pipes were processed.
	- 1918: No more data is available from the RPC pipe.
	- 1919: No site name is available for this machine.
	- 1920: The file cannot be accessed by the system.
	- 1921: The name of the file cannot be resolved by the system.
	- 1922: The entry is not of the expected type.
	- 1923: Not all object UUIDs could be exported to the specified entry.
	- 1924: Interface could not be exported to the specified entry.
	- 1925: The specified profile entry could not be added.
	- 1926: The specified profile element could not be added.
	- 1927: The specified profile element could not be removed.
	- 1928: The group element could not be added.
	- 1929: The group element could not be removed.
	- 1930: The printer driver is not compatible with a policy enabled on your computer that blocks NT 4.0 drivers.
	- 1931: The context has expired and can no longer be used.
	- 1932: The current user's delegated trust creation quota has been exceeded.
	- 1933: The total delegated trust creation quota has been exceeded.
	- 1934: The current user's delegated trust deletion quota has been exceeded.
	- 1935: The computer you are signing into is protected by an authentication firewall. The specified account is not allowed to authenticate to the computer.
	- 1936: Remote connections to the Print Spooler are blocked by a policy set on your machine.
	- 1937: Authentication failed because NTLM authentication has been disabled.
	- 1938: Logon Failure: EAS policy requires that the user change their password before this operation can be performed.
	- 1939: An administrator has restricted sign in. To sign in, make sure your device is connected to the Internet, and have your administrator sign in first.
	- 2000: The pixel format is invalid.
	- 2001: The specified driver is invalid.
	- 2002: The window style or class attribute is invalid for this operation.
	- 2003: The requested metafile operation is not supported.
	- 2004: The requested transformation operation is not supported.
	- 2005: The requested clipping operation is not supported.
	- 2010: The specified color management module is invalid.
	- 2011: The specified color profile is invalid.
	- 2012: The specified tag was not found.
	- 2013: A required tag is not present.
	- 2014: The specified tag is already present.
	- 2015: The specified color profile is not associated with the specified device.
	- 2016: The specified color profile was not found.
	- 2017: The specified color space is invalid.
	- 2018: Image Color Management is not enabled.
	- 2019: There was an error while deleting the color transform.
	- 2020: The specified color transform is invalid.
	- 2021: The specified transform does not match the bitmap's color space.
	- 2022: The specified named color index is not present in the profile.
	- 2023: The specified profile is intended for a device of a different type than the specified device.
	- 2102: The workstation driver is not installed.
	- 2103: The server could not be located.
	- 2104: An internal error occurred.  The network cannot access a shared memory segment.
	- 2105: A network resource shortage occurred .
	- 2106: This operation is not supported on workstations.
	- 2107: The device is not connected.
	- 2108: The network connection was made successfully, but the user had to be prompted for a password other than the one originally specified.
	- 2109: The network connection was made successfully using default credentials.
	- 2114: The Server service is not started.
	- 2115: The queue is empty.
	- 2116: The device or directory does not exist.
	- 2117: The operation is invalid on a redirected resource.
	- 2118: The name has already been shared.
	- 2119: The server is currently out of the requested resource.
	- 2121: Requested addition of items exceeds the maximum allowed.
	- 2122: The Peer service supports only two simultaneous users.
	- 2123: The API return buffer is too small.
	- 2127: A remote API error occurred.
	- 2131: An error occurred when opening or reading the configuration file.
	- 2136: A general network error occurred.
	- 2137: The Workstation service is in an inconsistent state. Restart the computer before restarting the Workstation service.
	- 2138: The Workstation service has not been started.
	- 2139: The requested information is not available.
	- 2140: An internal Windows error occurred.
	- 2141: The server is not configured for transactions.
	- 2142: The requested API is not supported on the remote server.
	- 2143: The event name is invalid.
	- 2144: The computer name already exists on the network. Change it and restart the computer.
	- 2146: The specified component could not be found in the configuration information.
	- 2147: The specified parameter could not be found in the configuration information.
	- 2149: A line in the configuration file is too long.
	- 2150: The printer does not exist.
	- 2151: The print job does not exist.
	- 2152: The printer destination cannot be found.
	- 2153: The printer destination already exists.
	- 2154: The printer queue already exists.
	- 2155: No more printers can be added.
	- 2156: No more print jobs can be added.
	- 2157: No more printer destinations can be added.
	- 2158: This printer destination is idle and cannot accept control operations.
	- 2159: This printer destination request contains an invalid control function.
	- 2160: The print processor is not responding.
	- 2161: The spooler is not running.
	- 2162: This operation cannot be performed on the print destination in its current state.
	- 2163: This operation cannot be performed on the printer queue in its current state.
	- 2164: This operation cannot be performed on the print job in its current state.
	- 2165: A spooler memory allocation failure occurred.
	- 2166: The device driver does not exist.
	- 2167: The data type is not supported by the print processor.
	- 2168: The print processor is not installed.
	- 2180: The service database is locked.
	- 2181: The service table is full.
	- 2182: The requested service has already been started.
	- 2183: The service does not respond to control actions.
	- 2184: The service has not been started.
	- 2185: The service name is invalid.
	- 2186: The service is not responding to the control function.
	- 2187: The service control is busy.
	- 2188: The configuration file contains an invalid service program name.
	- 2189: The service could not be controlled in its present state.
	- 2190: The service ended abnormally.
	- 2191: The requested pause, continue, or stop is not valid for this service.
	- 2192: The service control dispatcher could not find the service name in the dispatch table.
	- 2193: The service control dispatcher pipe read failed.
	- 2194: A thread for the new service could not be created.
	- 2200: This workstation is already logged on to the local-area network.
	- 2201: The workstation is not logged on to the local-area network.
	- 2202: The specified username is invalid.
	- 2203: The password parameter is invalid.
	- 2204: The logon processor did not add the message alias.
	- 2205: The logon processor did not add the message alias.
	- 2206: The logoff processor did not delete the message alias.
	- 2207: The logoff processor did not delete the message alias.
	- 2209: Network logons are paused.
	- 2210: A centralized logon-server conflict occurred.
	- 2211: The server is configured without a valid user path.
	- 2212: An error occurred while loading or running the logon script.
	- 2214: The logon server was not specified.  Your computer will be logged on as STANDALONE.
	- 2215: The logon server could not be found.
	- 2216: There is already a logon domain for this computer.
	- 2217: The logon server could not validate the logon.
	- 2219: The security database could not be found.
	- 2220: The group name could not be found.
	- 2221: The user name could not be found.
	- 2222: The resource name could not be found.
	- 2223: The group already exists.
	- 2224: The account already exists.
	- 2225: The resource permission list already exists.
	- 2226: This operation is only allowed on the primary domain controller of the domain.
	- 2227: The security database has not been started.
	- 2228: There are too many names in the user accounts database.
	- 2229: A disk I/O failure occurred.
	- 2230: The limit of 64 entries per resource was exceeded.
	- 2231: Deleting a user with a session is not allowed.
	- 2232: The parent directory could not be located.
	- 2233: Unable to add to the security database session cache segment.
	- 2234: This operation is not allowed on this special group.
	- 2235: This user is not cached in user accounts database session cache.
	- 2236: The user already belongs to this group.
	- 2237: The user does not belong to this group.
	- 2238: This user account is undefined.
	- 2239: This user account has expired.
	- 2240: The user is not allowed to log on from this workstation.
	- 2241: The user is not allowed to log on at this time.
	- 2242: The password of this user has expired.
	- 2243: The password of this user cannot change.
	- 2244: This password cannot be used now.
	- 2245: The password does not meet the password policy requirements. Check the minimum password length, password complexity and password history requirements.
	- 2246: The password of this user is too recent to change.
	- 2247: The security database is corrupted.
	- 2248: No updates are necessary to this replicant network/local security database.
	- 2249: This replicant database is outdated; synchronization is required.
	- 2250: This network connection does not exist.
	- 2251: This asg_type is invalid.
	- 2252: This device is currently being shared.
	- 2253: The user name may not be same as computer name.
	- 2270: The computer name could not be added as a message alias.  The name may already exist on the network.
	- 2271: The Messenger service is already started.
	- 2272: The Messenger service failed to start.
	- 2273: The message alias could not be found on the network.
	- 2274: This message alias has already been forwarded.
	- 2275: This message alias has been added but is still forwarded.
	- 2276: This message alias already exists locally.
	- 2277: The maximum number of added message aliases has been exceeded.
	- 2278: The computer name could not be deleted.
	- 2279: Messages cannot be forwarded back to the same workstation.
	- 2280: An error occurred in the domain message processor.
	- 2281: The message was sent, but the recipient has paused the Messenger service.
	- 2282: The message was sent but not received.
	- 2283: The message alias is currently in use. Try again later.
	- 2284: The Messenger service has not been started.
	- 2285: The name is not on the local computer.
	- 2286: The forwarded message alias could not be found on the network.
	- 2287: The message alias table on the remote station is full.
	- 2288: Messages for this alias are not currently being forwarded.
	- 2289: The broadcast message was truncated.
	- 2294: This is an invalid device name.
	- 2295: A write fault occurred.
	- 2297: A duplicate message alias exists on the network.
	- 2298: This message alias will be deleted later.
	- 2299: The message alias was not successfully deleted from all networks.
	- 2300: This operation is not supported on computers with multiple networks.
	- 2310: This shared resource does not exist.
	- 2311: This device is not shared.
	- 2312: A session does not exist with that computer name.
	- 2314: There is not an open file with that identification number.
	- 2315: A failure occurred when executing a remote administration command.
	- 2316: A failure occurred when opening a remote temporary file.
	- 2317: The data returned from a remote administration command has been truncated to 64K.
	- 2318: This device cannot be shared as both a spooled and a non-spooled resource.
	- 2319: The information in the list of servers may be incorrect.
	- 2320: The computer is not active in this domain.
	- 2321: The share must be removed from the Distributed File System before it can be deleted.
	- 2331: The operation is invalid for this device.
	- 2332: This device cannot be shared.
	- 2333: This device was not open.
	- 2334: This device name list is invalid.
	- 2335: The queue priority is invalid.
	- 2337: There are no shared communication devices.
	- 2338: The queue you specified does not exist.
	- 2340: This list of devices is invalid.
	- 2341: The requested device is invalid.
	- 2342: This device is already in use by the spooler.
	- 2343: This device is already in use as a communication device.
	- 2351: This computer name is invalid.
	- 2354: The string and prefix specified are too long.
	- 2356: This path component is invalid.
	- 2357: Could not determine the type of input.
	- 2362: The buffer for types is not big enough.
	- 2370: Profile files cannot exceed 64K.
	- 2371: The start offset is out of range.
	- 2372: The system cannot delete current connections to network resources.
	- 2373: The system was unable to parse the command line in this file.
	- 2374: An error occurred while loading the profile file.
	- 2375: Errors occurred while saving the profile file.  The profile was partially saved.
	- 2377: Log file %1 is full.
	- 2378: This log file has changed between reads.
	- 2379: Log file %1 is corrupt.
	- 2380: The source path cannot be a directory.
	- 2381: The source path is illegal.
	- 2382: The destination path is illegal.
	- 2383: The source and destination paths are on different servers.
	- 2385: The Run server you requested is paused.
	- 2389: An error occurred when communicating with a Run server.
	- 2391: An error occurred when starting a background process.
	- 2392: The shared resource you are connected to could not be found.
	- 2400: The LAN adapter number is invalid.
	- 2401: This network connection has files open or requests pending.
	- 2402: Active connections still exist.
	- 2403: This share name or password is invalid.
	- 2404: The device is in use by an active process and cannot be disconnected.
	- 2405: The drive letter is in use locally.
	- 2430: The specified client is already registered for the specified event.
	- 2431: The alert table is full.
	- 2432: An invalid or nonexistent alert name was raised.
	- 2433: The alert recipient is invalid.
	- 2434: A user's session with this server has been deleted
because the user's logon hours are no longer valid.
	- 2440: The log file does not contain the requested record number.
	- 2450: The user accounts database is not configured correctly.
	- 2451: This operation is not permitted when the Netlogon service is running.
	- 2452: This operation is not allowed on the last administrative account.
	- 2453: Could not find domain controller for this domain.
	- 2454: Could not set logon information for this user.
	- 2455: The Netlogon service has not been started.
	- 2456: Unable to add to the user accounts database.
	- 2457: This server's clock is not synchronized with the primary domain controller's clock.
	- 2458: A password mismatch has been detected.
	- 2460: The server identification does not specify a valid server.
	- 2461: The session identification does not specify a valid session.
	- 2462: The connection identification does not specify a valid connection.
	- 2463: There is no space for another entry in the table of available servers.
	- 2464: The server has reached the maximum number of sessions it supports.
	- 2465: The server has reached the maximum number of connections it supports.
	- 2466: The server cannot open more files because it has reached its maximum number.
	- 2467: There are no alternate servers registered on this server.
	- 2470: Try down-level (remote admin protocol) version of API instead.
	- 2480: The UPS driver could not be accessed by the UPS service.
	- 2481: The UPS service is not configured correctly.
	- 2482: The UPS service could not access the specified Comm Port.
	- 2483: The UPS indicated a line fail or low battery situation. Service not started.
	- 2484: The UPS service failed to perform a system shut down.
	- 2500: The program below returned an MS-DOS error code:
	- 2501: The program below needs more memory:
	- 2502: The program below called an unsupported MS-DOS function:
	- 2503: The workstation failed to boot.
	- 2504: The file below is corrupt.
	- 2505: No loader is specified in the boot-block definition file.
	- 2506: NetBIOS returned an error: The NCB and SMB are dumped above.
	- 2507: A disk I/O error occurred.
	- 2508: Image parameter substitution failed.
	- 2509: Too many image parameters cross disk sector boundaries.
	- 2510: The image was not generated from an MS-DOS diskette formatted with /S.
	- 2511: Remote boot will be restarted later.
	- 2512: The call to the Remoteboot server failed.
	- 2513: Cannot connect to the Remoteboot server.
	- 2514: Cannot open image file on the Remoteboot server.
	- 2515: Connecting to the Remoteboot server...
	- 2516: Connecting to the Remoteboot server...
	- 2517: Remote boot service was stopped; check the error log for the cause of the problem.
	- 2518: Remote boot startup failed; check the error log for the cause of the problem.
	- 2519: A second connection to a Remoteboot resource is not allowed.
	- 2550: The browser service was configured with MaintainServerList=No.
	- 2610: Service failed to start since none of the network adapters started with this service.
	- 2611: Service failed to start due to bad startup information in the registry.
	- 2612: Service failed to start because its database is absent or corrupt.
	- 2613: Service failed to start because RPLFILES share is absent.
	- 2614: Service failed to start because RPLUSER group is absent.
	- 2615: Cannot enumerate service records.
	- 2616: Workstation record information has been corrupted.
	- 2617: Workstation record was not found.
	- 2618: Workstation name is in use by some other workstation.
	- 2619: Profile record information has been corrupted.
	- 2620: Profile record was not found.
	- 2621: Profile name is in use by some other profile.
	- 2622: There are workstations using this profile.
	- 2623: Configuration record information has been corrupted.
	- 2624: Configuration record was not found.
	- 2625: Adapter id record information has been corrupted.
	- 2626: An internal service error has occurred.
	- 2627: Vendor id record information has been corrupted.
	- 2628: Boot block record information has been corrupted.
	- 2629: The user account for this workstation record is missing.
	- 2630: The RPLUSER local group could not be found.
	- 2631: Boot block record was not found.
	- 2632: Chosen profile is incompatible with this workstation.
	- 2633: Chosen network adapter id is in use by some other workstation.
	- 2634: There are profiles using this configuration.
	- 2635: There are workstations, profiles or configurations using this boot block.
	- 2636: Service failed to backup Remoteboot database.
	- 2637: Adapter record was not found.
	- 2638: Vendor record was not found.
	- 2639: Vendor name is in use by some other vendor record.
	- 2640: (boot name, vendor id) is in use by some other boot block record.
	- 2641: Configuration name is in use by some other configuration.
	- 2660: The internal database maintained by the DFS service is corrupt
	- 2661: One of the records in the internal DFS database is corrupt
	- 2662: There is no DFS name whose entry path matches the input Entry Path
	- 2663: A root or link with the given name already exists
	- 2664: The server share specified is already shared in the DFS
	- 2665: The indicated server share does not support the indicated DFS namespace
	- 2666: The operation is not valid on this portion of the namespace
	- 2667: The operation is not valid on this portion of the namespace
	- 2668: The operation is ambiguous because the link has multiple servers
	- 2669: Unable to create a link
	- 2670: The server is not DFS Aware
	- 2671: The specified rename target path is invalid
	- 2672: The specified DFS link is offline
	- 2673: The specified server is not a server for this link
	- 2674: A cycle in the DFS name was detected
	- 2675: The operation is not supported on a server-based DFS
	- 2676: This link is already supported by the specified server-share
	- 2677: Can't remove the last server-share supporting this root or link
	- 2678: The operation is not supported for an Inter-DFS link
	- 2679: The internal state of the DFS Service has become inconsistent
	- 2680: The DFS Service has been installed on the specified server
	- 2681: The DFS data being reconciled is identical
	- 2682: The DFS root cannot be deleted - Uninstall DFS if required
	- 2683: A child or parent directory of the share is already in a DFS
	- 2690: DFS internal error
	- 2691: This machine is already joined to a domain.
	- 2692: This machine is not currently joined to a domain.
	- 2693: This machine is a domain controller and cannot be unjoined from a domain.
	- 2694: The destination domain controller does not support creating machine accounts in OUs.
	- 2695: The specified workgroup name is invalid.
	- 2696: The specified computer name is incompatible with the default language used on the domain controller.
	- 2697: The specified computer account could not be found. Contact an administrator to verify the account is in the domain. If the account has been deleted unjoin, reboot, and rejoin the domain.
	- 2698: This version of Windows cannot be joined to a domain.
	- 2699: An attempt to resolve the DNS name of a domain controller in the domain being joined has failed.  Please verify this client is configured to reach a DNS server that can resolve DNS names in the target domain. For information about network troubleshooting, see Windows Help.
	- 2700: This device is joined to Azure AD. To join an Active Directory domain, you must first go to settings and choose to disconnect your device from your work or school.
	- 2701: Password must change at next logon
	- 2702: Account is locked out
	- 2703: Password is too long
	- 2704: Password doesn't meet the complexity policy
	- 2705: Password doesn't meet the requirements of the filter dll's
	- 2709: Offline join completion information was not found.
	- 2710: The offline join completion information was bad.
	- 2711: Unable to create offline join information. Please ensure you have access to the specified path location and permissions to modify its contents. Running as an elevated administrator may be required.
	- 2712: The domain join info being saved was incomplete or bad.
	- 2713: Offline join operation successfully completed but a restart is needed.
	- 2714: There was no offline join operation pending.
	- 2715: Unable to set one or more requested machine or domain name values on the local computer.
	- 2716: Could not verify the current machine's hostname against the saved value in the join completion information.
	- 2717: Unable to load the specified offline registry hive. Please ensure you have access to the specified path location and permissions to modify its contents. Running as an elevated administrator may be required.
	- 2718: The minimum session security requirements for this operation were not met.
	- 2719: Computer account provisioning blob version is not supported.
	- 2720: The specified domain controller does not meet the version requirement for this operation. Please select a domain controller capable of issuing claims.
	- 2721: This operation requires a domain controller which supports LDAP. Please select an LDAP-capable domain controller.
	- 2722: A domain controller which meets the version requirement for this operation could not be located. Please ensure that a domain controller capable of issuing claims is available.
	- 2723: The Windows version of the specified image does not support provisioning.
	- 2724: The machine name is blocked from joining the domain.
	- 2725: The domain controller does not meet the version requirement for this operation. See http://go.microsoft.com/fwlink/?LinkId=294288 for more information.
	- 2726: The local machine does not allow querying of LSA secrets in plain-text.
	- 2727: Unable to leave the Azure AD domain that this machine is joined to. Check the event log for detailed error information.
	- 2728: Unable to update hostname in Azure AD. Check the event log for detailed error information.
	- 2729: The hostname is already taken by another device.
	- 2730: The hostname is too long.
	- 2731: Too many hostnames specified for the device.
	- 2732: An account with the same name exists in Active Directory. Re-using the account was blocked by security policy.
	- 2999: This is the last error in NERR range.
	- 3000: The specified print monitor is unknown.
	- 3001: The specified printer driver is currently in use.
	- 3002: The spool file was not found.
	- 3003: A StartDocPrinter call was not issued.
	- 3004: An AddJob call was not issued.
	- 3005: The specified print processor has already been installed.
	- 3006: The specified print monitor has already been installed.
	- 3007: The specified print monitor does not have the required functions.
	- 3008: The specified print monitor is currently in use.
	- 3009: The requested operation is not allowed when there are jobs queued to the printer.
	- 3010: The requested operation is successful. Changes will not be effective until the system is rebooted.
	- 3011: The requested operation is successful. Changes will not be effective until the service is restarted.
	- 3012: No printers were found.
	- 3013: The printer driver is known to be unreliable.
	- 3014: The printer driver is known to harm the system.
	- 3015: The specified printer driver package is currently in use.
	- 3016: Unable to find a core driver package that is required by the printer driver package.
	- 3017: The requested operation failed. A system reboot is required to roll back changes made.
	- 3018: The requested operation failed. A system reboot has been initiated to roll back changes made.
	- 3019: The specified printer driver was not found on the system and needs to be downloaded.
	- 3020: The requested print job has failed to print. A print system update requires the job to be resubmitted.
	- 3021: The printer driver does not contain a valid manifest, or contains too many manifests.
	- 3022: The specified printer cannot be shared.
	- 3023: The requested function requires SMB1 to be present and enabled.
	- 3024: The user canceled the authentication prompt to a remote server. 
	- 3025: A defective sector on drive %1 has been replaced (hotfixed).
No data was lost.  You should run CHKDSK soon to restore full
performance and replenish the volume's spare sector pool.
The hotfix occurred while processing a remote request.
	- 3026: A disk error occurred on the HPFS volume in drive %1.
The error occurred while processing a remote request.
	- 3027: The user accounts database (NET.ACC) is corrupted.  The local security
system is replacing the corrupted NET.ACC with the backup
made on %1 at %2.
Any updates made to the database after this time are lost.
	- 3028: The user accounts database (NET.ACC) is missing. The local
security system is restoring the backup database
made on %1 at %2.
Any updates made to the database after this time are lost.
	- 3029: Local security could not be started because the user accounts database
(NET.ACC) was missing or corrupted, and no usable backup
database was present.
THE SYSTEM IS NOT SECURE.
	- 3030: The server cannot export directory %1, to client %2.
It is exported from another server.
	- 3031: The replication server could not update directory %2 from the source
on %3 due to error %1.
	- 3032: Master %1 did not send an update notice for directory %2 at the expected
time.
	- 3033: User %1 has exceeded account limitation %2 on server %3.
	- 3034: The primary domain controller for domain %1 failed.
	- 3035: Failed to authenticate with %2, a Windows Domain Controller for
domain %1.
	- 3036: The replicator attempted to log on at %2 as %1 and failed.
	- 3037: @I *LOGON HOURS	- 3038: Replicator could not access %2
on %3 due to system error %1.
	- 3039: Replicator limit for files in a directory has been exceeded.
	- 3040: Replicator limit for tree depth has been exceeded.
	- 3041: The replicator cannot update directory %1. It has tree integrity
and is the current directory for some process.
	- 3042: Network error %1 occurred.
	- 3045: System error %1 occurred.
	- 3046: Cannot log on. User is currently logged on and argument TRYUSER
is set to NO.
	- 3047: IMPORT path %1 cannot be found.
	- 3048: EXPORT path %1 cannot be found.
	- 3049: Replicated data has changed in directory %1.
	- 3050: The operation was paused.
	- 3051: The Registry or the information you just typed includes an illegal
value for "%1".
	- 3052: The required parameter was not provided on the command
line or in the configuration file.
	- 3053: LAN Manager does not recognize "%1" as a valid option.
	- 3054: A request for resource could not be satisfied.
	- 3055: A problem exists with the system configuration.
	- 3056: A system error has occurred.
	- 3057: An internal consistency error has occurred.
	- 3058: The configuration file or the command line has an ambiguous option.
	- 3059: The configuration file or the command line has a duplicate parameter.
	- 3060: The condition supplied for the app execution request was not satisfied, so the request was not performed.
	- 3061: The supplied handle has been invalidated and may not be used for the requested operation.
	- 3062: The supplied host generation has been invalidated and may not be used for the requested operation.
	- 3063: An attempt to register a process failed because the target host was not in a valid state to receive process registrations.
	- 3064: The host is not in a valid state to support the execution request.
	- 3065: The operation was not completed because a required resource donor was not found for the host.
	- 3066: The operation was not completed because an unexpected host ID was encountered.
	- 3067: The operation was not completed because the specified user was not known to the service.
	- 3068: The application is blocked by app compat policy.
	- 3069: The caller specified wait timed out before the operation completed.
	- 3070: The caller specified wait timed out before the operation completed because a host termination is in queued.
	- 3071: The caller specified wait timed out before the operation completed because a licensing operation is being performed.
	- 3072: The caller specified wait timed out before the operation completed because resources are being acquired.
	- 3073: process
	- 3074: Security Failure.	- 3075: Bad or missing LAN Manager root directory.
	- 3076: The network software is not installed.
	- 3077: The server is not started.
	- 3078: The server cannot access the user accounts database (NET.ACC).
	- 3079: Incompatible files are installed in the LANMAN tree.
	- 3080: Enabling driver verification from volatile command is currently not supported when both CFG and IO are enabled.
	- 3081: Removal of current driver verification is not supported from volatile command.
	- 3082: Enabling driver verification is not supported in safe mode.
	- 3083: Enabling driver verification is not supported from volatile mode in current system.
	- 3084: The specified rule class (a.k.a. flag) is not supported from volatile mode.
	- 3085: The specified driver is protected and volatile verification is currently not supported.
	- 3086: Enabling driver verification is not supported for a driver with  NMI callback(s) registered.
	- 3087: Volatile verification settings cannot be changed when verification is enabled from boot or DIF volatile verification is enabled.
	- 3088: View your error log for details.
	- 3089: Unable to write to this file.
	- 3090: ADDPAK file is corrupted.  Delete LANMAN\NETPROG\ADDPAK.SER
and reapply all ADDPAKs.
	- 3091: The LM386 server cannot be started because CACHE.EXE is not running.
	- 3092: There is no account for this computer in the security database.
	- 3093: This computer is not a member of the group SERVERS.
	- 3094: The group SERVERS is not present in the local security database.
	- 3095: This computer is configured as a member of a workgroup, not as
a member of a domain. The Netlogon service does not need to run in this
configuration.
	- 3096: The primary Domain Controller for this domain could not be located.
	- 3097: This computer is configured to be the primary domain controller of its domain.
However, the computer %1 is currently claiming to be the primary domain controller
of the domain.
	- 3098: The service failed to authenticate with the primary domain controller.
	- 3099: There is a problem with the security database creation date or serial number.
	- 3100: The operation failed because a network software error occurred.
	- 3101: The system ran out of a resource controlled by the %1 option.
	- 3102: The service failed to obtain a long-term lock on the
segment for network control blocks (NCBs). The error code is the data.
	- 3103: The service failed to release the long-term lock on the
segment for network control blocks (NCBs). The error code is the data.
	- 3104: There was an error stopping service %1.
The error code from NetServiceControl is the data.
	- 3105: Initialization failed because of a system execution failure on
path %1. The system error code is the data.
	- 3106: An unexpected network control block (NCB) was received. The NCB is the data.
	- 3107: The network is not started.
	- 3108: A DosDevIoctl or DosFsCtl to NETWKSTA.SYS failed.
The data shown is in this format:
DWORD  approx CS:IP of call to ioctl or fsctl
WORD   error code
WORD   ioctl or fsctl number
	- 3109: Unable to create or open system semaphore %1.
The error code is the data.
	- 3110: Initialization failed because of an open/create error on the
file %1. The system error code is the data.
	- 3111: An unexpected NetBIOS error occurred.
The error code is the data.
	- 3112: An illegal server message block (SMB) was received.
The SMB is the data.
	- 3113: Initialization failed because the requested service %1
could not be started.
	- 3114: Some entries in the error log were lost because of a buffer
overflow.
	- 3120: Initialization parameters controlling resource usage other
than net buffers are sized so that too much memory is needed.
	- 3121: The server cannot increase the size of a memory segment.
	- 3122: Initialization failed because account file %1 is either incorrect
or not present.
	- 3123: Initialization failed because network %1 was not started.
	- 3124: The server failed to start. Either all three chdev
parameters must be zero or all three must be nonzero.
	- 3125: A remote API request was halted due to the following
invalid description string: %1.
	- 3126: The network %1 ran out of network control blocks (NCBs).  You may need to increase NCBs
for this network.  The following information includes the
number of NCBs submitted by the server when this error occurred:
	- 3127: The server cannot create the %1 mailslot needed to send
the ReleaseMemory alert message.  The error received is:
	- 3128: The server failed to register for the ReleaseMemory alert,
with recipient %1. The error code from
NetAlertStart is the data.
	- 3129: The server cannot update the AT schedule file. The file
is corrupted.
	- 3130: The server encountered an error when calling
NetIMakeLMFileName. The error code is the data.
	- 3131: Initialization failed because of a system execution failure on
path %1. There is not enough memory to start the process.
The system error code is the data.
	- 3132: Longterm lock of the server buffers failed.
Check swap disk's free space and restart the system to start the server.
	- 3140: The service has stopped due to repeated consecutive
occurrences of a network control block (NCB) error.  The last bad NCB follows
in raw data.
	- 3141: The Message server has stopped due to a lock on the
Message server shared data segment.
	- 3150: A file system error occurred while opening or writing to the
system message log file %1. Message logging has been
switched off due to the error. The error code is the data.
	- 3151: Unable to display message POPUP due to system VIO call error.
The error code is the data.
	- 3152: An illegal server message block (SMB) was received.  The SMB is the data.
	- 3160: The workstation information segment is bigger than 64K.
The size follows, in DWORD format:
	- 3161: The workstation was unable to get the name-number of the computer.
	- 3162: The workstation could not initialize the Async NetBIOS Thread.
The error code is the data.
	- 3163: The workstation could not open the initial shared segment.
The error code is the data.
	- 3164: The workstation host table is full.
	- 3165: A bad mailslot server message block (SMB) was received.  The SMB is the data.
	- 3166: The workstation encountered an error while trying to start the user accounts database.
The error code is the data.
	- 3167: The workstation encountered an error while responding to an SSI revalidation request.
The function code and the error codes are the data.
	- 3170: The Alerter service had a problem creating the list of
alert recipients.  The error code is %1.
	- 3171: There was an error expanding %1 as a group name. Try
splitting the group into two or more smaller groups.
	- 3172: There was an error sending %2 the alert message -
(
%3 )
The error code is %1.
	- 3173: There was an error in creating or reading the alerter mailslot.
The error code is %1.
	- 3174: The server could not read the AT schedule file.
	- 3175: The server found an invalid AT schedule record.
	- 3176: The server could not find an AT schedule file so it created one.
	- 3177: The server could not access the %1 network with NetBiosOpen.
	- 3178: The AT command processor could not run %1.
	- 3180: WARNING:  Because of a lazy-write error, drive %1 now
contains some corrupted data.  The cache is stopped.
	- 3181: A defective sector on drive %1 has been replaced (hotfixed).
No data was lost.  You should run CHKDSK soon to restore full
performance and replenish the volume's spare sector pool.
The hotfix occurred while processing a remote request.
	- 3182: A disk error occurred on the HPFS volume in drive %1.
The error occurred while processing a remote request.
	- 3183: The user accounts database (NET.ACC) is corrupted.  The local security
system is replacing the corrupted NET.ACC with the backup
made at %1.
Any updates made to the database after this time are lost.
	- 3184: The user accounts database (NET.ACC) is missing.  The local
security system is restoring the backup database
made at %1.
Any updates made to the database made after this time are lost.
	- 3185: Local security could not be started because the user accounts database
(NET.ACC) was missing or corrupted, and no usable backup
database was present.
THE SYSTEM IS NOT SECURE.
	- 3186: Local security could not be started because an error
occurred during initialization. The error code returned is %1.
THE SYSTEM IS NOT SECURE.
	- 3190: The specified driver is not associated with driver object or driver extension.
	- 3191: Verifier's internal data size exceeds the limit of live dump secondary data.
	- 3192: Verification cannot start because an attempt to lock code or data section failed.
	- 3193: DIF volatile verification is not supported for hotpatched driver.
	- 3194: The passed system DIF information is invalid.
	- 3195: DIF volatile verification only supports on loaded drivers.
	- 3196: Currently no plugin is running.
	- 3197: Currently running plugin must be removed before applying a new plugin.
	- 3198: The plugin is not allowed to run in volatile mode.
	- 3199: One or more DDI is not yet supported by DIF.
	- 3204: The server could not create a thread.
The THREADS parameter in the CONFIG.SYS file should be increased.
	- 3205: The server could not close %1.
The file is probably corrupted.
	- 3206: The replicator cannot update directory %1. It has tree integrity
and is the current directory for some process.
	- 3207: The server cannot export directory %1 to client %2.
It is exported from another server.
	- 3208: The replication server could not update directory %2 from the source
on %3 due to error %1.
	- 3209: Master %1 did not send an update notice for directory %2 at the expected
time.
	- 3210: This computer could not authenticate with %2, a Windows domain controller
for domain %1, and therefore this computer might deny logon requests.
This inability to authenticate might be caused by another computer on the
same network using the same name or the password for this computer account
is not recognized. If this message appears again, contact your system
administrator.
	- 3211: The replicator attempted to log on at %2 as %1 and failed.
	- 3212: Network error %1 occurred.
	- 3213: Replicator limit for files in a directory has been exceeded.
	- 3214: Replicator limit for tree depth has been exceeded.
	- 3215: Unrecognized message received in mailslot.
	- 3216: System error %1 occurred.
	- 3217: Cannot log on. User is currently logged on and argument TRYUSER
is set to NO.
	- 3218: IMPORT path %1 cannot be found.
	- 3219: EXPORT path %1 cannot be found.
	- 3220: Replicator failed to update signal file in directory %2 due to
%1 system error.
	- 3221: Disk Fault Tolerance Error
%1
	- 3222: Replicator could not access %2
on %3 due to system error %1.
	- 3223: The primary domain controller for domain %1 has apparently failed.
	- 3224: Changing machine account password for account %1 failed with
the following error: 
%2
	- 3225: An error occurred while updating the logon or logoff information for %1.
	- 3226: An error occurred while synchronizing with primary domain controller %1
	- 3227: The session setup to the Windows Domain Controller %1 for the domain %2
failed because %1 does not support signing or sealing the Netlogon
session.
Either upgrade the Domain controller or set the RequireSignOrSeal
registry entry on this machine to 0.
	- 3230: A power failure was detected at the server.
	- 3231: The UPS service performed server shut down.
	- 3232: The UPS service did not complete execution of the
user specified shut down command file.
	- 3233: The UPS driver could not be opened.  The error code is
the data.
	- 3234: Power has been restored.
	- 3235: There is a problem with a configuration of user specified
shut down command file.
	- 3236: The UPS service failed to execute a user specified shutdown
command file %1.  The error code is the data.
	- 3250: Initialization failed because of an invalid or missing
parameter in the configuration file %1.
	- 3251: Initialization failed because of an invalid line in the
configuration file %1. The invalid line is the data.
	- 3252: Initialization failed because of an error in the configuration
file %1.
	- 3253: The file %1 has been changed after initialization.
The boot-block loading was temporarily terminated.
	- 3254: The files do not fit to the boot-block configuration
file %1. Change the BASE and ORG definitions or the order
of the files.
	- 3255: Initialization failed because the dynamic-link
library %1 returned an incorrect version number.
	- 3256: There was an unrecoverable error in the dynamic-
link library of the service.
	- 3257: The system returned an unexpected error code.
The error code is the data.
	- 3258: The fault-tolerance error log file, LANROOT\LOGS\FT.LOG,
is more than 64K.
	- 3259: The fault-tolerance error-log file, LANROOT\LOGS\FT.LOG, had the
update in progress bit set upon opening, which means that the
system crashed while working on the error log.
	- 3260: This computer has been successfully joined to domain '%1'.
	- 3261: This computer has been successfully joined to workgroup '%1'.
	- 3299: %1 %2 %3 %4 %5 %6 %7 %8 %9.
	- 3301: Remote IPC	- 3302: Remote Admin	- 3303: Logon server share	- 3304: A network error occurred.	- 3400: There is not enough memory to start the Workstation service.
	- 3401: An error occurred when reading the NETWORKS entry in the LANMAN.INI file.
	- 3402: This is an invalid argument: %1.
	- 3403: The %1 NETWORKS entry in the LANMAN.INI file has a
syntax error and will be ignored.
	- 3404: There are too many NETWORKS entries in the LANMAN.INI file.
	- 3406: An error occurred when opening network
device driver %1 = %2.
	- 3407: Device driver %1 sent a bad BiosLinkage response.
	- 3408: The program cannot be used with this operating system.
	- 3409: The redirector is already installed.
	- 3410: Installing NETWKSTA.SYS Version %1.%2.%3  (%4)
	- 3411: There was an error installing NETWKSTA.SYS.
Press ENTER to continue.
	- 3412: Resolver linkage problem.
	- 3413: Your logon time at %1 ends at %2.
Please clean up and log off.
	- 3414: You will be automatically disconnected at %1.
	- 3415: Your logon time at %1 has ended.
	- 3416: Your logon time at %1 ended at %2.
	- 3417: WARNING: You have until %1 to logoff. If you
have not logged off at this time, your session will be
disconnected, and any open files or devices you
have open may lose data.
	- 3418: WARNING: You must log off at %1 now.  You have
two minutes to log off, or you will be disconnected.
	- 3419: You have open files or devices, and a forced
disconnection may cause you to lose data.
	- 3420: Default Share for Internal Use	- 3421: Messenger Service	- 3500: The command completed successfully.
	- 3501: You used an invalid option.
	- 3502: System error %1 has occurred.
	- 3503: The command contains an invalid number of arguments.
	- 3504: The command completed with one or more errors.
	- 3505: You used an option with an invalid value.
	- 3506: The option %1 is unknown.
	- 3507: Option %1 is ambiguous.
	- 3510: A command was used with conflicting switches.
	- 3511: Could not find subprogram %1.
	- 3512: The software requires a newer version of the operating
system.
	- 3513: More data is available than can be returned by Windows.
	- 3514: More help is available by typing NET HELPMSG %1.
	- 3515: This command can be used only on a Windows Domain Controller.
	- 3516: This command cannot be used on a Windows Domain Controller.
	- 3520: These Windows services are started:
	- 3521: The %1 service is not started.
	- 3522: The %1 service is startin	- 3523: The %1 service could not be started.
	- 3524: The %1 service was started successfully.
	- 3525: Stopping the Workstation service also stops the Server service.
	- 3526: The workstation has open files.
	- 3527: The %1 service is stoppin	- 3528: The %1 service could not be stopped.
	- 3529: The %1 service was stopped successfully.
	- 3530: The following services are dependent on the %1 service.
Stopping the %1 service will also stop these services.
	- 3533: The service is starting or stopping.  Please try again later.
	- 3534: The service did not report an error.
	- 3535: An error occurred controlling the device.
	- 3536: The %1 service was continued successfully.
	- 3537: The %1 service was paused successfully.
	- 3538: The %1 service failed to resume.
	- 3539: The %1 service failed to pause.
	- 3540: The %1 service continue is pendin	- 3541: The %1 service pause is pendin	- 3542: %1 was continued successfully.
	- 3543: %1 was paused successfully.
	- 3544: The %1 service has been started by another process and is pending	- 3547: A service specific error occurred: %1.
	- 3660: These workstations have sessions on this server:
	- 3661: These workstations have sessions with open files on this server:
	- 3666: The message alias is forwarded.
	- 3670: You have these remote connections:
	- 3671: Continuing will cancel the connections.
	- 3675: The session from %1 has open files.
	- 3676: New connections will be remembered.
	- 3677: New connections will not be remembered.
	- 3678: An error occurred while saving your profile : Access Denied. The state of your remembered connections has not changed.
	- 3679: An error occurred while reading your profile.
	- 3680: An error occurred while restoring the connection to %1.
	- 3682: No network services are started.
	- 3683: There are no entries in the list.
	- 3688: Users have open files on %1.  Continuing the operation will force the files closed.
	- 3689: The Workstation service is already running. Windows will ignore command options for the workstation.
	- 3691: There are open files and/or incomplete directory searches pending on the connection to %1.
	- 3693: The request will be processed at a domain controller for domain %1.
	- 3694: The shared queue cannot be deleted while a print job is being spooled to the queue.
	- 3695: %1 has a remembered connection to %2.
	- 3710: An error occurred while opening the Help file.
	- 3711: The Help file is empty.
	- 3712: The Help file is corrupted.
	- 3713: Could not find a domain controller for domain %1.
	- 3714: This operation is privileged on systems with earlier
versions of the software.
	- 3716: The device type is unknown.
	- 3717: The log file has been corrupted.
	- 3718: Program filenames must end with .EXE.
	- 3719: A matching share could not be found so nothing was deleted.
	- 3720: A bad value is in the units-per-week field of the user record.
	- 3721: The password is invalid for %1.
	- 3722: An error occurred while sending a message to %1.
	- 3723: The password or user name is invalid for %1.
	- 3725: An error occurred when the share was deleted.
	- 3726: The user name is invalid.
	- 3727: The password is invalid.
	- 3728: The passwords do not match.
	- 3729: Your persistent connections were not all restored.
	- 3730: This is not a valid computer name or domain name.
	- 3732: Default permissions cannot be set for that resource.
	- 3734: A valid password was not entered.
	- 3735: A valid name was not entered.
	- 3736: The resource named cannot be shared.
	- 3737: The permissions string contains invalid permissions.
	- 3738: You can only perform this operation on printers and communication devices.
	- 3742: %1 is an invalid user or group name.
	- 3743: The server is not configured for remote administration.
	- 3752: No users have sessions with this server.
	- 3753: User %1 is not a member of group %2.
	- 3754: User %1 is already a member of group %2.
	- 3755: There is no such user: %1.
	- 3756: This is an invalid response.
	- 3757: No valid response was provided.
	- 3758: The destination list provided does not match the destination list of the printer queue.
	- 3759: Your password cannot be changed until %1.
	- 3760: %1 is not a recognized day of the week.
	- 3761: The time range specified ends before it starts.
	- 3762: %1 is not a recognized hour.
	- 3763: %1 is not a valid specification for minutes.
	- 3764: Time supplied is not exactly on the hour.
	- 3765: 12 and 24 hour time formats may not be mixed.
	- 3766: %1 is not a valid 12-hour suffix.
	- 3767: An illegal date format has been supplied.
	- 3768: An illegal day range has been supplied.
	- 3769: An illegal time range has been supplied.
	- 3770: Arguments to NET USER are invalid. Check the minimum password
length and/or arguments supplied.
	- 3771: The value for ENABLESCRIPT must be YES.
	- 3773: An illegal country/region code has been supplied.
	- 3774: The user was successfully created but could not be added
to the USERS local group.
	- 3775: The user context supplied is invalid.
	- 3776: The dynamic-link library %1 could not be loaded, or an error
occurred while trying to use it.
	- 3777: Sending files is no longer supported.
	- 3778: You may not specify paths for ADMIN$ and IPC$ shares.
	- 3779: User or group %1 is already a member of local group %2.
	- 3780: There is no such user or group: %1.
	- 3781: There is no such computer: %1.
	- 3782: The computer %1 already exists.
	- 3783: There is no such global user or group: %1.
	- 3784: Only disk shares can be marked as cacheable
	- 3790: The system could not find message: %1.
	- 3802: This schedule date is invalid.
	- 3803: The LANMAN root directory is unavailable.
	- 3804: The SCHED.LOG file could not be opened.
	- 3805: The Server service has not been started.
	- 3806: The AT job ID does not exist.
	- 3807: The AT schedule file is corrupted.
	- 3808: The delete failed due to a problem with the AT schedule file.
	- 3809: The command line cannot exceed 259 characters.
	- 3810: The AT schedule file could not be updated because the disk is full.
	- 3812: The AT schedule file is invalid.  Please delete the file and create a new one.
	- 3813: The AT schedule file was deleted.
	- 3814: The syntax of this command is:
AT [id] [/DELETE]
AT time [/EVERY:date | /NEXT:date] command
The AT command schedules a program command to run at a
later date and time on a server.  It also displays the
list of programs and commands scheduled to be run.
You can specify the date as M,T,W,Th,F,Sa,Su or 1-31
for the day of the month.
You can specify the time in the 24 hour HH:MM format.
	- 3815: The AT command has timed-out.
Please try again later.
	- 3816: The minimum password age for user accounts cannot be greater
than the maximum password age.
	- 3817: You have specified a value that is incompatible
with servers with down-level software. Please specify a lower value.
	- 3870: %1 is not a valid computer name.
	- 3871: %1 is not a valid Windows network message number.
	- 3900: Message from %1 to %2 on %3
	- 3901: ****
	- 3902: **** unexpected end of message ****
	- 3905: Press ESC to exit
	- 3906: ...
	- 3910: Current time at %1 is %2
	- 3911: The current local clock is %1
Do you want to set the local computer's time to match the
time at %2? %3:	- 3912: Could not locate a time-server.
	- 3913: Could not find the domain controller for domain %1.
	- 3914: Local time (GMT%3) at %1 is %2
	- 3915: The user's home directory could not be determined.
	- 3916: The user's home directory has not been specified.
	- 3917: The name specified for the user's home directory (%1) is not a universal naming convention (UNC) name.
	- 3918: Drive %1 is now connected to %2. Your home directory is %3\%4.
	- 3919: Drive %1 is now connected to %2.
	- 3920: There are no available drive letters left.
	- 3932: %1 is not a valid domain or workgroup name.
	- 3935: The current SNTP value is: %1
	- 3936: This computer is not currently configured to use a specific SNTP server.
	- 3937: This current autoconfigured SNTP value is: %1
	- 3950: Reissue the given operation as a cached IO operation
	- 3951: You specified too many values for the %1 option.
	- 3952: You entered an invalid value for the %1 option.
	- 3953: The syntax is incorrect.
	- 3960: You specified an invalid file number.
	- 3961: You specified an invalid print job number.
	- 3963: The user or group account specified cannot be found.
	- 3965: The user was added but could not be enabled for File and Print
Services for NetWare.
	- 3966: File and Print Services for NetWare is not installed.
	- 3967: Cannot set user properties for File and Print Services for NetWare.
	- 3968: Password for %1 is: %2
	- 3969: NetWare compatible logon
	- 4000: WINS encountered an error while processing the command.
	- 4001: The local WINS cannot be deleted.
	- 4002: The importation from the file failed.
	- 4003: The backup failed. Was a full backup done before?
	- 4004: The backup failed. Check the directory to which you are backing the database.
	- 4005: The name does not exist in the WINS database.
	- 4006: Replication with a nonconfigured partner is not allowed.
	- 4050: The version of the supplied content information is not supported.
	- 4051: The supplied content information is malformed.
	- 4052: The requested data cannot be found in local or peer caches.
	- 4053: No more data is available or required.
	- 4054: The supplied object has not been initialized.
	- 4055: The supplied object has already been initialized.
	- 4056: A shutdown operation is already in progress.
	- 4057: The supplied object has already been invalidated.
	- 4058: An element already exists and was not replaced.
	- 4059: Can not cancel the requested operation as it has already been completed.
	- 4060: Can not perform the requested operation because it has already been carried out.
	- 4061: An operation accessed data beyond the bounds of valid data.
	- 4062: The requested version is not supported.
	- 4063: A configuration value is invalid.
	- 4064: The SKU is not licensed.
	- 4065: PeerDist Service is still initializing and will be available shortly.
	- 4066: Communication with one or more computers will be temporarily blocked due to recent errors.
	- 4100: The DHCP client has obtained an IP address that is already in use on the network. The local interface will be disabled until the DHCP client can obtain a new address.
	- 4200: The GUID passed was not recognized as valid by a WMI data provider.
	- 4201: The instance name passed was not recognized as valid by a WMI data provider.
	- 4202: The data item ID passed was not recognized as valid by a WMI data provider.
	- 4203: The WMI request could not be completed and should be retried.
	- 4204: The WMI data provider could not be located.
	- 4205: The WMI data provider references an instance set that has not been registered.
	- 4206: The WMI data block or event notification has already been enabled.
	- 4207: The WMI data block is no longer available.
	- 4208: The WMI data service is not available.
	- 4209: The WMI data provider failed to carry out the request.
	- 4210: The WMI MOF information is not valid.
	- 4211: The WMI registration information is not valid.
	- 4212: The WMI data block or event notification has already been disabled.
	- 4213: The WMI data item or data block is read only.
	- 4214: The WMI data item or data block could not be changed.
	- 4250: This operation is only valid in the context of an app container.
	- 4251: This application can only run in the context of an app container.
	- 4252: This functionality is not supported in the context of an app container.
	- 4253: The length of the SID supplied is not a valid length for app container SIDs.
	- 4300: The media identifier does not represent a valid medium.
	- 4301: The library identifier does not represent a valid library.
	- 4302: The media pool identifier does not represent a valid media pool.
	- 4303: The drive and medium are not compatible or exist in different libraries.
	- 4304: The medium currently exists in an offline library and must be online to perform this operation.
	- 4305: The operation cannot be performed on an offline library.
	- 4306: The library, drive, or media pool is empty.
	- 4307: The library, drive, or media pool must be empty to perform this operation.
	- 4308: No media is currently available in this media pool or library.
	- 4309: A resource required for this operation is disabled.
	- 4310: The media identifier does not represent a valid cleaner.
	- 4311: The drive cannot be cleaned or does not support cleaning.
	- 4312: The object identifier does not represent a valid object.
	- 4313: Unable to read from or write to the database.
	- 4314: The database is full.
	- 4315: The medium is not compatible with the device or media pool.
	- 4316: The resource required for this operation does not exist.
	- 4317: The operation identifier is not valid.
	- 4318: The media is not mounted or ready for use.
	- 4319: The device is not ready for use.
	- 4320: The operator or administrator has refused the request.
	- 4321: The drive identifier does not represent a valid drive.
	- 4322: Library is full. No slot is available for use.
	- 4323: The transport cannot access the medium.
	- 4324: Unable to load the medium into the drive.
	- 4325: Unable to retrieve the drive status.
	- 4326: Unable to retrieve the slot status.
	- 4327: Unable to retrieve status about the transport.
	- 4328: Cannot use the transport because it is already in use.
	- 4329: Unable to open or close the inject/eject port.
	- 4330: Unable to eject the medium because it is in a drive.
	- 4331: A cleaner slot is already reserved.
	- 4332: A cleaner slot is not reserved.
	- 4333: The cleaner cartridge has performed the maximum number of drive cleanings.
	- 4334: Unexpected on-medium identifier.
	- 4335: The last remaining item in this group or resource cannot be deleted.
	- 4336: The message provided exceeds the maximum size allowed for this parameter.
	- 4337: The volume contains system or paging files.
	- 4338: The media type cannot be removed from this library since at least one drive in the library reports it can support this media type.
	- 4339: This offline media cannot be mounted on this system since no enabled drives are present which can be used.
	- 4340: A cleaner cartridge is present in the tape library.
	- 4341: Cannot use the inject/eject port because it is not empty.
	- 4342: Erro	- 4343: O	- 4344: 	- 4345: 	- 4346: An	- 4347: 	- 4348: 	- 4349: (not found	- 4350: This file is currently not available for use on this computer.
	- 4351: The remote storage service is not operational at this time.
	- 4352: The remote storage service encountered a media error.
	- 4353: Rea	- 4354: Chang	- 4355: Ful	- 4356: Please type the password:	- 4357: Type the password for %1:	- 4358: Type a password for the user:	- 4359: Type the password for the shared resource:	- 4360: Type your password:	- 4361: Retype the password to confirm:	- 4362: Type the user's old password:	- 4363: Type the user's new password:	- 4364: Type your new password:	- 4365: Type the Replicator service password:	- 4366: Type your user name, or press ENTER if it is %1:	- 4367: Type the domain or server where you want to change a password, or
press ENTER if it is for domain %1:	- 4368: Type your user name:	- 4369: Network statistics for \\%1
	- 4370: Printing options for %1
	- 4371: Communication-device queues accessing %1
	- 4372: Print job detail
	- 4373: Communication-device queues at \\%1
	- 4374: Printers at %1
	- 4375: Printers accessing %1
	- 4376: Print jobs at %1:
	- 4377: Shared resources at %1
	- 4378: The following running services can be controlled:
	- 4379: Statistics are available for the following running services:
	- 4380: User accounts for \\%1
	- 4381: The syntax of this command is:
	- 4382: The options of this command are:
	- 4383: Please enter the name of the Primary Domain Controller:	- 4384: The string you have entered is too long. The maximum
is %1, please reenter.	- 4385: Sunda	- 4386: Monda	- 4387: Tuesda	- 4388: Wednesda	- 4389: Thursda	- 4390: The file or directory is not a reparse point.
	- 4391: The reparse point attribute cannot be set because it conflicts with an existing attribute.
	- 4392: The data present in the reparse point buffer is invalid.
	- 4393: The tag present in the reparse point buffer is invalid.
	- 4394: There is a mismatch between the tag specified in the request and the tag present in the reparse point.
	- 4395: The object manager encountered a reparse point while retrieving an object.
	- 4396: T	- 4397: 	- 4398: 	- 4399: S	- 4400: Fast Cache data not found.
	- 4401: Fast Cache data expired.
	- 4402: Fast Cache data corrupt.
	- 4403: Fast Cache data has exceeded its max size and cannot be updated.
	- 4404: Fast Cache has been ReArmed and requires a reboot until it can be updated.
	- 4405: Aliases for \\%1
	- 4406: Alias nam	- 4407: Commen	- 4408: Members
	- 4410: User Accounts for \\%1
	- 4411: User nam	- 4412: Full Nam	- 4413: Commen	- 4414: User's commen	- 4415: Parameter	- 4416: Country/region cod	- 4417: Privilege leve	- 4418: Operator privilege	- 4419: Account activ	- 4420: Secure Boot detected that rollback of protected data has been attempted.
	- 4421: The value is protected by Secure Boot policy and cannot be modified or deleted.
	- 4422: The Secure Boot policy is invalid.
	- 4423: A new Secure Boot policy did not contain the current publisher on its update list.
	- 4424: The Secure Boot policy is either not signed or is signed by a non-trusted signer.
	- 4425: Secure Boot is not enabled on this machine.
	- 4426: Secure Boot requires that certain files and drivers are not replaced by other files or drivers.
	- 4427: The Secure Boot Supplemental Policy file was not authorized on this machine.
	- 4428: The Supplemental Policy is not recognized on this device.
	- 4429: The Antirollback version was not found in the Secure Boot Policy.
	- 4430: The Platform ID specified in the Secure Boot policy does not match the Platform ID on this device.
	- 4431: The Secure Boot policy file has an older Antirollback Version than this device.
	- 4432: The Secure Boot policy file does not match the upgraded legacy policy.
	- 4433: The Secure Boot policy file is required but could not be found.
	- 4434: Supplemental Secure Boot policy file can not be loaded as a base Secure Boot policy.
	- 4435: Base Secure Boot policy file can not be loaded as a Supplemental Secure Boot policy.
	- 4436: Home director	- 4437: Password require	- 4438: User may change passwor	- 4439: User profil	- 4440: The copy offload read operation is not supported by a filter.
	- 4441: The copy offload write operation is not supported by a filter.
	- 4442: The copy offload read operation is not supported for the file.
	- 4443: The copy offload write operation is not supported for the file.
	- 4444: This file is currently associated with a different stream id.
	- 4445: The volume must undergo garbage collection.
	- 4446: The WOF driver encountered a corruption in WIM image's Header.
	- 4447: The WOF driver encountered a corruption in WIM image's Resource Table.
	- 4448: The WOF driver encountered a corruption in the compressed file's Resource Table.
	- 4449: The request cannot be completed as it requires modifying an immutable object.
	- 4450: Computer nam	- 4451: User nam	- 4452: Software versio	- 4453: Workstation active o	- 4454: Windows NT root director	- 4455: Workstation domai	- 4456: Logon domai	- 4457: Other domain(s	- 4458: COM Open Timeout (sec	- 4459: COM Send Count (byte	- 4460: COM Send Timeout (msec	- 4461: DOS session print time-out (sec	- 4462: Maximum error log size (K	- 4463: Maximum cache memory (K	- 4464: Number of network buffer	- 4465: Number of character buffer	- 4466: Size of network buffer	- 4467: Size of character buffer	- 4468: Full Computer nam	- 4469: Workstation Domain DNS Nam	- 4470: Windows 200	- 4481: Server Nam	- 4482: Server Commen	- 4483: Send administrative alerts t	- 4484: Software versio	- 4485: Peer Serve	- 4486: Windows N	- 4487: Server Leve	- 4488: Windows NT Serve	- 4489: Server is active o	- 4492: Server hidde	- 4500: Single Instance Storage is not available on this volume.
	- 4506: Maximum Logged On User	- 4507: Maximum concurrent administrator	- 4508: Maximum resources share	- 4509: Maximum connections to resource	- 4510: Maximum open files on serve	- 4511: Maximum open files per sessio	- 4512: Maximum file lock	- 4520: Idle session time (min	- 4526: Share-leve	- 4527: User-leve	- 4530: Unlimited Serve	- 4550: System Integrity detected that policy rollback has been attempted.
	- 4551: Your organization used Device Guard to block this app. Contact your support person for more info.
	- 4552: The System Integrity policy is invalid.
	- 4553: The System Integrity policy is either not signed or is signed by a non-trusted signer.
	- 4554: The number of System Integrity policies is out of limit.
	- 4555: The Code Integrity supplemental policy is not authorized by a Code Integrity base policy.
	- 4556: System Integrity policy has been violated.  Malicious binary reputation.
	- 4557: System Integrity policy has been violated.  Potentially unwanted application.
	- 4558: System Integrity policy has been violated.  Dangerous file extension from the web.
	- 4559: System Integrity policy has been violated.  Unable to contact reputation service for unknown file.
	- 4560: Virtual Secure Mode (VSM) is not initialized. The hypervisor or VSM may not be present or enabled.
	- 4561: The hypervisor is not protecting DMA because an IOMMU is not present or not enabled in the BIOS.
	- 4570: The Platform Manifest file was not authorized on this machine.
	- 4571: The Platform Manifest file was not valid.
	- 4572: The file is not authorized on this platform because an entry was not found in the Platform Manifest.
	- 4573: The catalog is not authorized on this platform because an entry was not found in the Platform Manifest.
	- 4574: The file is not authorized on this platform because a Binary ID was not found in the embedded signature.
	- 4575: No active Platform Manifest exists on this system.
	- 4576: The Platform Manifest file was not properly signed.
	- 4577: Primary Domain controller for workstation domain	- 4578: Lockout threshold	- 4579: Lockout duration (minutes)	- 4580: System Integrity policy has been violated.  Unfriendly file.
	- 4581: System Integrity policy has been violated.  Failed to obtain file reputation because an infrastructure issue occurred. Try again later.
	- 4582: System Integrity policy has been violated.  Explicit denied file.
	- 4600: Statistics sinc	- 4601: Sessions accepte	- 4602: Sessions timed-ou	- 4603: Sessions errored-ou	- 4604: Kilobytes sen	- 4605: Kilobytes receive	- 4606: Mean response time (msec	- 4607: Network error	- 4608: Files accesse	- 4609: Print jobs spoole	- 4610: System error	- 4611: Password violation	- 4612: Permission violation	- 4613: Communication devices accesse	- 4614: Sessions starte	- 4615: Sessions reconnecte	- 4616: Sessions starts faile	- 4617: Sessions disconnecte	- 4618: Network I/O's performe	- 4619: Files and pipes accesse	- 4620: Times buffers exhausted
	- 4621: Big buffer	- 4622: Request buffer	- 4623: Workstation Statistics for \\%1
	- 4624: Server Statistics for \\%1
	- 4625: Statistics since %1
	- 4626: Connections mad	- 4627: Connections faile	- 4630: Bytes receive	- 4631: Server Message Blocks (SMBs) receive	- 4632: Bytes transmitte	- 4633: Server Message Blocks (SMBs) transmitte	- 4634: Read operation	- 4635: Write operation	- 4636: Raw reads denie	- 4637: Raw writes denie	- 4638: Network error	- 4639: Connections mad	- 4640: Reconnections mad	- 4641: Server disconnect	- 4642: Sessions starte	- 4643: Hung session	- 4644: Failed session	- 4645: Failed operation	- 4646: Use coun	- 4647: Failed use coun	- 4650: %1 was deleted successfully.
	- 4651: %1 was used successfully.
	- 4652: The message was successfully sent to %1.
	- 4653: The message name %1 was forwarded successfully.
	- 4654: The message name %1 was added successfully.
	- 4655: The message name forwarding was successfully canceled.
	- 4656: %1 was shared successfully.
	- 4657: The server %1 successfully logged you on as %2.
	- 4658: %1 was logged off successfully.
	- 4659: %1 was successfully removed from the list of shares the Server creates
on startup.
	- 4661: The password was changed successfully.
	- 4662: %1 file(s) copied.
	- 4663: %1 file(s) moved.
	- 4664: The message was successfully sent to all users of the network.
	- 4665: The message was successfully sent to domain %1.
	- 4666: The message was successfully sent to all users of this server.
	- 4667: The message was successfully sent to group *%1.
	- 4695: Microsoft LAN Manager Version %1
	- 4696: Windows NT Server
	- 4697: Windows NT Workstation
	- 4698: MS-DOS Enhanced Workstation
	- 4699: Created at %1
	- 4700: Server Name            Remark
	- 4701: Cannot enumerate servers in non-default compartment.
	- 4702: (UNC	- 4703: ..	- 4704: Domain
	- 4705: Resources on %1
	- 4706: Invalid network provider.  Available networks are:
	- 4710: Dis	- 4711: Prin	- 4712: Com	- 4713: IP	- 4714: Status       Local     Remote                    Network
	- 4715: O	- 4716: Dorman	- 4717: Pause	- 4718: Disconnecte	- 4719: Erro	- 4720: Connectin	- 4721: Reconnectin	- 4722: Statu	- 4723: Local nam	- 4724: Remote nam	- 4725: Resource typ	- 4726: # Open	- 4727: # Connection	- 4728: Unavailabl	- 4730: Share name   Resource                        Remark
	- 4731: Share nam	- 4732: Resourc	- 4733: Spoole	- 4734: Permissio	- 4735: Maximum user	- 4736: No limi	- 4737: User	- 4738: The share name entered may not be accessible from some MS-DOS workstations.
Are you sure you want to use this share name? %1:	- 4739: Cachin	- 4740: ID         Path                                    User name            # Locks
	- 4741: File I	- 4742: Lock	- 4743: Permission	- 4744: Share nam	- 4745: Typ	- 4746: Used a	- 4747: Commen	- 4750: Computer               User name            Client Type       Opens Idle time
	- 4751: Compute	- 4752: Sess tim	- 4753: Idle tim	- 4754: Share name     Type     # Opens
	- 4755: Client typ	- 4756: Guest logo	- 4770: Manual caching of document	- 4771: Automatic caching of document	- 4772: Automatic caching of programs and document	- 4773: Manual caching of documents with BranchCache enable	- 4774: Caching disable	- 4775: Automati	- 4776: Manua	- 4777: Document	- 4778: Program	- 4779: BranchCach	- 4780: Non	- 4800: Nam	- 4801: Forwarded t	- 4802: Forwarded to you fro	- 4803: Users of this serve	- 4804: Net Send has been interrupted by a Ctrl+Break from the user.
	- 4810: Name                         Job #      Size            Status
	- 4811: job	- 4812: Prin	- 4813: Nam	- 4814: Job 	- 4815: Siz	- 4816: Statu	- 4817: Separator fil	- 4818: Commen	- 4819: Priorit	- 4820: Print afte	- 4821: Print unti	- 4822: Print processo	- 4823: Additional inf	- 4824: Parameter	- 4825: Print Device	- 4826: Printer Activ	- 4827: Printer hel	- 4828: Printer erro	- 4829: Printer being delete	- 4830: Printer status unknow	- 4840: Held until %	- 4841: Job 	- 4842: Submitting use	- 4843: Notif	- 4844: Job data typ	- 4845: Job parameter	- 4846: Waitin	- 4847: Held in queu	- 4848: Spoolin	- 4849: Pause	- 4850: Offlin	- 4851: Erro	- 4852: Out of pape	- 4853: Intervention require	- 4854: Printin	- 4855: on	- 4856: Paused on %	- 4857: Offline on %	- 4858: Error on%	- 4859: Out of Paper on %	- 4860: Check printer on %	- 4861: Printing on %	- 4862: Drive	- 4930: User name              Type                 Dat	- 4931: Lockou	- 4932: Servic	- 4933: Serve	- 4934: Server starte	- 4935: Server pause	- 4936: Server continue	- 4937: Server stoppe	- 4938: Sessio	- 4939: Logon Gues	- 4940: Logon Use	- 4941: Logon Administrato	- 4942: Logoff norma	- 4943: Logo	- 4944: Logoff erro	- 4945: Logoff auto-disconnec	- 4946: Logoff administrator-disconnec	- 4947: Logoff forced by logon restriction	- 4948: Servic	- 4949: %1 Installe	- 4950: %1 Install Pendin	- 4951: %1 Pause	- 4952: %1 Pause Pendin	- 4953: %1 Continue	- 4954: %1 Continue Pendin	- 4955: %1 Stoppe	- 4956: %1 Stop Pendin	- 4957: Accoun	- 4958: User account %1 was modified	- 4959: Group account %1 was modified	- 4960: User account %1 was delete	- 4961: Group account %1 was delete	- 4962: User account %1 was adde	- 4963: Group account %1 was adde	- 4964: Account system settings were modifie	- 4965: Logon restrictio	- 4966: Limit exceeded:  UNKNOW	- 4967: Limit exceeded:  Logon hour	- 4968: Limit exceeded:  Account expire	- 4969: Limit exceeded:  Workstation ID invali	- 4970: Limit exceeded:  Account disable	- 4971: Limit exceeded:  Account delete	- 4972: Shar	- 4973: Use %	- 4974: Unuse %	- 4975: User's session disconnected %	- 4976: Administrator stopped sharing resource %	- 4977: User reached limit for %	- 4978: Bad passwor	- 4979: Administrator privilege require	- 4980: Acces	- 4981: %1 permissions adde	- 4982: %1 permissions modifie	- 4983: %1 permissions delete	- 4984: Access denie	- 4985: Unknow	- 4986: Othe	- 4987: Duration	- 4988: Duration: Not availabl	- 4989: Duration: Less than one secon	- 4990: (none	- 4991: Closed %	- 4992: Closed %1 (disconnected	- 4993: Administrator closed %	- 4994: Access ende	- 4995: Log on to networ	- 4996: Logon denie	- 4997: Program             Message             Tim	- 4998: Account locked due to %1 bad password	- 4999: Account unlocked by administrato	- 5000: Log off networ	- 5001: The operation cannot be completed because other resources are dependent on this resource.
	- 5002: The cluster resource dependency cannot be found.
	- 5003: The cluster resource cannot be made dependent on the specified resource because it is already dependent.
	- 5004: The cluster resource is not online.
	- 5005: A cluster node is not available for this operation.
	- 5006: The cluster resource is not available.
	- 5007: The cluster resource could not be found.
	- 5008: The cluster is being shut down.
	- 5009: A cluster node cannot be evicted from the cluster unless the node is down or it is the last node.
	- 5010: The object already exists.
	- 5011: The object is already in the list.
	- 5012: The cluster group is not available for any new requests.
	- 5013: The cluster group could not be found.
	- 5014: The operation could not be completed because the cluster group is not online.
	- 5015: The operation failed because either the specified cluster node is not the owner of the resource, or the node is not a possible owner of the resource.
	- 5016: The operation failed because either the specified cluster node is not the owner of the group, or the node is not a possible owner of the group.
	- 5017: The cluster resource could not be created in the specified resource monitor.
	- 5018: The cluster resource could not be brought online by the resource monitor.
	- 5019: The operation could not be completed because the cluster resource is online.
	- 5020: The cluster resource could not be deleted or brought offline because it is the quorum resource.
	- 5021: The cluster could not make the specified resource a quorum resource because it is not capable of being a quorum resource.
	- 5022: The cluster software is shutting down.
	- 5023: The group or resource is not in the correct state to perform the requested operation.
	- 5024: The properties were stored but not all changes will take effect until the next time the resource is brought online.
	- 5025: The cluster could not make the specified resource a quorum resource because it does not belong to a shared storage class.
	- 5026: The cluster resource could not be deleted since it is a core resource.
	- 5027: The quorum resource failed to come online.
	- 5028: The quorum log could not be created or mounted successfully.
	- 5029: The cluster log is corrupt.
	- 5030: The record could not be written to the cluster log since it exceeds the maximum size.
	- 5031: The cluster log exceeds its maximum size.
	- 5032: No checkpoint record was found in the cluster log.
	- 5033: The minimum required disk space needed for logging is not available.
	- 5034: The cluster node failed to take control of the quorum resource because the resource is owned by another active node.
	- 5035: A cluster network is not available for this operation.
	- 5036: A cluster node is not available for this operation.
	- 5037: All cluster nodes must be running to perform this operation.
	- 5038: A cluster resource failed.
	- 5039: The cluster node is not valid.
	- 5040: The cluster node already exists.
	- 5041: A node is in the process of joining the cluster.
	- 5042: The cluster node was not found.
	- 5043: The cluster local node information was not found.
	- 5044: The cluster network already exists.
	- 5045: The cluster network was not found.
	- 5046: The cluster network interface already exists.
	- 5047: The cluster network interface was not found.
	- 5048: The cluster request is not valid for this object.
	- 5049: The cluster network provider is not valid.
	- 5050: The cluster node is down.
	- 5051: The cluster node is not reachable.
	- 5052: The cluster node is not a member of the cluster.
	- 5053: A cluster join operation is not in progress.
	- 5054: The cluster network is not valid.
	- 5055: Ma	- 5056: The cluster node is up.
	- 5057: The cluster IP address is already in use.
	- 5058: The cluster node is not paused.
	- 5059: No cluster security context is available.
	- 5060: The cluster network is not configured for internal cluster communication.
	- 5061: The cluster node is already up.
	- 5062: The cluster node is already down.
	- 5063: The cluster network is already online.
	- 5064: The cluster network is already offline.
	- 5065: The cluster node is already a member of the cluster.
	- 5066: The cluster network is the only one configured for internal cluster communication between two or more active cluster nodes. The internal communication capability cannot be removed from the network.
	- 5067: One or more cluster resources depend on the network to provide service to clients. The client access capability cannot be removed from the network.
	- 5068: This operation cannot currently be performed on the cluster group containing the quorum resource.
	- 5069: The cluster quorum resource is not allowed to have any dependencies.
	- 5070: The cluster node is paused.
	- 5071: The cluster resource cannot be brought online. The owner node cannot run this resource.
	- 5072: The cluster node is not ready to perform the requested operation.
	- 5073: The cluster node is shutting down.
	- 5074: The cluster join operation was aborted.
	- 5075: The node failed to join the cluster because the joining node and other nodes in the cluster have incompatible operating system versions. To get more information about operating system versions of the cluster, run the Validate a Configuration Wizard or the Test-Cluster Windows PowerShell cmdlet.
	- 5076: This resource cannot be created because the cluster has reached the limit on the number of resources it can monitor.
	- 5077: The system configuration changed during the cluster join or form operation. The join or form operation was aborted.
	- 5078: The specified resource type was not found.
	- 5079: The specified node does not support a resource of this type. This may be due to version inconsistencies or due to the absence of the resource DLL on this node.
	- 5080: The specified resource name is not supported by this resource DLL. This may be due to a bad (or changed) name supplied to the resource DLL.
	- 5081: No authentication package could be registered with the RPC server.
	- 5082: You cannot bring the group online because the owner of the group is not in the preferred list for the group. To change the owner node for the group, move the group.
	- 5083: The join operation failed because the cluster database sequence number has changed or is incompatible with the locker node. This may happen during a join operation if the cluster database was changing during the join.
	- 5084: The resource monitor will not allow the fail operation to be performed while the resource is in its current state. This may happen if the resource is in a pending state.
	- 5085: A non locker code got a request to reserve the lock for making global updates.
	- 5086: The quorum disk could not be located by the cluster service.
	- 5087: The backed up cluster database is possibly corrupt.
	- 5088: A DFS root already exists in this cluster node.
	- 5089: An attempt to modify a resource property failed because it conflicts with another existing property.
	- 5090: This operation is not supported on a cluster without an Administrator Access Point.
	- 5091: Denmar	- 5092: Swede	- 5093: Norwa	- 5094: German	- 5095: Australi	- 5096: Japa	- 5097: Kore	- 5098: China (PRC	- 5099: Taiwa	- 5100: Asi	- 5101: Portuga	- 5102: Finlan	- 5103: Arabi	- 5104: Hebre	- 5150: A power failure has occurred at %1.  Please terminate all activity with this server.
	- 5151: Power has been restored at %1.  Normal operations have resumed.
	- 5152: The UPS service is starting shut down at %1.
	- 5153: The UPS service is about to perform final shut down.
	- 5170: The Workstation must be started with the NET START command.
	- 5175: Remote IP	- 5176: Remote Admi	- 5177: Default shar	- 5178: User Profile	- 5280: The password entered is longer than 14 characters.  Computers
with Windows prior to Windows 2000 will not be able to use
this account. Do you want to continue this operation? %1:	- 5281: %1 has a remembered connection to %2. Do you
want to overwrite the remembered connection? %3:	- 5282: Do you want to resume loading the profile?  The command which
caused the error will be ignored. %1:	- 5284: Do you want to continue this operation? %1:	- 5285: Do you want to add this? %1:	- 5286: Do you want to continue this operation? %1:	- 5287: Is it OK to start it? %1:	- 5288: Do you want to start the Workstation service? %1:	- 5289: Is it OK to continue disconnecting and force them closed? %1:	- 5290: The printer does not exist.  Do you want to create it? %1:	- 5291: Neve	- 5292: Neve	- 5293: Neve	- 5295: NET.HL	- 5296: NET.HL	- 5297: Den	- 5300: The network control block (NCB) request completed successfully.
The NCB is the data.
	- 5301: Illegal network control block (NCB) buffer length on SEND DATAGRAM,
SEND BROADCAST, ADAPTER STATUS, or SESSION STATUS.
The NCB is the data.
	- 5302: The data descriptor array specified in the network control block (NCB) is
invalid.  The NCB is the data.
	- 5303: The command specified in the network control block (NCB) is illegal.
The NCB is the data.
	- 5304: The message correlator specified in the network control block (NCB) is
invalid.  The NCB is the data.
	- 5305: A network control block (NCB) command timed-out.  The session may have
terminated abnormally.  The NCB is the data.
	- 5306: An incomplete network control block (NCB) message was received.
The NCB is the data.
	- 5307: The buffer address specified in the network control block (NCB) is illegal.
The NCB is the data.
	- 5308: The session number specified in the network control block (NCB) is not active.
The NCB is the data.
	- 5309: No resource was available in the network adapter.
The network control block (NCB) request was refused.  The NCB is the data.
	- 5310: The session specified in the network control block (NCB) was closed.
The NCB is the data.
	- 5311: The network control block (NCB) command was canceled.
The NCB is the data.
	- 5312: The message segment specified in the network control block (NCB) is
illogical.  The NCB is the data.
	- 5313: The name already exists in the local adapter name table.
The network control block (NCB) request was refused.  The NCB is the data.
	- 5314: The network adapter name table is full.
The network control block (NCB) request was refused.  The NCB is the data.
	- 5315: The network name has active sessions and is now de-registered.
The network control block (NCB) command completed.  The NCB is the data.
	- 5316: A previously issued Receive Lookahead command is active
for this session.  The network control block (NCB) command was rejected.
The NCB is the data.
	- 5317: The local session table is full. The network control block (NCB) request was refused.
The NCB is the data.
	- 5318: A network control block (NCB) session open was rejected.  No LISTEN is outstanding
on the remote computer.  The NCB is the data.
	- 5319: The name number specified in the network control block (NCB) is illegal.
The NCB is the data.
	- 5320: The call name specified in the network control block (NCB) cannot be found or
did not answer.  The NCB is the data.
	- 5321: The name specified in the network control block (NCB) was not found.  Cannot put '*' or
00h in the NCB name.  The NCB is the data.
	- 5322: The name specified in the network control block (NCB) is in use on a remote adapter.
The NCB is the data.
	- 5323: The name specified in the network control block (NCB) has been deleted.
The NCB is the data.
	- 5324: The session specified in the network control block (NCB) ended abnormally.
The NCB is the data.
	- 5325: The network protocol has detected two or more identical
names on the network.	The network control block (NCB) is the data.
	- 5326: An unexpected protocol packet was received.  There may be an
incompatible remote device.  The network control block (NCB) is the data.
	- 5333: The NetBIOS interface is busy.
The network control block (NCB) request was refused.  The NCB is the data.
	- 5334: There are too many network control block (NCB) commands outstanding.
The NCB request was refused.  The NCB is the data.
	- 5335: The adapter number specified in the network control block (NCB) is illegal.
The NCB is the data.
	- 5336: The network control block (NCB) command completed while a cancel was occurring.
The NCB is the data.
	- 5337: The name specified in the network control block (NCB) is reserved.
The NCB is the data.
	- 5338: The network control block (NCB) command is not valid to cancel.
The NCB is the data.
	- 5351: There are multiple network control block (NCB) requests for the same session.
The NCB request was refused.  The NCB is the data.
	- 5352: There has been a network adapter error. The only NetBIOS
command that may be issued is an NCB RESET. The network control block (NCB) is
the data.
	- 5354: The maximum number of applications was exceeded.
The network control block (NCB) request was refused.  The NCB is the data.
	- 5356: The requested resources are not available.
The network control block (NCB) request was refused.  The NCB is the data.
	- 5364: A system error has occurred.
The network control block (NCB) request was refused.  The NCB is the data.
	- 5365: A ROM checksum failure has occurred.
The network control block (NCB) request was refused.  The NCB is the data.
	- 5366: A RAM test failure has occurred.
The network control block (NCB) request was refused.  The NCB is the data.
	- 5367: A digital loopback failure has occurred.
The network control block (NCB) request was refused.  The NCB is the data.
	- 5368: An analog loopback failure has occurred.
The network control block (NCB) request was refused.  The NCB is the data.
	- 5369: An interface failure has occurred.
The network control block (NCB) request was refused.  The NCB is the data.
	- 5370: An unrecognized network control block (NCB) return code was received.
The NCB is the data.
	- 5380: A network adapter malfunction has occurred.
The network control block (NCB) request was refused.  The NCB is the data.
	- 5381: The network control block (NCB) command is still pending.
The NCB is the data.
	- 5500: The update log on %1 is over 80%% capacity. The primary
domain controller %2 is not retrieving the updates.
	- 5501: The update log on %1 is full, and no further updates
can be added until the primary domain controller %2
retrieves the updates.
	- 5502: The time difference with the primary domain controller %1
exceeds the maximum allowed skew of %2 seconds.
	- 5503: The account of user %1 has been locked out on %2
due to %3 bad password attempts.
	- 5504: The %1 log file cannot be opened.
	- 5505: The %1 log file is corrupted and will be cleared.
	- 5506: The Application log file could not be opened.  %1 will be used as the
default log file.
	- 5507: The %1 Log is full.  If this is the first time you have seen this
message, take the following steps:
1. Click Start, click Run, type "eventvwr", and then click OK.
2. Click %1, click the Action menu, click Clear All Events, and then click No.
If this dialog reappears, contact your helpdesk or system administrator.
	- 5508: The security database full synchronization has been initiated by the server %1.
	- 5509: Windows could not be started as configured.
A previous working configuration was used instead.
	- 5510: The exception 0x%1 occurred in the application %2 at location 0x%3.
	- 5511: The servers %1 and  %3 both claim to be an NT Domain Controller for
the %2 domain. One of the servers should be removed from the
domain because the servers have different security identifiers
(SID).
	- 5512: The server %1 and %2 both claim to be the primary domain
controller for the %3 domain. One of the servers should be
demoted or removed from the domain.
	- 5513: The computer %1 tried to connect to the server %2 using
the trust relationship established by the %3 domain. However, the
computer lost the correct security identifier (SID)
when the domain was reconfigured. Reestablish the trust
relationship.
	- 5514: The computer has rebooted from a bugcheck.  The bugcheck was:
%1.
%2
A full dump was not saved.
	- 5515: The computer has rebooted from a bugcheck.  The bugcheck was:
%1.
%2
A dump was saved in: %3.
	- 5516: The computer or domain %1 trusts domain %2.  (This may be an indirect
trust.)  However, %1 and %2 have the same machine security identifier
(SID).  NT should be re-installed on either %1 or %2.
	- 5517: The computer or domain %1 trusts domain %2.  (This may be an indirect
trust.)  However, %2 is not a valid name for a trusted domain.
The name of the trusted domain should be changed to a valid name.
	- 5600: Could not share the User or Script path.
	- 5601: The password for this computer is not found in the local security
database.
	- 5602: An internal error occurred while accessing the computer's
local or network security database.
	- 5700: The Netlogon service could not initialize the replication data
structures successfully. The service was terminated.  The following
error occurred: 
%1
	- 5701: The Netlogon service failed to update the domain trust list.  The
following error occurred: 
%1
	- 5702: The Netlogon service could not add the RPC interface.  The
service was terminated. The following error occurred: 
%1
	- 5703: The Netlogon service could not read a mailslot message from %1 due
to the following error: 
%2
	- 5704: The Netlogon service failed to register the service with the
service controller. The service was terminated. The following
error occurred: 
%1
	- 5705: The change log cache maintained by the Netlogon service for %1
database changes is inconsistent. The Netlogon service is resetting
the change log.
	- 5706: The Netlogon service could not create server share %1.  The following
error occurred: 
%2
	- 5707: The down-level logon request for the user %1 from %2 failed.
	- 5708: The down-level logoff request for the user %1 from %2 failed.
	- 5709: The Windows NT or Windows 2000 %1 logon request for the user %2\%3 from %4 (via %5)
failed.
	- 5710: The Windows NT or Windows 2000 %1 logoff request for the user %2\%3 from %4
failed.
	- 5711: The partial synchronization request from the server %1 completed
successfully. %2 changes(s) has(have) been returned to the
caller.
	- 5712: The partial synchronization request from the server %1 failed with
the following error: 
%2
	- 5713: The full synchronization request from the server %1 completed
successfully. %2 object(s) has(have) been returned to
the caller.
	- 5714: The full synchronization request from the server %1 failed with
the following error: 
%2
	- 5715: The partial synchronization replication of the %1 database from the
primary domain controller %2 completed successfully. %3 change(s) is(are)
applied to the database.
	- 5716: The partial synchronization replication of the %1 database from the
primary domain controller %2 failed with the following error: 
%3
	- 5717: The full synchronization replication of the %1 database from the
primary domain controller %2 completed successfully.
	- 5718: The full synchronization replication of the %1 database from the
primary domain controller %2 failed with the following error: 
%3
	- 5719: This computer was not able to set up a secure session with a domain
controller in domain %1 due to the following: 
%2
This may lead to authentication problems. Make sure that this
computer is connected to the network. If the problem persists,
please contact your domain administrator.
ADDITIONAL INFO
If this computer is a domain controller for the specified domain, it
sets up the secure session to the primary domain controller emulator in the specified
domain. Otherwise, this computer sets up the secure session to any domain controller
in the specified domain.
	- 5720: The session setup to the Windows Domain Controller %1 for the domain %2
failed because the computer %3 does not have a local security database account.
	- 5721: The session setup to the Windows Domain Controller %1 for the domain %2
failed because the Domain Controller did not have an account %4
needed to set up the session by this computer %3.
ADDITIONAL DATA
If this computer is a member of or a Domain Controller in the specified domain, the
aforementioned account is a computer account for this computer in the specified domain.
Otherwise, the account is an interdomain trust account with the specified domain.
	- 5722: The session setup from the computer %1 failed to authenticate.
The name(s) of the account(s) referenced in the security database is
%2.  The following error occurred: 
%3
	- 5723: The session setup from computer '%1' failed because the security database
does not contain a trust account '%2' referenced by the specified computer.
USER ACTION
If this is the first occurrence of this event for the specified computer
and account, this may be a transient issue that doesn't require any action
at this time.
If this is a Read-Only Domain Controller and '%2' is a legitimate machine
account for the computer '%1' then '%1' should be marked cacheable for this
location if appropriate or otherwise ensure connectivity to a domain controller
capable of servicing the request (for example a writable domain controller).
Otherwise, the following steps may be taken to resolve this problem:
If '%2' is a legitimate machine account for the computer '%1', then '%1'
should be rejoined to the domain.
If '%2' is a legitimate interdomain trust account, then the trust should
be recreated.
Otherwise, assuming that '%2' is not a legitimate account, the following
action should be taken on '%1':
If '%1' is a Domain Controller, then the trust associated with '%2' should be deleted.
If '%1' is not a Domain Controller, it should be disjoined from the domain.
	- 5724: Could not register control handler with service controller %1.
	- 5725: Could not set service status with service controller %1.
	- 5726: Could not find the computer name %1.
	- 5727: Could not load %1 device driver.
	- 5728: Could not load any transport.
	- 5729: Replication of the %1 Domain Object "%2" from primary domain controller
%3 failed with the following error: 
%4
	- 5730: Replication of the %1 Global Group "%2" from primary domain controller
%3 failed with the following error: 
%4
	- 5731: Replication of the %1 Local Group "%2" from primary domain controller
%3 failed with the following error: 
%4
	- 5732: Replication of the %1 User "%2" from primary domain controller
%3 failed with the following error: 
%4
	- 5733: Replication of the %1 Policy Object "%2" from primary domain controller
%3 failed with the following error: 
%4
	- 5734: Replication of the %1 Trusted Domain Object "%2" from primary domain controller
%3 failed with the following error: 
%4
	- 5735: Replication of the %1 Account Object "%2" from primary domain controller
%3 failed with the following error: 
%4
	- 5736: Replication of the %1 Secret "%2" from primary domain controller
%3 failed with the following error: 
%4
	- 5737: The system returned the following unexpected error code: 
%1
	- 5738: Netlogon has detected two machine accounts for server "%1".
The server can be either a Windows 2000 Server that is a member of the
domain or the server can be a LAN Manager server with an account in the
SERVERS global group.  It cannot be both.
	- 5739: This domain has more global groups than can be replicated to a LanMan
BDC.  Either delete some of your global groups or remove the LanMan
BDCs from the domain.
	- 5740: The Browser driver returned the following error to Netlogon: 
%1
	- 5741: Netlogon could not register the %1<1B> name for the following reason: 
%2
	- 5742: Service failed to retrieve messages needed to boot remote boot clients.
	- 5743: Service experienced a severe error and can no longer provide remote boot
for 3Com 3Start remote boot clients.
	- 5744: Service experienced a severe system error and will shut itself down.
	- 5745: Client with computer name %1 failed to acknowledge receipt of the
boot data.  Remote boot of this client was not completed.
	- 5746: Client with computer name %1 was not booted due to an error in opening
file %2.
	- 5747: Client with computer name %1 was not booted due to an error in reading
file %2.
	- 5748: Client with computer name %1 was not booted due to insufficient memory
at the remote boot server.
	- 5749: Client with computer name %1 will be booted without using checksums
because checksum for file %2 could not be calculated.
	- 5750: Client with computer name %1 was not booted due to too many lines in
file %2.
	- 5751: Client with computer name %1 was not booted because the boot block
configuration file %2 for this client does not contain boot block
line and/or loader line.
	- 5752: Client with computer name %1 was not booted due to a bad size of
file %2.
	- 5753: Client with computer name %1 was not booted due to remote boot
service internal error.
	- 5754: Client with computer name %1 was not booted because file %2 has an
invalid boot header.
	- 5755: Client with computer name %1 was not booted due to network error.
	- 5756: Client with adapter id %1 was not booted due to lack of resources.
	- 5757: Service experienced error copying file or directory %1.
	- 5758: Service experienced error deleting file or directory %1.
	- 5759: Service experienced error setting permissions on file or directory %1.
	- 5760: Service experienced error evaluating RPL configurations.
	- 5761: Service experienced error creating RPL profiles for all configurations.
	- 5762: Service experienced error accessing registry.
	- 5763: Service experienced error replacing possibly outdated RPLDISK.SYS.
	- 5764: Service experienced error adding security accounts or setting
file permissions.  These accounts are the RPLUSER local group
and the user accounts for the individual RPL workstations.
	- 5765: Service failed to back up its database.
	- 5766: Service failed to initialize from its database.  The database may be
missing or corrupted.  Service will attempt restoring the database
from the backup.
	- 5767: Service failed to restore its database from the backup.  Service
will not start.
	- 5768: Service successfully restored its database from the backup.
	- 5769: Service failed to initialize from its restored database.  Service
will not start.
	- 5770: The session setup to the Windows Domain Controller %1 from computer
%2 using account %4 failed.  %2 is declared to be a BDC in domain %3.
However, %2 tried to connect as either a DC in a trusted domain,
a member workstation in domain %3, or as a server in domain %3.
Use the Active Directory Users and Computers tool or Server Manager to remove the BDC account for %2.
	- 5771: The Remoteboot database was in NT 3.5 / NT 3.51 format and NT is
attempting to convert it to NT 4.0 format. The JETCONV converter
will write to the Application event log when it is finished.
	- 5772: Global group SERVERS exists in domain %1 and has members.
This group defines Lan Manager BDCs in the domain.
Lan Manager BDCs are not permitted in NT domains.
	- 5773: The following DNS server that is authoritative for the DNS domain controller
locator records of this domain controller does not support dynamic DNS updates:
DNS server IP address: %1
Returned Response Code (RCODE): %2
Returned Status Code: %3
USER ACTION
Configure the DNS server to allow dynamic DNS updates or manually add the DNS
records from the file '%SystemRoot%\System32\Config\Netlogon.dns' to the DNS database.
	- 5774: The dynamic registration of the DNS record '%1' failed on the following DNS server:
DNS server IP address: %3
Returned Response Code (RCODE): %4
Returned Status Code: %5
For computers and users to locate this domain controller, this record must be
registered in DNS.
USER ACTION
Determine what might have caused this failure, resolve the problem, and initiate
registration of the DNS records by the domain controller. To determine what might
have caused this failure, run DCDiag.exe. To learn more about DCDiag.exe, see Help
and Support Center. To initiate registration of the DNS records by this domain
controller, run 'nltest.exe /dsregdns' from the command prompt on the domain controller
or restart Net Logon service. 
  Or, you can manually add this record to DNS, but it
is not recommended.
ADDITIONAL DATA
Error Value: %2
	- 5775: The dynamic deletion of the DNS record '%1' failed on the following DNS server:
DNS server IP address: %3
Returned Response Code (RCODE): %4
Returned Status Code: %5
USER ACTION
To prevent remote computers from connecting unnecessarily to the domain controller,
delete the record manually or troubleshoot the failure to dynamically delete the
record. To learn more about debugging DNS, see Help and Support Center.
ADDITIONAL DATA
Error Value: %2
	- 5776: Failed to create/open file %1 with the following error: 
%2
	- 5777: Netlogon got the following error while trying to get the subnet to site
mapping information from the DS: 
%1
	- 5778: '%1' tried to determine its site by looking up its IP address ('%2')
in the Configuration\Sites\Subnets container in the DS.  No subnet matched
the IP address.  Consider adding a subnet object for this IP address.
	- 5779: The site name for this computer is '%1'.  That site name is not a valid
site name.  A site name must be a valid DNS label.
Rename the site to be a valid name.
	- 5780: The subnet object '%1' appears in the Configuration\Sites\Subnets
container in the DS.  The name is not syntactically valid.  The valid
syntax is xx.xx.xx.xx/yy where xx.xx.xx.xx is a valid IP subnet number
and yy is the number of bits in the subnet mask.
Correct the name of the subnet object.
	- 5781: Dynamic registration or deletion of one or more DNS records associated with DNS
domain '%1' failed.  These records are used by other computers to locate this
server as a domain controller (if the specified domain is an Active Directory
domain) or as an LDAP server (if the specified domain is an application partition).
Possible causes of failure include:
- TCP/IP properties of the network connections of this computer contain wrong IP address(es) of the preferred and alternate DNS servers
- Specified preferred and alternate DNS servers are not running
- DNS server(s) primary for the records to be registered is not running
- Preferred or alternate DNS servers are configured with wrong root hints
- Parent DNS zone contains incorrect delegation to the child zone authoritative for the DNS records that failed registration
USER ACTION
Fix possible misconfiguration(s) specified above and initiate registration or deletion of
the DNS records by running 'nltest.exe /dsregdns' from the command prompt on the domain
controller or by restarting Net Logon service on the domain controller.
	- 5782: Dynamic registration or deregistration of one or more DNS records failed with the following error: 
%1
	- 5783: The session setup to the Windows Domain Controller %1 for the domain %2
is not responsive.  The current RPC call from Netlogon on \\%3 to %1 has been cancelled.
	- 5784: Site '%2' does not have any Domain Controllers for domain '%3'.
Domain Controllers in site '%1' have been automatically
selected to cover site '%2' for domain '%3' based on configured
Directory Server replication costs.
	- 5785: This Domain Controller no longer automatically covers site '%1' for domain '%2'.
	- 5786: Site '%2' does not have any Global Catalog servers for forest '%3'.
Global Catalog servers in site '%1' have been automatically
selected to cover site '%2' for forest '%3' based on configured
Directory Server replication costs.
	- 5787: This Global Catalog server no longer automatically covers site '%1' for forest '%2'.
	- 5788: Attempt to update HOST Service Principal Names (SPNs) of the computer
object in Active Directory failed. The updated values were '%1' and '%2'.
The following error occurred: 
%3
	- 5789: Attempt to update DNS Host Name of the computer object
in Active Directory failed. The updated value was '%1'.
The following error occurred: 
%2
	- 5790: No suitable Domain Controller is available for domain %1.
An NT4 or older domain controller is available but it cannot
be used for authentication purposes in the Windows 2000 or newer
domain that this computer is a member of.
The following error occurred:
%2
	- 5791: The domain of this computer, %1 has been downgraded from Windows 2000
or newer to Windows NT4 or older. The computer cannot function properly
in this case for authentication purposes. This computer needs to rejoin
the domain.
The following error occurred:
%2
	- 5792: Site '%2' does not have any LDAP servers for non-domain NC '%3'.
LDAP servers in site '%1' have been automatically selected to
cover site '%2' for non-domain NC '%3' based on configured
Directory Server replication costs.
	- 5793: This LDAP server no longer automatically covers site '%1' for non-domain NC '%2'.
	- 5794: Site '%2' is no longer manually configured in the registry as
covered by this Domain Controller for domain '%3'. As a result,
site '%2' does not have any Domain Controllers for domain '%3'.
Domain Controllers in site '%1' have been automatically
selected to cover site '%2' for domain '%3' based on configured
Directory Server replication costs.
	- 5795: This Domain Controller no longer automatically covers site '%1' for domain '%2'.
However, site '%1' is still (manually) covered by this Domain Controller for
domain '%2' since this site has been manually configured in the registry.
	- 5796: Site '%2' is no longer manually configured in the registry as
covered by this Global Catalog server for forest '%3'. As a result,
site '%2' does not have any Global Catalog servers for forest '%3'.
Global Catalog servers in site '%1' have been automatically
selected to cover site '%2' for forest '%3' based on configured
Directory Server replication costs.
	- 5797: This Global Catalog server no longer automatically covers site '%1' for forest '%2'.
However, site '%1' is still (manually) covered by this Global catalog for
forest '%2' since this site has been manually configured in the registry.
	- 5798: Site '%2' is no longer manually configured in the registry as
covered by this LDAP server for non-domain NC '%3'. As a result,
site '%2' does not have any LDAP servers for non-domain NC '%3'.
LDAP servers in site '%1' have been automatically
selected to cover site '%2' for non-domain NC '%3' based on
configured Directory Server replication costs.
	- 5799: This LDAP server no longer automatically covers site '%1' for non-domain NC '%2'.
However, site '%1' is still (manually) covered by this LDAP server for
non-domain NC '%2' since this site has been manually configured in the registry.
	- 5800: Attempt to update DnsHostName and HOST Service Principal Name (SPN) attributes
of the computer object in Active Directory failed because the Domain Controller
'%1' had more than one account with the name '%2' corresponding to this computer.
Not having SPNs registered may result in authentication failures for this computer.
Contact your domain administrator who may need to manually resolve the account name
collision.
	- 5801: Attempt to update DnsHostName and HOST Service Principal Name (SPN) attributes
of the computer object in Active Directory failed because this computer account
name, '%2' could not be mapped to the computer object on Domain Controller '%1'.
Not having SPNs registered may result in authentication failures for this computer.
Contact your domain administrator. The following technical information may be
useful for the resolution of this failure:
DsCrackNames status = 0x%3, crack error = 0x%4.
	- 5802: None of the IP addresses (%2) of this Domain Controller map to the configured site '%1'.
While this may be a temporary situation due to IP address changes, it is generally
recommended that the IP address of the Domain Controller (accessible to machines in
its domain) maps to the Site which it services. If the above list of IP addresses is
stable, consider moving this server to a site (or create one if it does not already
exist) such that the above IP address maps to the selected site. This may require the
creation of a new subnet object (whose range includes the above IP address) which maps
to the selected site object.
	- 5803: The following error occurred while reading a parameter '%2' in the
Netlogon %1 registry section:
%3
	- 5804: The Netlogon %1 registry key contains an invalid value 0x%2 for parameter '%3'.
The minimum and maximum values allowed for this parameter are 0x%4 and 0x%5, respectively.
The value of 0x%6 has been assigned to this parameter.
	- 5805: The session setup from the computer %1 failed to authenticate.
The following error occurred: 
%2
	- 5806: Dynamic DNS updates have been manually disabled on this domain controller.
USER ACTION
Reconfigure this domain controller to use dynamic DNS updates or manually add the DNS
records from the file '%SystemRoot%\System32\Config\Netlogon.dns' to the DNS database.
	- 5807: During the past %1 hours there have been %2 connections to this Domain
Controller from client machines whose IP addresses don't map to any of
the existing sites in the enterprise. Those clients, therefore, have
undefined sites and may connect to any Domain Controller including
those that are in far distant locations from the clients. A client's site
is determined by the mapping of its subnet to one of the existing sites.
To move the above clients to one of the sites, please consider creating
subnet object(s) covering the above IP addresses with mapping to one of the
existing sites.  The names and IP addresses of the clients in question have
been logged on this computer in the following log file
'%SystemRoot%\debug\netlogon.log' and, potentially, in the log file
'%SystemRoot%\debug\netlogon.bak' created if the former log becomes full.
The log(s) may contain additional unrelated debugging information. To filter
out the needed information, please search for lines which contain text
'NO_CLIENT_SITE:'. The first word after this string is the client name and
the second word is the client IP address. The maximum size of the log(s) is
controlled by the following registry DWORD value
'HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Netlogon\Parameters\LogFileMaxSize';
the default is %3 bytes.  The current maximum size is %4 bytes.  To set a
different maximum size, create the above registry value and set the desired
maximum size in bytes.
	- 5808: The deregistration of some DNS domain controller locator records was aborted
at the time of this domain controller demotion because the DNS deregistrations
took too long.
USER ACTION
Manually delete the DNS records listed in the file
'%SystemRoot%\System32\Config\Netlogon.dns' from the DNS database.
	- 5809: The NetLogon service on this domain controller has been configured to use port %1
for incoming RPC connections over TCP/IP from remote machines. However, the
following error occurred when Netlogon attempted to register this port with the RPC
endpoint mapper service: 
%2 
This will prevent the NetLogon service on remote
machines from connecting to this domain controller over TCP/IP that may result in
authentication problems.
USER ACTION
The specified port is configured via the Group Policy or via a registry value 'DcTcpipPort'
under the 'HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Netlogon\Parameters'
registry key; the value configured through the Group Policy takes precedence. If the
port specified is in error, reset it to a correct value. You can also remove this
configuration for the port in which case the port will be assigned dynamically by
the endpoint mapper at the time the NetLogon service on remote machines makes RPC connections
to this domain controller. After the misconfiguration is corrected, restart the NetLogon
service on this machine and verify that this event log no longer appears.
	- 5810: During the past %1 hours, this domain controller has received %2 connections
from dual-stack IPv4/IPv6 clients with partial subnet-site mappings. A client
has a partial subnet-site mapping if its IPv4 address is mapped to a site but
its global IPv6 address is not mapped to a site, or vice versa. To ensure correct
behavior for applications running on member computers and servers that rely on
subnet-site mappings, dual-stack IPv4/IPv6 clients must have both IPv4 and global
IPv6 addresses mapped to the same site. If a partially mapped client attempts
to connect to this domain controller using its unmapped IP address, its mapped
address is used for the client's site mapping.
The log files %SystemRoot%\debug\netlogon.log or %SystemRoot%\debug\netlogon.bak
contain the name, unmapped IP address and mapped IP address for each partially
mapped client. The log files may also contain unrelated debugging information.
To locate the information pertaining to partial-subnet mappings, search for
lines that contain the text 'PARTIAL_CLIENT_SITE_MAPPING:'. The first word after
this text is the client name. Following the client name is the client's unmapped
IP address (the IP address that does not have a subnet-site mapping) and the
client's mapped IP address, which was used to return site information.
USER ACTION
Use the Active Directory Sites and Services management console (MMC) snap-in
to add the subnet mapping for the unmapped IP addresses to the same site being
used by the mapped IP addresses. When adding site mappings for IPv6 addresses,
you should use global IPv6 addresses and not for instance temporary, link-local
or site-local IPv6 addresses.
The default maximum size of the log files is %3 bytes. The current maximum
size is %4 bytes. To set a different maximum size, create the following registry
DWORD value to specify the maximum size in bytes:
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Netlogon\Parameters\LogFileMaxSize
	- 5811: The dynamic registration of the DNS record '%1' for the remote domain controller '%3'
failed on the following DNS server:
DNS server IP address: %4
Returned Response Code (RCODE): %5
Returned Status Code: %6
For computers and users to locate the domain controller '%3', this record must be
registered in DNS.
USER ACTION
Determine what might have caused this failure, resolve the problem, and initiate
registration of the DNS records by the domain controller '%3'. For help with determining
and resolving the problem, see Help and Support for information about troubleshooting
DNS. To initiate registration of the DNS records by the domain controller '%3', run
'nltest.exe /dsregdns' from the command prompt on the domain controller '%3' or restart
the Net Logon service on the domain controller '%3'. Nltest.exe is a command line tool
that is built into Windows Server.
 As a workaround, you can manually add this record to DNS, but it is not recommended
because you then must manually update any changes it requires hereafter.
ADDITIONAL DATA
Error Value: %2
	- 5812: The dynamic deregistration of the DNS record '%1' for the remote domain controller
'%3' failed on the following DNS server:
DNS server IP address: %4
Returned Response Code (RCODE): %5
Returned Status Code: %6
USER ACTION
To prevent remote computers from attempting to connect to the domain controller '%3'
using an invalid record, delete the record '%1' manually or troubleshoot the root cause
behind the dynamic deregistration failure. To learn more about troubleshooting DNS, see
Help and Support.
ADDITIONAL DATA
Error Value: %2
	- 5813: The dynamic registration request for the DNS record '%1' has been rejected by the
remote domain controller '%2'. Error: '%3'
For computers and users to locate this domain controller, this record must be
registered in DNS. If the problem persists, please contact your domain administrator.
	- 5814: The dynamic deregistration request of the DNS record '%1' has been rejected by the
remote domain controller '%2'. Error: '%3'
To prevent remote computers from connecting unnecessarily to this domain controller,
an administrator with sufficient privileges must manually delete the record on the DNS
server that hosts it.
	- 5815: The remoting of the dynamic update request for the local domain controller's DNS records
through a secure session has failed with error '%1'.
For other computers and member servers to locate this domain controller, the appropriate
records must be registered in DNS. On this domain controller, look for events related to
failure to set up a secure session to determine why the request is failing. If the problem
persists, please contact your domain administrator.
	- 5816: Netlogon has failed an authentication request of account %1 in domain %2. The request timed out before it
could be sent to domain controller %3 in domain %4. This is the first failure. If the problem continues,
consolidated events will be logged about every %5 minutes.
Please see http://support.microsoft.com/kb/2654097 for more information.
	- 5817: Netlogon has failed an additional %1 authentication requests in the last %2 minutes.
The requests timed out before they could be sent to domain controller %3 in domain %4.
Please see http://support.microsoft.com/kb/2654097 for more information.
	- 5818: Netlogon took more than %1 seconds for an authentication request of account %2 in domain %3, through
domain controller %4 in domain %5. This is the first warning. If the problem persists, a recurring event will be logged
every %6 minutes.
Please see http://support.microsoft.com/kb/2654097 for more information on this error.
	- 5819: Netlogon took more than %1 seconds for %2 authentication requests through domain controller %3 in domain %4 in the last %5 minutes.
Please see http://support.microsoft.com/kb/2654097 for more information.
	- 5820: The Netlogon service could not add the AuthZ RPC interface.  The
service was terminated. The following error occurred: '%1'
	- 5821: The Netlogon service failed to initialize the AuthZ resource manager.
The service was terminated. The following error occurred: '%1'.
	- 5822: The Netlogon service failed to initialize the security descriptor
for the Netlogon RPC interface.   The service was terminated. The
following error occurred: '%1'.
	- 5823: The system successfully changed its password on the domain controller %1.
This event is logged when the password for the computer account is
changed by the system. It is logged on the computer that changed the
password.
	- 5824: The system successfully changed the password for managed service account %1
on the domain controller %2.
This event is logged when the password for a standalone managed service
account is changed by the system. It is logged on the computer that
changed the password.
	- 5825: The system failed to lowercase the currently configured host name. This
conversion failed with the error code below. This may affect the system's
ability to register SRV records, potentially affecting clients' ability
to locate domain controllers.
Error code: %1
More information is available at https://aka.ms/lowercasehostnamesrvrecord
	- 5826: The Netlogon service detected a non-windows account using secure RPC.
 Machine SamAccountName: %1
 Domain: %2
 Account Type: %3
 Machine Os: %4
 Machine Os Build Version: %5
 Machine Os Service Pack: %6
	- 5827: The Netlogon service denied a vulnerable Netlogon secure channel connection from a machine account.
 Machine SamAccountName: %1
 Domain: %2
 Account Type: %3
 Machine Operating System: %4
 Machine Operating System Build: %5
 Machine Operating System Service Pack: %6
For more information about why this was denied, please visit  https://go.microsoft.com/fwlink/?linkid=2133485.
	- 5828: The Netlogon service denied a vulnerable Netlogon secure channel connection using a trust account.
 Account Type: %1
 Trust Name: %2
 Trust Target: %3
 Client IP Address: %4
For more information about why this was denied, please visit  https://go.microsoft.com/fwlink/?linkid=2133485.
	- 5829: The Netlogon service allowed a vulnerable Netlogon secure channel connection.
Warning: This connection will be denied once the enforcement phase is released. To better understand the enforcement phase,
please visit  https://go.microsoft.com/fwlink/?linkid=2133485.
 Machine SamAccountName: %1
 Domain: %2
 Account Type: %3
 Machine Operating System: %4
 Machine Operating System Build: %5
 Machine Operating System Service Pack: %6
	- 5830: The Netlogon service allowed a vulnerable Netlogon secure channel connection because the machine account is allowed in the
"Domain controller: Allow vulnerable Netlogon secure channel connections" group policy.
Warning: Using vulnerable Netlogon secure channels will expose the domain-joined devices to attack. To protect your device from attack,
remove a machine account from "Domain controller: Allow vulnerable Netlogon secure channel connections" group policy after the third-party
Netlogon client has been updated. To better understand the risk of configuring machine accounts to be allowed to use vulnerable Netlogon
secure channel connections, please visit  https://go.microsoft.com/fwlink/?linkid=2133485.
 Machine SamAccountName: %1
 Domain: %2
 Account Type: %3
 Machine Os: %4
 Machine Os Build Version: %5
 Machine Os Service Pack: %6
	- 5831: The Netlogon service allowed a vulnerable Netlogon secure channel connection because the trust account is allowed in the
"Domain controller: Allow vulnerable Netlogon secure channel connections" group policy.
Warning: Using vulnerable Netlogon secure channels will expose Active Directory forests to attack. To protect your
Active Directory forests from attack, all trusts must use secure RPC with Netlogon secure channel. Remove a trust account from
"Domain controller: Allow vulnerable Netlogon secure channel connections" group policy after the third-party Netlogon client on the domain controllers
have been updated. To better understand the risk of configuring trust accounts to be allowed to use vulnerable Netlogon secure channel connections,
please visit  https://go.microsoft.com/fwlink/?linkid=2133485.
 Account Type: %1
 Trust Name: %2
 Trust Target: %3
 Client IP Address: %4
	- 5832: The Netlogon service allowed one or more unsecure pass-through NTLM authentication requests from trusted domains and/or forests
during the most recent event throttling window. These unsecure requests would normally be blocked but were allowed to proceed
due to the current trust configuration.
Warning: Allowing unsecure pass-through authentication requests will expose your Active Directory forest to attack.
For more information about this issue please visit https://go.microsoft.com/fwlink/?linkid=276811&.
Count of unsecure requests allowed due to administrative override: %1
	- 5833: The Netlogon service blocked one or more unsecure pass-through NTLM authentication requests from trusted clients, domains,
and/or forests during the most recent event throttling window. For more information about this issue, including how to enable
more verbose logging, please visit https://go.microsoft.com/fwlink/?linkid=276811&.
Count of unsecure requests blocked: %1
	- 5834: The Netlogon service allowed an unsecure pass-through NTLM authentication request from a trusted client, domain,
or forest. This unsecure request would normally be blocked but was allowed to proceed due to the current trust
configuration.
Warning: Allowing unsecure pass-through authentication requests will expose your Active Directory forest to attack.
For more information about this issue please visit https://go.microsoft.com/fwlink/?linkid=276811&.
Account name: %1
Trust name: %2
Trust type: %3
Client IP Address: %4
Block reason: %5
Resource server Netbios name: %6
Resource server DNS name: %7
Resource domain Netbios name: %8
Resource domain DNS name: %9
	- 5835: The Netlogon service blocked an unsecure pass-through NTLM authentication requests from a trusted client, domain,
or forest. For more information, please visit https://go.microsoft.com/fwlink/?linkid=276811&.
Account name: %1
Trust name: %2
Trust type: %3
Client IP Address: %4
Block reason: %5
Resource server Netbios name: %6
Resource server DNS name: %7
Resource domain Netbios name: %8
Resource domain DNS name: %9
	- 5836: The Netlogon service was able to bind to a TCP/IP port with the configured backlog size of %1.
	- 5837: The Netlogon service tried to bind to a TCP/IP port with the configured backlog size of %1 but failed. 
More information can be found in the following log file '%SystemRoot%\debug\netlogon.log' and, potentially, in the log file
'%SystemRoot%\debug\netlogon.bak' created if the former log becomes full. For steps in enabling the log, please visit
https://go.microsoft.com/fwlink/?linkid=2163327
	- 5838: The Netlogon service encountered a client using RPC signing instead of RPC sealing.
 Machine SamAccountName: %1
 Domain: %2
 Account Type: %3
 Machine Operating System: %4
 Machine Operating System Build: %5
 Machine Operating System Service Pack: %6
 Client IP Address: %7
For more information about the impact of this, please visit  https://go.microsoft.com/fwlink/?linkid=2209514.
	- 5839: The Netlogon service encountered a trust using RPC signing instead of RPC sealing.
 Account Type: %1
 Trust Name: %2
 Trust Target: %3
 Client IP Address: %4
For more information about the impact of this, please visit  https://go.microsoft.com/fwlink/?linkid=2209514.
	- 5840: The Netlogon service created a secure channel with a client with RC4.
 Account Name: %1
 Domain: %2
 Account Type: %3
 Client IP Address: %4
 Negotiated Flags: %5
For more information about why this was logged, please visit  https://go.microsoft.com/fwlink/?linkid=2209514.
	- 5841: The Netlogon service denied a client using RC4 due to the 'RejectMd5Clients' setting.
 Account Name: %1
 Domain: %2
 Account Type: %3
 Client IP Address: %4
 Negotiated Flags: %5
For more information about why this was denied, please visit  https://go.microsoft.com/fwlink/?linkid=2209514.
	- 5890: An operation was attempted that is incompatible with the current membership state of the node.
	- 5891: The quorum resource does not contain the quorum log.
	- 5892: The membership engine requested shutdown of the cluster service on this node.
	- 5893: The join operation failed because the cluster instance ID of the joining node does not match the cluster instance ID of the sponsor node.
	- 5894: A matching cluster network for the specified IP address could not be found.
	- 5895: The actual data type of the property did not match the expected data type of the property.
	- 5896: The cluster node was evicted from the cluster successfully, but the node was not cleaned up. To determine what cleanup steps failed and how to recover, see the Failover Clustering application event log using Event Viewer.
	- 5897: Two or more parameter values specified for a resource's properties are in conflict.
	- 5898: This computer cannot be made a member of a cluster.
	- 5899: This computer cannot be made a member of a cluster because it does not have the correct version of Windows installed.
	- 5900: A cluster cannot be created with the specified cluster name because that cluster name is already in use. Specify a different name for the cluster.
	- 5901: The cluster configuration action has already been committed.
	- 5902: The cluster configuration action could not be rolled back.
	- 5903: The drive letter assigned to a system disk on one node conflicted with the drive letter assigned to a disk on another node.
	- 5904: One or more nodes in the cluster are running a version of Windows that does not support this operation.
	- 5905: The name of the corresponding computer account doesn't match the Network Name for this resource.
	- 5906: No network adapters are available.
	- 5907: The cluster node has been poisoned.
	- 5908: The group is unable to accept the request since it is moving to another node.
	- 5909: The resource type cannot accept the request since is too busy performing another operation.
	- 5910: The call to the cluster resource DLL timed out.
	- 5911: The address is not valid for an IPv6 Address resource. A global IPv6 address is required, and it must match a cluster network. Compatibility addresses are not permitted.
	- 5912: An internal cluster error occurred. A call to an invalid function was attempted.
	- 5913: A parameter value is out of acceptable range.
	- 5914: A network error occurred while sending data to another node in the cluster. The number of bytes transmitted was less than required.
	- 5915: An invalid cluster registry operation was attempted.
	- 5916: An input string of characters is not properly terminated.
	- 5917: An input string of characters is not in a valid format for the data it represents.
	- 5918: An internal cluster error occurred. A cluster database transaction was attempted while a transaction was already in progress.
	- 5919: An internal cluster error occurred. There was an attempt to commit a cluster database transaction while no transaction was in progress.
	- 5920: An internal cluster error occurred. Data was not properly initialized.
	- 5921: An error occurred while reading from a stream of data. An unexpected number of bytes was returned.
	- 5922: An error occurred while writing to a stream of data. The required number of bytes could not be written.
	- 5923: An error occurred while deserializing a stream of cluster data.
	- 5924: One or more property values for this resource are in conflict with one or more property values associated with its dependent resource(s).
	- 5925: A quorum of cluster nodes was not present to form a cluster.
	- 5926: The cluster network is not valid for an IPv6 Address resource, or it does not match the configured address.
	- 5927: The cluster network is not valid for an IPv6 Tunnel resource. Check the configuration of the IP Address resource on which the IPv6 Tunnel resource depends.
	- 5928: Quorum resource cannot reside in the Available Storage group.
	- 5929: The dependencies for this resource are nested too deeply.
	- 5930: The call into the resource DLL raised an unhandled exception.
	- 5931: The RHS process failed to initialize.
	- 5932: The Failover Clustering feature is not installed on this node.
	- 5933: The resources must be online on the same node for this operation
	- 5934: A new node can not be added since this cluster is already at its maximum number of nodes.
	- 5935: This cluster can not be created since the specified number of nodes exceeds the maximum allowed limit.
	- 5936: An attempt to use the specified cluster name failed because an enabled computer object with the given name already exists in the domain.
	- 5937: This cluster cannot be destroyed. It has non-core application groups which must be deleted before the cluster can be destroyed.
	- 5938: File share associated with file share witness resource cannot be hosted by this cluster or any of its nodes.
	- 5939: Eviction of this node is invalid at this time. Due to quorum requirements node eviction will result in cluster shutdown.
If it is the last node in the cluster, destroy cluster command should be used.
	- 5940: Only one instance of this resource type is allowed in the cluster.
	- 5941: Only one instance of this resource type is allowed per resource group.
	- 5942: The resource failed to come online due to the failure of one or more provider resources.
	- 5943: The resource has indicated that it cannot come online on any node.
	- 5944: The current operation cannot be performed on this group at this time.
	- 5945: The directory or file is not located on a cluster shared volume.
	- 5946: The Security Descriptor does not meet the requirements for a cluster.
	- 5947: There is one or more shared volumes resources configured in the cluster.
Those resources must be moved to available storage in order for operation to succeed.
	- 5948: This group or resource cannot be directly manipulated.
Use shared volume APIs to perform desired operation.
	- 5949: Back up is in progress. Please wait for backup completion before trying this operation again.
	- 5950: The path does not belong to a cluster shared volume.
	- 5951: The cluster shared volume is not locally mounted on this node.
	- 5952: The cluster watchdog is terminating.
	- 5953: A resource vetoed a move between two nodes because they are incompatible.
	- 5954: The request is invalid either because node weight cannot be changed while the cluster is in disk-only quorum mode, or because changing the node weight would violate the minimum cluster quorum requirements.
	- 5955: The resource vetoed the call.
	- 5956: Resource could not start or run because it could not reserve sufficient system resources.
	- 5957: A resource vetoed a move between two nodes because the destination currently does not have enough resources to complete the operation.
	- 5958: 
A resource vetoed a move between two nodes because the source currently does not have enough resources to complete the operation.
	- 5959: 
The requested operation can not be completed because the group is queued for an operation.
	- 5960: 
The requested operation can not be completed because a resource has locked status.
	- 5961: 
The resource cannot move to another node because a cluster shared volume vetoed the operation.
	- 5962: 
A node drain is already in progress.
	- 5963: 
Clustered storage is not connected to the node.
	- 5964: 
The disk is not configured in a way to be used with CSV. CSV disks must have at least one partition that is formatted with NTFS or REFS.
	- 5965: 
The resource must be part of the Available Storage group to complete this action.
	- 5966: 
CSVFS failed operation as volume is in redirected mode.
	- 5967: 
CSVFS failed operation as volume is not in redirected mode.
	- 5968: 
Cluster properties cannot be returned at this time.
	- 5969: 
The clustered disk resource contains software snapshot diff area that are not supported for Cluster Shared Volumes.
	- 5970: 
The operation cannot be completed because the resource is in maintenance mode.
	- 5971: 
The operation cannot be completed because of cluster affinity conflicts
	- 5972: 
The operation cannot be completed because the resource is a replica virtual machine.
	- 5973: 
The Cluster Functional Level could not be increased because not all nodes in the cluster support the updated version.
	- 5974: 
Updating the cluster functional level failed because the cluster is running in fix quorum mode.
Start additional nodes which are members of the cluster until the cluster reaches quorum and the cluster will automatically
switch out of fix quorum mode, or stop and restart the cluster without the FixQuorum switch. Once the cluster is out
of fix quorum mode retry the Update-ClusterFunctionalLevel PowerShell cmdlet to update the cluster functional level.
	- 5975: 
The cluster functional level has been successfully updated but not all features are available yet. Restart the cluster by
using the Stop-Cluster PowerShell cmdlet followed by the Start-Cluster PowerShell cmdlet and all cluster features will
be available.
	- 5976: 
The cluster is currently performing a version upgrade.
	- 5977: 
The cluster did not successfully complete the version upgrade.
	- 5978: 
The cluster node is in grace period.
	- 5979: 
The operation has failed because CSV volume was not able to recover in time specified on this file object.
	- 5980: 
The operation failed because the requested node is not currently part of active cluster membership.
	- 5981: 
The operation failed because the requested cluster resource is currently unmonitored.
	- 5982: 
The operation failed because a resource does not support running in an unmonitored state.
	- 5983: 
The operation cannot be completed because a resource participates in replication.
	- 5984: 
The operation failed because the requested cluster node has been isolated
	- 5985: 
The operation failed because the requested cluster node has been quarantined
	- 5986: 
The operation failed because the specified database update condition was not met
	- 5987: 
A clustered space is in a degraded condition and the requested action cannot be completed at this time.
	- 5988: 
The operation failed because token delegation for this control is not supported.
	- 5989: 
The operation has failed because CSV has invalidated this file object.
	- 5990: 
This operation is supported only on the CSV coordinator node.
	- 5991: 
The cluster group set is not available for any further requests.
	- 5992: 
The cluster group set could not be found.
	- 5993: 
The action cannot be completed at this time because the cluster group set would fall below quorum and not be able to act as a provider.
	- 5994: 
The specified parent fault domain is not found.
	- 5995: 
The fault domain cannot be a child of the parent specified.
	- 5996: 
Storage Spaces Direct has rejected the proposed fault domain changes because it impacts the fault tolerance of the storage.
	- 5997: 
Storage Spaces Direct has rejected the proposed fault domain changes because it reduces the storage connected to the system.
	- 5998: 
Cluster infrastructure file server creation failed because a valid non-empty file server name was not provided.
	- 5999: 
The action cannot be completed because the cluster set management cluster is unreachable.
	- 6000: The specified file could not be encrypted.
	- 6001: The specified file could not be decrypted.
	- 6002: The specified file is encrypted and the user does not have the ability to decrypt it.
	- 6003: There is no valid encryption recovery policy configured for this system.
	- 6004: The required encryption driver is not loaded for this system.
	- 6005: The file was encrypted with a different encryption driver than is currently loaded.
	- 6006: There are no EFS keys defined for the user.
	- 6007: The specified file is not encrypted.
	- 6008: The specified file is not in the defined EFS export format.
	- 6009: The specified file is read only.
	- 6010: The directory has been disabled for encryption.
	- 6011: The server is not trusted for remote encryption operation.
	- 6012: Recovery policy configured for this system contains invalid recovery certificate.
	- 6013: The encryption algorithm used on the source file needs a bigger key buffer than the one on the destination file.
	- 6014: The disk partition does not support file encryption.
	- 6015: This machine is disabled for file encryption.
	- 6016: A newer system is required to decrypt this encrypted file.
	- 6017: The remote server sent an invalid response for a file being opened with Client Side Encryption.
	- 6018: Client Side Encryption is not supported by the remote server even though it claims to support it.
	- 6019: File is encrypted and should be opened in Client Side Encryption mode.
	- 6020: A new encrypted file is being created and a $EFS needs to be provided.
	- 6021: The SMB client requested a CSE FSCTL on a non-CSE file.
	- 6022: The requested operation was blocked by policy. For more information, contact your system administrator.
	- 6023: The specified file could not be encrypted with Windows Information Protection.
	- 6118: The list of servers for this workgroup is not currently available
	- 6200: The Task Scheduler service must be configured to run in the System account to function properly. Individual tasks may be configured to run in other accounts.
	- 6250: 
The object cannot be deleted from the local cluster because it is registered with the cluster set.
	- 6600: Log service encountered an invalid log sector.
	- 6601: Log service encountered a log sector with invalid block parity.
	- 6602: Log service encountered a remapped log sector.
	- 6603: Log service encountered a partial or incomplete log block.
	- 6604: Log service encountered an attempt access data outside the active log range.
	- 6605: Log service user marshalling buffers are exhausted.
	- 6606: Log service encountered an attempt read from a marshalling area with an invalid read context.
	- 6607: Log service encountered an invalid log restart area.
	- 6608: Log service encountered an invalid log block version.
	- 6609: Log service encountered an invalid log block.
	- 6610: Log service encountered an attempt to read the log with an invalid read mode.
	- 6611: Log service encountered a log stream with no restart area.
	- 6612: Log service encountered a corrupted metadata file.
	- 6613: Log service encountered a metadata file that could not be created by the log file system.
	- 6614: Log service encountered a metadata file with inconsistent data.
	- 6615: Log service encountered an attempt to erroneous allocate or dispose reservation space.
	- 6616: Log service cannot delete log file or file system container.
	- 6617: Log service has reached the maximum allowable containers allocated to a log file.
	- 6618: Log service has attempted to read or write backward past the start of the log.
	- 6619: Log policy could not be installed because a policy of the same type is already present.
	- 6620: Log policy in question was not installed at the time of the request.
	- 6621: The installed set of policies on the log is invalid.
	- 6622: A policy on the log in question prevented the operation from completing.
	- 6623: Log space cannot be reclaimed because the log is pinned by the archive tail.
	- 6624: Log record is not a record in the log file.
	- 6625: Number of reserved log records or the adjustment of the number of reserved log records is invalid.
	- 6626: Reserved log space or the adjustment of the log space is invalid.
	- 6627: An new or existing archive tail or base of the active log is invalid.
	- 6628: Log space is exhausted.
	- 6629: The log could not be set to the requested size.
	- 6630: Log is multiplexed, no direct writes to the physical log is allowed.
	- 6631: The operation failed because the log is a dedicated log.
	- 6632: The operation requires an archive context.
	- 6633: Log archival is in progress.
	- 6634: The operation requires a non-ephemeral log, but the log is ephemeral.
	- 6635: The log must have at least two containers before it can be read from or written to.
	- 6636: A log client has already registered on the stream.
	- 6637: A log client has not been registered on the stream.
	- 6638: A request has already been made to handle the log full condition.
	- 6639: Log service encountered an error when attempting to read from a log container.
	- 6640: Log service encountered an error when attempting to write to a log container.
	- 6641: Log service encountered an error when attempting open a log container.
	- 6642: Log service encountered an invalid container state when attempting a requested action.
	- 6643: Log service is not in the correct state to perform a requested action.
	- 6644: Log space cannot be reclaimed because the log is pinned.
	- 6645: Log metadata flush failed.
	- 6646: Security on the log and its containers is inconsistent.
	- 6647: Records were appended to the log or reservation changes were made, but the log could not be flushed.
	- 6648: The log is pinned due to reservation consuming most of the log space. Free some reserved records to make space available.
	- 6700: The transaction handle associated with this operation is not valid.
	- 6701: The requested operation was made in the context of a transaction that is no longer active.
	- 6702: The requested operation is not valid on the Transaction object in its current state.
	- 6703: The caller has called a response API, but the response is not expected because the TM did not issue the corresponding request to the caller.
	- 6704: It is too late to perform the requested operation, since the Transaction has already been aborted.
	- 6705: It is too late to perform the requested operation, since the Transaction has already been committed.
	- 6706: The Transaction Manager was unable to be successfully initialized. Transacted operations are not supported.
	- 6707: The specified ResourceManager made no changes or updates to the resource under this transaction.
	- 6708: The resource manager has attempted to prepare a transaction that it has not successfully joined.
	- 6709: The Transaction object already has a superior enlistment, and the caller attempted an operation that would have created a new superior. Only a single superior enlistment is allow.
	- 6710: The RM tried to register a protocol that already exists.
	- 6711: The attempt to propagate the Transaction failed.
	- 6712: The requested propagation protocol was not registered as a CRM.
	- 6713: The buffer passed in to PushTransaction or PullTransaction is not in a valid format.
	- 6714: The current transaction context associated with the thread is not a valid handle to a transaction object.
	- 6715: The specified Transaction object could not be opened, because it was not found.
	- 6716: The specified ResourceManager object could not be opened, because it was not found.
	- 6717: The specified Enlistment object could not be opened, because it was not found.
	- 6718: The specified TransactionManager object could not be opened, because it was not found.
	- 6719: The object specified could not be created or opened, because its associated TransactionManager is not online.  The TransactionManager must be brought fully Online by calling RecoverTransactionManager to recover to the end of its LogFile before objects in its Transaction or ResourceManager namespaces can be opened.  In addition, errors in writing records to its LogFile can cause a TransactionManager to go offline.
	- 6720: The specified TransactionManager was unable to create the objects contained in its logfile in the Ob namespace. Therefore, the TransactionManager was unable to recover.
	- 6721: The call to create a superior Enlistment on this Transaction object could not be completed, because the Transaction object specified for the enlistment is a subordinate branch of the Transaction. Only the root of the Transaction can be enlisted on as a superior.
	- 6722: Because the associated transaction manager or resource manager has been closed, the handle is no longer valid.
	- 6723: The specified operation could not be performed on this Superior enlistment, because the enlistment was not created with the corresponding completion response in the NotificationMask.
	- 6724: The specified operation could not be performed, because the record that would be logged was too long. This can occur because of two conditions: either there are too many Enlistments on this Transaction, or the combined RecoveryInformation being logged on behalf of those Enlistments is too long.
	- 6725: Implicit transaction are not supported.
	- 6726: The kernel transaction manager had to abort or forget the transaction because it blocked forward progress.
	- 6727: The TransactionManager identity that was supplied did not match the one recorded in the TransactionManager's log file.
	- 6728: This snapshot operation cannot continue because a transactional resource manager cannot be frozen in its current state.  Please try again.
	- 6729: The transaction cannot be enlisted on with the specified EnlistmentMask, because the transaction has already completed the PrePrepare phase.  In order to ensure correctness, the ResourceManager must switch to a write-through mode and cease caching data within this transaction.  Enlisting for only subsequent transaction phases may still succeed.
	- 6730: The transaction does not have a superior enlistment.
	- 6731: The attempt to commit the Transaction completed, but it is possible that some portion of the transaction tree did not commit successfully due to heuristics.  Therefore it is possible that some data modified in the transaction may not have committed, resulting in transactional inconsistency.  If possible, check the consistency of the associated data.
	- 6800: The function attempted to use a name that is reserved for use by another transaction.
	- 6801: Transaction support within the specified resource manager is not started or was shut down due to an error.
	- 6802: The metadata of the RM has been corrupted. The RM will not function.
	- 6803: The specified directory does not contain a resource manager.
	- 6805: The remote server or share does not support transacted file operations.
	- 6806: The requested log size is invalid.
	- 6807: The object (file, stream, link) corresponding to the handle has been deleted by a Transaction Savepoint Rollback.
	- 6808: The specified file miniversion was not found for this transacted file open.
	- 6809: The specified file miniversion was found but has been invalidated. Most likely cause is a transaction savepoint rollback.
	- 6810: A miniversion may only be opened in the context of the transaction that created it.
	- 6811: It is not possible to open a miniversion with modify access.
	- 6812: It is not possible to create any more miniversions for this stream.
	- 6814: The remote server sent mismatching version number or Fid for a file opened with transactions.
	- 6815: The handle has been invalidated by a transaction. The most likely cause is the presence of memory mapping on a file or an open handle when the transaction ended or rolled back to savepoint.
	- 6816: There is no transaction metadata on the file.
	- 6817: The log data is corrupt.
	- 6818: The file can't be recovered because there is a handle still open on it.
	- 6819: The transaction outcome is unavailable because the resource manager responsible for it has disconnected.
	- 6820: The request was rejected because the enlistment in question is not a superior enlistment.
	- 6821: The transactional resource manager is already consistent. Recovery is not needed.
	- 6822: The transactional resource manager has already been started.
	- 6823: The file cannot be opened transactionally, because its identity depends on the outcome of an unresolved transaction.
	- 6824: The operation cannot be performed because another transaction is depending on the fact that this property will not change.
	- 6825: The operation would involve a single file with two transactional resource managers and is therefore not allowed.
	- 6826: The $Txf directory must be empty for this operation to succeed.
	- 6827: The operation would leave a transactional resource manager in an inconsistent state and is therefore not allowed.
	- 6828: The operation could not be completed because the transaction manager does not have a log.
	- 6829: A rollback could not be scheduled because a previously scheduled rollback has already executed or been queued for execution.
	- 6830: The transactional metadata attribute on the file or directory is corrupt and unreadable.
	- 6831: The encryption operation could not be completed because a transaction is active.
	- 6832: This object is not allowed to be opened in a transaction.
	- 6833: An attempt to create space in the transactional resource manager's log failed. The failure status has been recorded in the event log.
	- 6834: Memory mapping (creating a mapped section) a remote file under a transaction is not supported.
	- 6835: Transaction metadata is already present on this file and cannot be superseded.
	- 6836: A transaction scope could not be entered because the scope handler has not been initialized.
	- 6837: Promotion was required in order to allow the resource manager to enlist, but the transaction was set to disallow it.
	- 6838: This file is open for modification in an unresolved transaction and may be opened for execute only by a transacted reader.
	- 6839: The request to thaw frozen transactions was ignored because transactions had not previously been frozen.
	- 6840: Transactions cannot be frozen because a freeze is already in progress.
	- 6841: The target volume is not a snapshot volume. This operation is only valid on a volume mounted as a snapshot.
	- 6842: The savepoint operation failed because files are open on the transaction. This is not permitted.
	- 6843: Windows has discovered corruption in a file, and that file has since been repaired. Data loss may have occurred.
	- 6844: The sparse operation could not be completed because a transaction is active on the file.
	- 6845: The call to create a TransactionManager object failed because the Tm Identity stored in the logfile does not match the Tm Identity that was passed in as an argument.
	- 6846: I/O was attempted on a section object that has been floated as a result of a transaction ending. There is no valid data.
	- 6847: The transactional resource manager cannot currently accept transacted work due to a transient condition such as low resources.
	- 6848: The transactional resource manager had too many transactions outstanding that could not be aborted. The transactional resource manger has been shut down.
	- 6849: The operation could not be completed due to bad clusters on disk.
	- 6850: The compression operation could not be completed because a transaction is active on the file.
	- 6851: The operation could not be completed because the volume is dirty. Please run chkdsk and try again.
	- 6852: The link tracking operation could not be completed because a transaction is active.
	- 6853: This operation cannot be performed in a transaction.
	- 6854: The handle is no longer properly associated with its transaction.  It may have been opened in a transactional resource manager that was subsequently forced to restart.  Please close the handle and open a new one.
	- 6855: The specified operation could not be performed because the resource manager is not enlisted in the transaction.
	- 7001: The specified session name is invalid.
	- 7002: The specified protocol driver is invalid.
	- 7003: The specified protocol driver was not found in the system path.
	- 7004: The specified terminal connection driver was not found in the system path.
	- 7005: A registry key for event logging could not be created for this session.
	- 7006: A service with the same name already exists on the system.
	- 7007: A close operation is pending on the session.
	- 7008: There are no free output buffers available.
	- 7009: The MODEM.INF file was not found.
	- 7010: The modem name was not found in MODEM.INF.
	- 7011: The modem did not accept the command sent to it. Verify that the configured modem name matches the attached modem.
	- 7012: The modem did not respond to the command sent to it. Verify that the modem is properly cabled and powered on.
	- 7013: Carrier detect has failed or carrier has been dropped due to disconnect.
	- 7014: Dial tone not detected within the required time. Verify that the phone cable is properly attached and functional.
	- 7015: Busy signal detected at remote site on callback.
	- 7016: Voice detected at remote site on callback.
	- 7017: Transport driver error
	- 7022: The specified session cannot be found.
	- 7023: The specified session name is already in use.
	- 7024: The task you are trying to do can't be completed because Remote Desktop Services is currently busy. Please try again in a few minutes. Other users should still be able to log on.
	- 7025: An attempt has been made to connect to a session whose video mode is not supported by the current client.
	- 7035: The application attempted to enable DOS graphics mode. DOS graphics mode is not supported.
	- 7037: Your interactive logon privilege has been disabled. Please contact your administrator.
	- 7038: The requested operation can be performed only on the system console. This is most often the result of a driver or system DLL requiring direct console access.
	- 7040: The client failed to respond to the server connect message.
	- 7041: Disconnecting the console session is not supported.
	- 7042: Reconnecting a disconnected session to the console is not supported.
	- 7044: The request to control another session remotely was denied.
	- 7045: The requested session access is denied.
	- 7049: The specified terminal connection driver is invalid.
	- 7050: The requested session cannot be controlled remotely.
This may be because the session is disconnected or does not currently have a user logged on.
	- 7051: The requested session is not configured to allow remote control.
	- 7052: Your request to connect to this Terminal Server has been rejected. Your Terminal Server client license number is currently being used by another user. Please call your system administrator to obtain a unique license number.
	- 7053: Your request to connect to this Terminal Server has been rejected. Your Terminal Server client license number has not been entered for this copy of the Terminal Server client. Please contact your system administrator.
	- 7054: The number of connections to this computer is limited and all connections are in use right now. Try connecting later or contact your system administrator.
	- 7055: The client you are using is not licensed to use this system. Your logon request is denied.
	- 7056: The system license has expired. Your logon request is denied.
	- 7057: Remote control could not be terminated because the specified session is not currently being remotely controlled.
	- 7058: The remote control of the console was terminated because the display mode was changed. Changing the display mode in a remote control session is not supported.
	- 7059: Activation has already been reset the maximum number of times for this installation. Your activation timer will not be cleared.
	- 7060: Remote logins are currently disabled.
	- 7061: You do not have the proper encryption level to access this Session.
	- 7062: The user %s\\%s is currently logged on to this computer. Only the current user or an administrator can log on to this computer.
	- 7063: The user %s\\%s is already logged on to the console of this computer. You do not have permission to log in at this time. To resolve this issue, contact %s\\%s and have them log off.
	- 7064: Unable to log you on because of an account restriction.
	- 7065: The RDP protocol component %2 detected an error in the protocol stream and has disconnected the client.
	- 7066: The Client Drive Mapping Service Has Connected on Terminal Connection.
	- 7067: The Client Drive Mapping Service Has Disconnected on Terminal Connection.
	- 7068: The Terminal Server security layer detected an error in the protocol stream and has disconnected the client.
	- 7069: The target session is incompatible with the current session.
	- 7070: Windows can't connect to your session because a problem occurred in the Windows video subsystem. Try connecting again later, or contact the server administrator for assistance.
	- 8001: The file replication service API was called incorrectly.
	- 8002: The file replication service cannot be started.
	- 8003: The file replication service cannot be stopped.
	- 8004: The file replication service API terminated the request. The event log may have more information.
	- 8005: The file replication service terminated the request. The event log may have more information.
	- 8006: The file replication service cannot be contacted. The event log may have more information.
	- 8007: The file replication service cannot satisfy the request because the user has insufficient privileges. The event log may have more information.
	- 8008: The file replication service cannot satisfy the request because authenticated RPC is not available. The event log may have more information.
	- 8009: The file replication service cannot satisfy the request because the user has insufficient privileges on the domain controller. The event log may have more information.
	- 8010: The file replication service cannot satisfy the request because authenticated RPC is not available on the domain controller. The event log may have more information.
	- 8011: The file replication service cannot communicate with the file replication service on the domain controller. The event log may have more information.
	- 8012: The file replication service on the domain controller cannot communicate with the file replication service on this computer. The event log may have more information.
	- 8013: The file replication service cannot populate the system volume because of an internal error. The event log may have more information.
	- 8014: The file replication service cannot populate the system volume because of an internal timeout. The event log may have more information.
	- 8015: The file replication service cannot process the request. The system volume is busy with a previous request.
	- 8016: The file replication service cannot stop replicating the system volume because of an internal error. The event log may have more information.
	- 8017: The file replication service detected an invalid parameter.
	- 8200: An error occurred while installing the directory service. For more information, see the event log.
	- 8201: The directory service evaluated group memberships locally.
	- 8202: The specified directory service attribute or value does not exist.
	- 8203: The attribute syntax specified to the directory service is invalid.
	- 8204: The attribute type specified to the directory service is not defined.
	- 8205: The specified directory service attribute or value already exists.
	- 8206: The directory service is busy.
	- 8207: The directory service is unavailable.
	- 8208: The directory service was unable to allocate a relative identifier.
	- 8209: The directory service has exhausted the pool of relative identifiers.
	- 8210: The requested operation could not be performed because the directory service is not the master for that type of operation.
	- 8211: The directory service was unable to initialize the subsystem that allocates relative identifiers.
	- 8212: The requested operation did not satisfy one or more constraints associated with the class of the object.
	- 8213: The directory service can perform the requested operation only on a leaf object.
	- 8214: The directory service cannot perform the requested operation on the RDN attribute of an object.
	- 8215: The directory service detected an attempt to modify the object class of an object.
	- 8216: The requested cross-domain move operation could not be performed.
	- 8217: Unable to contact the global catalog server.
	- 8218: The policy object is shared and can only be modified at the root.
	- 8219: The policy object does not exist.
	- 8220: The requested policy information is only in the directory service.
	- 8221: A domain controller promotion is currently active.
	- 8222: A domain controller promotion is not currently active
	- 8224: An operations error occurred.
	- 8225: A protocol error occurred.
	- 8226: The time limit for this request was exceeded.
	- 8227: The size limit for this request was exceeded.
	- 8228: The administrative limit for this request was exceeded.
	- 8229: The compare response was false.
	- 8230: The compare response was true.
	- 8231: The requested authentication method is not supported by the server.
	- 8232: A more secure authentication method is required for this server.
	- 8233: Inappropriate authentication.
	- 8234: The authentication mechanism is unknown.
	- 8235: A referral was returned from the server.
	- 8236: The server does not support the requested critical extension.
	- 8237: This request requires a secure connection.
	- 8238: Inappropriate matching.
	- 8239: A constraint violation occurred.
	- 8240: There is no such object on the server.
	- 8241: There is an alias problem.
	- 8242: An invalid dn syntax has been specified.
	- 8243: The object is a leaf object.
	- 8244: There is an alias dereferencing problem.
	- 8245: The server is unwilling to process the request.
	- 8246: A loop has been detected.
	- 8247: There is a naming violation.
	- 8248: The result set is too large.
	- 8249: The operation affects multiple DSAs
	- 8250: The server is not operational.
	- 8251: A local error has occurred.
	- 8252: An encoding error has occurred.
	- 8253: A decoding error has occurred.
	- 8254: The search filter cannot be recognized.
	- 8255: One or more parameters are illegal.
	- 8256: The specified method is not supported.
	- 8257: No results were returned.
	- 8258: The specified control is not supported by the server.
	- 8259: A referral loop was detected by the client.
	- 8260: The preset referral limit was exceeded.
	- 8261: The search requires a SORT control.
	- 8262: The search results exceed the offset range specified.
	- 8263: The directory service detected the subsystem that allocates relative identifiers is disabled. This can occur as a protective mechanism when the system determines a significant portion of relative identifiers (RIDs) have been exhausted. Please see http://go.microsoft.com/fwlink/?LinkId=228610 for recommended diagnostic steps and the procedure to re-enable account creation.
	- 8301: The root object must be the head of a naming context. The root object cannot have an instantiated parent.
	- 8302: The add replica operation cannot be performed. The naming context must be writeable in order to create the replica.
	- 8303: A reference to an attribute that is not defined in the schema occurred.
	- 8304: The maximum size of an object has been exceeded.
	- 8305: An attempt was made to add an object to the directory with a name that is already in use.
	- 8306: An attempt was made to add an object of a class that does not have an RDN defined in the schema.
	- 8307: An attempt was made to add an object using an RDN that is not the RDN defined in the schema.
	- 8308: None of the requested attributes were found on the objects.
	- 8309: The user buffer is too small.
	- 8310: The attribute specified in the operation is not present on the object.
	- 8311: Illegal modify operation. Some aspect of the modification is not permitted.
	- 8312: The specified object is too large.
	- 8313: The specified instance type is not valid.
	- 8314: The operation must be performed at a master DSA.
	- 8315: The object class attribute must be specified.
	- 8316: A required attribute is missing.
	- 8317: An attempt was made to modify an object to include an attribute that is not legal for its class.
	- 8318: The specified attribute is already present on the object.
	- 8320: The specified attribute is not present, or has no values.
	- 8321: Multiple values were specified for an attribute that can have only one value.
	- 8322: A value for the attribute was not in the acceptable range of values.
	- 8323: The specified value already exists.
	- 8324: The attribute cannot be removed because it is not present on the object.
	- 8325: The attribute value cannot be removed because it is not present on the object.
	- 8326: The specified root object cannot be a subref.
	- 8327: Chaining is not permitted.
	- 8328: Chained evaluation is not permitted.
	- 8329: The operation could not be performed because the object's parent is either uninstantiated or deleted.
	- 8330: Having a parent that is an alias is not permitted. Aliases are leaf objects.
	- 8331: The object and parent must be of the same type, either both masters or both replicas.
	- 8332: The operation cannot be performed because child objects exist. This operation can only be performed on a leaf object.
	- 8333: Directory object not found.
	- 8334: The aliased object is missing.
	- 8335: The object name has bad syntax.
	- 8336: It is not permitted for an alias to refer to another alias.
	- 8337: The alias cannot be dereferenced.
	- 8338: The operation is out of scope.
	- 8339: The operation cannot continue because the object is in the process of being removed.
	- 8340: The DSA object cannot be deleted.
	- 8341: A directory service error has occurred.
	- 8342: The operation can only be performed on an internal master DSA object.
	- 8343: The object must be of class DSA.
	- 8344: Insufficient access rights to perform the operation.
	- 8345: The object cannot be added because the parent is not on the list of possible superiors.
	- 8346: Access to the attribute is not permitted because the attribute is owned by the Security Accounts Manager (SAM).
	- 8347: The name has too many parts.
	- 8348: The name is too long.
	- 8349: The name value is too long.
	- 8350: The directory service encountered an error parsing a name.
	- 8351: The directory service cannot get the attribute type for a name.
	- 8352: The name does not identify an object; the name identifies a phantom.
	- 8353: The security descriptor is too short.
	- 8354: The security descriptor is invalid.
	- 8355: Failed to create name for deleted object.
	- 8356: The parent of a new subref must exist.
	- 8357: The object must be a naming context.
	- 8358: It is not permitted to add an attribute which is owned by the system.
	- 8359: The class of the object must be structural; you cannot instantiate an abstract class.
	- 8360: The schema object could not be found.
	- 8361: A local object with this GUID (dead or alive) already exists.
	- 8362: The operation cannot be performed on a back link.
	- 8363: The cross reference for the specified naming context could not be found.
	- 8364: The operation could not be performed because the directory service is shutting down.
	- 8365: The directory service request is invalid.
	- 8366: The role owner attribute could not be read.
	- 8367: The requested FSMO operation failed. The current FSMO holder could not be contacted.
	- 8368: Modification of a DN across a naming context is not permitted.
	- 8369: The attribute cannot be modified because it is owned by the system.
	- 8370: Only the replicator can perform this function.
	- 8371: The specified class is not defined.
	- 8372: The specified class is not a subclass.
	- 8373: The name reference is invalid.
	- 8374: A cross reference already exists.
	- 8375: It is not permitted to delete a master cross reference.
	- 8376: Subtree notifications are only supported on NC heads.
	- 8377: Notification filter is too complex.
	- 8378: Schema update failed: duplicate RDN.
	- 8379: Schema update failed: duplicate OID.
	- 8380: Schema update failed: duplicate MAPI identifier.
	- 8381: Schema update failed: duplicate schema-id GUID.
	- 8382: Schema update failed: duplicate LDAP display name.
	- 8383: Schema update failed: range-lower less than range upper.
	- 8384: Schema update failed: syntax mismatch.
	- 8385: Schema deletion failed: attribute is used in must-contain.
	- 8386: Schema deletion failed: attribute is used in may-contain.
	- 8387: Schema update failed: attribute in may-contain does not exist.
	- 8388: Schema update failed: attribute in must-contain does not exist.
	- 8389: Schema update failed: class in aux-class list does not exist or is not an auxiliary class.
	- 8390: Schema update failed: class in poss-superiors does not exist.
	- 8391: Schema update failed: class in subclassof list does not exist or does not satisfy hierarchy rules.
	- 8392: Schema update failed: Rdn-Att-Id has wrong syntax.
	- 8393: Schema deletion failed: class is used as auxiliary class.
	- 8394: Schema deletion failed: class is used as sub class.
	- 8395: Schema deletion failed: class is used as poss superior.
	- 8396: Schema update failed in recalculating validation cache.
	- 8397: The tree deletion is not finished. The request must be made again to continue deleting the tree.
	- 8398: The requested delete operation could not be performed.
	- 8399: Cannot read the governs class identifier for the schema record.
	- 8400: The attribute schema has bad syntax.
	- 8401: The attribute could not be cached.
	- 8402: The class could not be cached.
	- 8403: The attribute could not be removed from the cache.
	- 8404: The class could not be removed from the cache.
	- 8405: The distinguished name attribute could not be read.
	- 8406: No superior reference has been configured for the directory service. The directory service is therefore unable to issue referrals to objects outside this forest.
	- 8407: The instance type attribute could not be retrieved.
	- 8408: An internal error has occurred.
	- 8409: A database error has occurred.
	- 8410: The attribute GOVERNSID is missing.
	- 8411: An expected attribute is missing.
	- 8412: The specified naming context is missing a cross reference.
	- 8413: A security checking error has occurred.
	- 8414: The schema is not loaded.
	- 8415: Schema allocation failed. Please check if the machine is running low on memory.
	- 8416: Failed to obtain the required syntax for the attribute schema.
	- 8417: The global catalog verification failed. The global catalog is not available or does not support the operation. Some part of the directory is currently not available.
	- 8418: The replication operation failed because of a schema mismatch between the servers involved.
	- 8419: The DSA object could not be found.
	- 8420: The naming context could not be found.
	- 8421: The naming context could not be found in the cache.
	- 8422: The child object could not be retrieved.
	- 8423: The modification was not permitted for security reasons.
	- 8424: The operation cannot replace the hidden record.
	- 8425: The hierarchy file is invalid.
	- 8426: The attempt to build the hierarchy table failed.
	- 8427: The directory configuration parameter is missing from the registry.
	- 8428: The attempt to count the address book indices failed.
	- 8429: The allocation of the hierarchy table failed.
	- 8430: The directory service encountered an internal failure.
	- 8431: The directory service encountered an unknown failure.
	- 8432: A root object requires a class of 'top'.
	- 8433: This directory server is shutting down, and cannot take ownership of new floating single-master operation roles.
	- 8434: The directory service is missing mandatory configuration information, and is unable to determine the ownership of floating single-master operation roles.
	- 8435: The directory service was unable to transfer ownership of one or more floating single-master operation roles to other servers.
	- 8436: The replication operation failed.
	- 8437: An invalid parameter was specified for this replication operation.
	- 8438: The directory service is too busy to complete the replication operation at this time.
	- 8439: The distinguished name specified for this replication operation is invalid.
	- 8440: The naming context specified for this replication operation is invalid.
	- 8441: The distinguished name specified for this replication operation already exists.
	- 8442: The replication system encountered an internal error.
	- 8443: The replication operation encountered a database inconsistency.
	- 8444: The server specified for this replication operation could not be contacted.
	- 8445: The replication operation encountered an object with an invalid instance type.
	- 8446: The replication operation failed to allocate memory.
	- 8447: The replication operation encountered an error with the mail system.
	- 8448: The replication reference information for the target server already exists.
	- 8449: The replication reference information for the target server does not exist.
	- 8450: The naming context cannot be removed because it is replicated to another server.
	- 8451: The replication operation encountered a database error.
	- 8452: The naming context is in the process of being removed or is not replicated from the specified server.
	- 8453: Replication access was denied.
	- 8454: The requested operation is not supported by this version of the directory service.
	- 8455: The replication remote procedure call was cancelled.
	- 8456: The source server is currently rejecting replication requests.
	- 8457: The destination server is currently rejecting replication requests.
	- 8458: The replication operation failed due to a collision of object names.
	- 8459: The replication source has been reinstalled.
	- 8460: The replication operation failed because a required parent object is missing.
	- 8461: The replication operation was preempted.
	- 8462: The replication synchronization attempt was abandoned because of a lack of updates.
	- 8463: The replication operation was terminated because the system is shutting down.
	- 8464: Synchronization attempt failed because the destination DC is currently waiting to synchronize new partial attributes from source. This condition is normal if a recent schema change modified the partial attribute set. The destination partial attribute set is not a subset of source partial attribute set.
	- 8465: The replication synchronization attempt failed because a master replica attempted to sync from a partial replica.
	- 8466: The server specified for this replication operation was contacted, but that server was unable to contact an additional server needed to complete the operation.
	- 8467: The version of the directory service schema of the source forest is not compatible with the version of directory service on this computer.
	- 8468: Schema update failed: An attribute with the same link identifier already exists.
	- 8469: Name translation: Generic processing error.
	- 8470: Name translation: Could not find the name or insufficient right to see name.
	- 8471: Name translation: Input name mapped to more than one output name.
	- 8472: Name translation: Input name found, but not the associated output format.
	- 8473: Name translation: Unable to resolve completely, only the domain was found.
	- 8474: Name translation: Unable to perform purely syntactical mapping at the client without going out to the wire.
	- 8475: Modification of a constructed attribute is not allowed.
	- 8476: The OM-Object-Class specified is incorrect for an attribute with the specified syntax.
	- 8477: The replication request has been posted; waiting for reply.
	- 8478: The requested operation requires a directory service, and none was available.
	- 8479: The LDAP display name of the class or attribute contains non-ASCII characters.
	- 8480: The requested search operation is only supported for base searches.
	- 8481: The search failed to retrieve attributes from the database.
	- 8482: The schema update operation tried to add a backward link attribute that has no corresponding forward link.
	- 8483: Source and destination of a cross-domain move do not agree on the object's epoch number. Either source or destination does not have the latest version of the object.
	- 8484: Source and destination of a cross-domain move do not agree on the object's current name. Either source or destination does not have the latest version of the object.
	- 8485: Source and destination for the cross-domain move operation are identical. Caller should use local move operation instead of cross-domain move operation.
	- 8486: Source and destination for a cross-domain move are not in agreement on the naming contexts in the forest. Either source or destination does not have the latest version of the Partitions container.
	- 8487: Destination of a cross-domain move is not authoritative for the destination naming context.
	- 8488: Source and destination of a cross-domain move do not agree on the identity of the source object. Either source or destination does not have the latest version of the source object.
	- 8489: Object being moved across-domains is already known to be deleted by the destination server. The source server does not have the latest version of the source object.
	- 8490: Another operation which requires exclusive access to the PDC FSMO is already in progress.
	- 8491: A cross-domain move operation failed such that two versions of the moved object exist - one each in the source and destination domains. The destination object needs to be removed to restore the system to a consistent state.
	- 8492: This object may not be moved across domain boundaries either because cross-domain moves for this class are disallowed, or the object has some special characteristics, e.g.: trust account or restricted RID, which prevent its move.
	- 8493: Can't move objects with memberships across domain boundaries as once moved, this would violate the membership conditions of the account group. Remove the object from any account group memberships and retry.
	- 8494: A naming context head must be the immediate child of another naming context head, not of an interior node.
	- 8495: The directory cannot validate the proposed naming context name because it does not hold a replica of the naming context above the proposed naming context. Please ensure that the domain naming master role is held by a server that is configured as a global catalog server, and that the server is up to date with its replication partners. (Applies only to Windows 2000 Domain Naming masters)
	- 8496: Destination domain must be in native mode.
	- 8497: The operation cannot be performed because the server does not have an infrastructure container in the domain of interest.
	- 8498: Cross-domain move of non-empty account groups is not allowed.
	- 8499: Cross-domain move of non-empty resource groups is not allowed.
	- 8500: The search flags for the attribute are invalid. The ANR bit is valid only on attributes of Unicode or Teletex strings.
	- 8501: Tree deletions starting at an object which has an NC head as a descendant are not allowed.
	- 8502: The directory service failed to lock a tree in preparation for a tree deletion because the tree was in use.
	- 8503: The directory service failed to identify the list of objects to delete while attempting a tree deletion.
	- 8504: Security Accounts Manager initialization failed because of the following error: %1.
Error Status: 0x%2. Please shutdown this system and reboot into Directory Services Restore Mode, check the event log for more detailed information.
	- 8505: Only an administrator can modify the membership list of an administrative group.
	- 8506: Cannot change the primary group ID of a domain controller account.
	- 8507: An attempt is made to modify the base schema.
	- 8508: Adding a new mandatory attribute to an existing class, deleting a mandatory attribute from an existing class, or adding an optional attribute to the special class Top that is not a backlink attribute (directly or through inheritance, for example, by adding or deleting an auxiliary class) is not allowed.
	- 8509: Schema update is not allowed on this DC because the DC is not the schema FSMO Role Owner.
	- 8510: An object of this class cannot be created under the schema container. You can only create attribute-schema and class-schema objects under the schema container.
	- 8511: The replica/child install failed to get the objectVersion attribute on the schema container on the source DC. Either the attribute is missing on the schema container or the credentials supplied do not have permission to read it.
	- 8512: The replica/child install failed to read the objectVersion attribute in the SCHEMA section of the file schema.ini in the system32 directory.
	- 8513: The specified group type is invalid.
	- 8514: You cannot nest global groups in a mixed domain if the group is security-enabled.
	- 8515: You cannot nest local groups in a mixed domain if the group is security-enabled.
	- 8516: A global group cannot have a local group as a member.
	- 8517: A global group cannot have a universal group as a member.
	- 8518: A universal group cannot have a local group as a member.
	- 8519: A global group cannot have a cross-domain member.
	- 8520: A local group cannot have another cross domain local group as a member.
	- 8521: A group with primary members cannot change to a security-disabled group.
	- 8522: The schema cache load failed to convert the string default SD on a class-schema object.
	- 8523: Only DSAs configured to be Global Catalog servers should be allowed to hold the Domain Naming Master FSMO role. (Applies only to Windows 2000 servers)
	- 8524: The DSA operation is unable to proceed because of a DNS lookup failure.
	- 8525: While processing a change to the DNS Host Name for an object, the Service Principal Name values could not be kept in sync.
	- 8526: The Security Descriptor attribute could not be read.
	- 8527: The object requested was not found, but an object with that key was found.
	- 8528: The syntax of the linked attribute being added is incorrect. Forward links can only have syntax 2.5.5.1, 2.5.5.7, and 2.5.5.14, and backlinks can only have syntax 2.5.5.1
	- 8529: Security Account Manager needs to get the boot password.
	- 8530: Security Account Manager needs to get the boot key from floppy disk.
	- 8531: Directory Service cannot start.
	- 8532: Directory Services could not start.
	- 8533: The connection between client and server requires packet privacy or better.
	- 8534: The source domain may not be in the same forest as destination.
	- 8535: The destination domain must be in the forest.
	- 8536: The operation requires that destination domain auditing be enabled.
	- 8537: The operation couldn't locate a DC for the source domain.
	- 8538: The source object must be a group or user.
	- 8539: The source object's SID already exists in destination forest.
	- 8540: The source and destination object must be of the same type.
	- 8541: Security Accounts Manager initialization failed because of the following error: %1.
Error Status: 0x%2. Click OK to shut down the system and reboot into Safe Mode. Check the event log for detailed information.
	- 8542: Schema information could not be included in the replication request.
	- 8543: The replication operation could not be completed due to a schema incompatibility.
	- 8544: The replication operation could not be completed due to a previous schema incompatibility.
	- 8545: The replication update could not be applied because either the source or the destination has not yet received information regarding a recent cross-domain move operation.
	- 8546: The requested domain could not be deleted because there exist domain controllers that still host this domain.
	- 8547: The requested operation can be performed only on a global catalog server.
	- 8548: A local group can only be a member of other local groups in the same domain.
	- 8549: Foreign security principals cannot be members of universal groups.
	- 8550: The attribute is not allowed to be replicated to the GC because of security reasons.
	- 8551: The checkpoint with the PDC could not be taken because there too many modifications being processed currently.
	- 8552: The operation requires that source domain auditing be enabled.
	- 8553: Security principal objects can only be created inside domain naming contexts.
	- 8554: A Service Principal Name (SPN) could not be constructed because the provided hostname is not in the necessary format.
	- 8555: A Filter was passed that uses constructed attributes.
	- 8556: The unicodePwd attribute value must be enclosed in double quotes.
	- 8557: Your computer could not be joined to the domain. You have exceeded the maximum number of computer accounts you are allowed to create in this domain. Contact your system administrator to have this limit reset or increased.
	- 8558: For security reasons, the operation must be run on the destination DC.
	- 8559: For security reasons, the source DC must be NT4SP4 or greater.
	- 8560: Critical Directory Service System objects cannot be deleted during tree delete operations. The tree delete may have been partially performed.
	- 8561: Directory Services could not start because of the following error: %1.
Error Status: 0x%2. Please click OK to shutdown the system. You can use the recovery console to diagnose the system further.
	- 8562: Security Accounts Manager initialization failed because of the following error: %1.
Error Status: 0x%2. Please click OK to shutdown the system. You can use the recovery console to diagnose the system further.
	- 8563: The version of the operating system is incompatible with the current AD DS forest functional level or AD LDS Configuration Set functional level. You must upgrade to a new version of the operating system before this server can become an AD DS Domain Controller or add an AD LDS Instance in this AD DS Forest or AD LDS Configuration Set.
	- 8564: The version of the operating system installed is incompatible with the current domain functional level. You must upgrade to a new version of the operating system before this server can become a domain controller in this domain.
	- 8565: The version of the operating system installed on this server no longer supports the current AD DS Forest functional level or AD LDS Configuration Set functional level. You must raise the AD DS Forest functional level or AD LDS Configuration Set functional level before this server can become an AD DS Domain Controller or an AD LDS Instance in this Forest or Configuration Set.
	- 8566: The version of the operating system installed on this server no longer supports the current domain functional level. You must raise the domain functional level before this server can become a domain controller in this domain.
	- 8567: The version of the operating system installed on this server is incompatible with the functional level of the domain or forest.
	- 8568: The functional level of the domain (or forest) cannot be raised to the requested value, because there exist one or more domain controllers in the domain (or forest) that are at a lower incompatible functional level.
	- 8569: The forest functional level cannot be raised to the requested value since one or more domains are still in mixed domain mode. All domains in the forest must be in native mode, for you to raise the forest functional level.
	- 8570: The sort order requested is not supported.
	- 8571: The requested name already exists as a unique identifier.
	- 8572: The machine account was created pre-NT4. The account needs to be recreated.
	- 8573: The database is out of version store.
	- 8574: Unable to continue operation because multiple conflicting controls were used.
	- 8575: Unable to find a valid security descriptor reference domain for this partition.
	- 8576: Schema update failed: The link identifier is reserved.
	- 8577: Schema update failed: There are no link identifiers available.
	- 8578: An account group cannot have a universal group as a member.
	- 8579: Rename or move operations on naming context heads or read-only objects are not allowed.
	- 8580: Move operations on objects in the schema naming context are not allowed.
	- 8581: A system flag has been set on the object and does not allow the object to be moved or renamed.
	- 8582: This object is not allowed to change its grandparent container. Moves are not forbidden on this object, but are restricted to sibling containers.
	- 8583: Unable to resolve completely, a referral to another forest is generated.
	- 8584: The requested action is not supported on standard server.
	- 8585: Could not access a partition of the directory service located on a remote server. Make sure at least one server is running for the partition in question.
	- 8586: The directory cannot validate the proposed naming context (or partition) name because it does not hold a replica nor can it contact a replica of the naming context above the proposed naming context. Please ensure that the parent naming context is properly registered in DNS, and at least one replica of this naming context is reachable by the Domain Naming master.
	- 8587: The thread limit for this request was exceeded.
	- 8588: The Global catalog server is not in the closest site.
	- 8589: The DS cannot derive a service principal name (SPN) with which to mutually authenticate the target server because the corresponding server object in the local DS database has no serverReference attribute.
	- 8590: The Directory Service failed to enter single user mode.
	- 8591: The Directory Service cannot parse the script because of a syntax error.
	- 8592: The Directory Service cannot process the script because of an error.
	- 8593: The directory service cannot perform the requested operation because the servers involved are of different replication epochs (which is usually related to a domain rename that is in progress).
	- 8594: The directory service binding must be renegotiated due to a change in the server extensions information.
	- 8595: Operation not allowed on a disabled cross ref.
	- 8596: Schema update failed: No values for msDS-IntId are available.
	- 8597: Schema update failed: Duplicate msDS-INtId. Retry the operation.
	- 8598: Schema deletion failed: attribute is used in rDNAttID.
	- 8599: The directory service failed to authorize the request.
	- 8600: The Directory Service cannot process the script because it is invalid.
	- 8601: The remote create cross reference operation failed on the Domain Naming Master FSMO. The operation's error is in the extended data.
	- 8602: A cross reference is in use locally with the same name.
	- 8603: The DS cannot derive a service principal name (SPN) with which to mutually authenticate the target server because the server's domain has been deleted from the forest.
	- 8604: Writeable NCs prevent this DC from demoting.
	- 8605: The requested object has a non-unique identifier and cannot be retrieved.
	- 8606: Insufficient attributes were given to create an object. This object may not exist because it may have been deleted and already garbage collected.
	- 8607: The group cannot be converted due to attribute restrictions on the requested group type.
	- 8608: Cross-domain move of non-empty basic application groups is not allowed.
	- 8609: Cross-domain move of non-empty query based application groups is not allowed.
	- 8610: The FSMO role ownership could not be verified because its directory partition has not replicated successfully with at least one replication partner.
	- 8611: The target container for a redirection of a well known object container cannot already be a special container.
	- 8612: The Directory Service cannot perform the requested operation because a domain rename operation is in progress.
	- 8613: The directory service detected a child partition below the requested partition name. The partition hierarchy must be created in a top down method.
	- 8614: The directory service cannot replicate with this server because the time since the last replication with this server has exceeded the tombstone lifetime.
	- 8615: The requested operation is not allowed on an object under the system container.
	- 8616: The LDAP servers network send queue has filled up because the client is not processing the results of its requests fast enough. No more requests will be processed until the client catches up. If the client does not catch up then it will be disconnected.
	- 8617: The scheduled replication did not take place because the system was too busy to execute the request within the schedule window. The replication queue is overloaded. Consider reducing the number of partners or decreasing the scheduled replication frequency.
	- 8618: At this time, it cannot be determined if the branch replication policy is available on the hub domain controller. Please retry at a later time to account for replication latencies.
	- 8619: The site settings object for the specified site does not exist.
	- 8620: The local account store does not contain secret material for the specified account.
	- 8621: Could not find a writable domain controller in the domain.
	- 8622: The server object for the domain controller does not exist.
	- 8623: The NTDS Settings object for the domain controller does not exist.
	- 8624: The requested search operation is not supported for ASQ searches.
	- 8625: A required audit event could not be generated for the operation.
	- 8626: The search flags for the attribute are invalid. The subtree index bit is valid only on single valued attributes.
	- 8627: The search flags for the attribute are invalid. The tuple index bit is valid only on attributes of Unicode strings.
	- 8628: The address books are nested too deeply. Failed to build the hierarchy table.
	- 8629: The specified up-to-date-ness vector is corrupt.
	- 8630: The request to replicate secrets is denied.
	- 8631: Schema update failed: The MAPI identifier is reserved.
	- 8632: Schema update failed: There are no MAPI identifiers available.
	- 8633: The replication operation failed because the required attributes of the local krbtgt object are missing.
	- 8634: The domain name of the trusted domain already exists in the forest.
	- 8635: The flat name of the trusted domain already exists in the forest.
	- 8636: The User Principal Name (UPN) is invalid.
	- 8637: OID mapped groups cannot have members.
	- 8638: The specified OID cannot be found.
	- 8639: The replication operation failed because the target object referred by a link value is recycled.
	- 8640: The redirect operation failed because the target object is in a NC different from the domain NC of the current domain controller.
	- 8641: The functional level of the AD LDS configuration set cannot be lowered to the requested value.
	- 8642: The functional level of the domain (or forest) cannot be lowered to the requested value.
	- 8643: The functional level of the AD LDS configuration set cannot be raised to the requested value, because there exist one or more ADLDS instances that are at a lower incompatible functional level.
	- 8644: The domain join cannot be completed because the SID of the domain you attempted to join was identical to the SID of this machine. This is a symptom of an improperly cloned operating system install.  You should run sysprep on this machine in order to generate a new machine SID. Please see http://go.microsoft.com/fwlink/?LinkId=168895 for more information.
	- 8645: The undelete operation failed because the Sam Account Name or Additional Sam Account Name of the object being undeleted conflicts with an existing live object.
	- 8646: The system is not authoritative for the specified account and therefore cannot complete the operation. Please retry the operation using the provider associated with this account. If this is an online provider please use the provider's online site.
	- 8647: The operation failed because SPN value provided for addition/modification is not unique forest-wide.
	- 8648: The operation failed because UPN value provided for addition/modification is not unique forest-wide.
	- 8649: The operation failed because the addition/modification referenced an inbound forest-wide trust that is not present.
	- 8650: The link value specified was not found, but a link value with that key was found.
	- 8651: The Security Account Manager blocked the use of a weak Windows Hello for Business key.
	- 8652: The add object operation failed because the caller was not authorized to add one or more attributes included in the request.
	- 8653: The local account policy modification request was rejected because the policy is controlled by a regional authority.
	- 8654: The account is controlled by external policy and cannot be modified.
	- 8655: The Local Administrator Password Solution password update operation failed because the legacy LAPS schema needs to be added to Active Directory.
	- 8656: The Local Administrator Password Solution password update operation failed because the Windows LAPS schema needs to be added to Active Directory.
	- 8657: The Local Administrator Password Solution encrypted password update operation failed because Active Directory is not yet running at the minimum required domain functional level (2016).
	- 9001: DNS server unable to interpret format.
	- 9002: DNS server failure.
	- 9003: DNS name does not exist.
	- 9004: DNS request not supported by name server.
	- 9005: DNS operation refused.
	- 9006: DNS name that ought not exist, does exist.
	- 9007: DNS RR set that ought not exist, does exist.
	- 9008: DNS RR set that ought to exist, does not exist.
	- 9009: DNS server not authoritative for zone.
	- 9010: DNS name in update or prereq is not in zone.
	- 9016: DNS signature failed to verify.
	- 9017: DNS bad key.
	- 9018: DNS signature validity expired.
	- 9101: Only the DNS server acting as the key master for the zone may perform this operation.
	- 9102: This operation is not allowed on a zone that is signed or has signing keys.
	- 9103: NSEC3 is not compatible with the RSA-SHA-1 algorithm. Choose a different algorithm or use NSEC.
	- 9104: The zone does not have enough signing keys. There must be at least one key signing key (KSK) and at least one zone signing key (ZSK).
	- 9105: The specified algorithm is not supported.
	- 9106: The specified key size is not supported.
	- 9107: One or more of the signing keys for a zone are not accessible to the DNS server. Zone signing will not be operational until this error is resolved.
	- 9108: The specified key storage provider does not support DPAPI++ data protection. Zone signing will not be operational until this error is resolved.
	- 9109: An unexpected DPAPI++ error was encountered. Zone signing will not be operational until this error is resolved.
	- 9110: An unexpected crypto error was encountered. Zone signing may not be operational until this error is resolved.
	- 9111: The DNS server encountered a signing key with an unknown version. Zone signing will not be operational until this error is resolved.
	- 9112: The specified key service provider cannot be opened by the DNS server.
	- 9113: The DNS server cannot accept any more signing keys with the specified algorithm and KSK flag value for this zone.
	- 9114: The specified rollover period is invalid.
	- 9115: The specified initial rollover offset is invalid.
	- 9116: The specified signing key is already in process of rolling over keys.
	- 9117: The specified signing key does not have a standby key to revoke.
	- 9118: This operation is not allowed on a zone signing key (ZSK).
	- 9119: This operation is not allowed on an active signing key.
	- 9120: The specified signing key is already queued for rollover.
	- 9121: This operation is not allowed on an unsigned zone.
	- 9122: This operation could not be completed because the DNS server listed as the current key master for this zone is down or misconfigured. Resolve the problem on the current key master for this zone or use another DNS server to seize the key master role.
	- 9123: The specified signature validity period is invalid.
	- 9124: The specified NSEC3 iteration count is higher than allowed by the minimum key length used in the zone.
	- 9125: This operation could not be completed because the DNS server has been configured with DNSSEC features disabled. Enable DNSSEC on the DNS server.
	- 9126: This operation could not be completed because the XML stream received is empty or syntactically invalid.
	- 9127: This operation completed, but no trust anchors were added because all of the trust anchors received were either invalid, unsupported, expired, or would not become valid in less than 30 days.
	- 9128: The specified signing key is not waiting for parental DS update.
	- 9129: Hash collision detected during NSEC3 signing. Specify a different user-provided salt, or use a randomly generated salt, and attempt to sign the zone again.
	- 9130: NSEC is not compatible with the NSEC3-RSA-SHA-1 algorithm. Choose a different algorithm or use NSEC3.
	- 9501: No records found for given DNS query.
	- 9502: Bad DNS packet.
	- 9503: No DNS packet.
	- 9504: DNS error, check rcode.
	- 9505: Unsecured DNS packet.
	- 9506: DNS query request is pending.
	- 9551: Invalid DNS type.
	- 9552: Invalid IP address.
	- 9553: Invalid property.
	- 9554: Try DNS operation again later.
	- 9555: Record for given name and type is not unique.
	- 9556: DNS name does not comply with RFC specifications.
	- 9557: DNS name is a fully-qualified DNS name.
	- 9558: DNS name is dotted (multi-label).
	- 9559: DNS name is a single-part name.
	- 9560: DNS name contains an invalid character.
	- 9561: DNS name is entirely numeric.
	- 9562: The operation requested is not permitted on a DNS root server.
	- 9563: The record could not be created because this part of the DNS namespace has been delegated to another server.
	- 9564: The DNS server could not find a set of root hints.
	- 9565: The DNS server found root hints but they were not consistent across all adapters.
	- 9566: The specified value is too small for this parameter.
	- 9567: The specified value is too large for this parameter.
	- 9568: This operation is not allowed while the DNS server is loading zones in the background. Please try again later.
	- 9569: The operation requested is not permitted on against a DNS server running on a read-only DC.
	- 9570: No data is allowed to exist underneath a DNAME record.
	- 9571: This operation requires credentials delegation.
	- 9572: Name resolution policy table has been corrupted. DNS resolution will fail until it is fixed. Contact your network administrator.
	- 9573: Not allowed to remove all addresses.
	- 9601: DNS zone does not exist.
	- 9602: DNS zone information not available.
	- 9603: Invalid operation for DNS zone.
	- 9604: Invalid DNS zone configuration.
	- 9605: DNS zone has no start of authority (SOA) record.
	- 9606: DNS zone has no Name Server (NS) record.
	- 9607: DNS zone is locked.
	- 9608: DNS zone creation failed.
	- 9609: DNS zone already exists.
	- 9610: DNS automatic zone already exists.
	- 9611: Invalid DNS zone type.
	- 9612: Secondary DNS zone requires master IP address.
	- 9613: DNS zone not secondary.
	- 9614: Need secondary IP address.
	- 9615: WINS initialization failed.
	- 9616: Need WINS servers.
	- 9617: NBTSTAT initialization call failed.
	- 9618: Invalid delete of start of authority (SOA)
	- 9619: A conditional forwarding zone already exists for that name.
	- 9620: This zone must be configured with one or more master DNS server IP addresses.
	- 9621: The operation cannot be performed because this zone is shut down.
	- 9622: This operation cannot be performed because the zone is currently being signed. Please try again later.
	- 9651: Primary DNS zone requires datafile.
	- 9652: Invalid datafile name for DNS zone.
	- 9653: Failed to open datafile for DNS zone.
	- 9654: Failed to write datafile for DNS zone.
	- 9655: Failure while reading datafile for DNS zone.
	- 9701: DNS record does not exist.
	- 9702: DNS record format error.
	- 9703: Node creation failure in DNS.
	- 9704: Unknown DNS record type.
	- 9705: DNS record timed out.
	- 9706: Name not in DNS zone.
	- 9707: CNAME loop detected.
	- 9708: Node is a CNAME DNS record.
	- 9709: A CNAME record already exists for given name.
	- 9710: Record only at DNS zone root.
	- 9711: DNS record already exists.
	- 9712: Secondary DNS zone data error.
	- 9713: Could not create DNS cache data.
	- 9714: DNS name does not exist.
	- 9715: Could not create pointer (PTR) record.
	- 9716: DNS domain was undeleted.
	- 9717: The directory service is unavailable.
	- 9718: DNS zone already exists in the directory service.
	- 9719: DNS server not creating or reading the boot file for the directory service integrated DNS zone.
	- 9720: Node is a DNAME DNS record.
	- 9721: A DNAME record already exists for given name.
	- 9722: An alias loop has been detected with either CNAME or DNAME records.
	- 9751: DNS AXFR (zone transfer) complete.
	- 9752: DNS zone transfer failed.
	- 9753: Added local WINS server.
	- 9801: Secure update call needs to continue update request.
	- 9851: TCP/IP network protocol not installed.
	- 9852: No DNS servers configured for local system.
	- 9901: The specified directory partition does not exist.
	- 9902: The specified directory partition already exists.
	- 9903: This DNS server is not enlisted in the specified directory partition.
	- 9904: This DNS server is already enlisted in the specified directory partition.
	- 9905: The directory partition is not available at this time. Please wait a few minutes and try again.
	- 9906: The operation failed because the domain naming master FSMO role could not be reached. The domain controller holding the domain naming master FSMO role is down or unable to service the request or is not running Windows Server 2003 or later.
	- 9911: The RRL is not enabled.
	- 9912: The window size parameter is invalid. It should be greater than or equal to 1.
	- 9913: The IPv4 prefix length parameter is invalid. It should be less than or equal to 32.
	- 9914: The IPv6 prefix length parameter is invalid. It should be less than or equal to 128.
	- 9915: The TC Rate parameter is invalid. It should be less than 10.
	- 9916: The Leak Rate parameter is invalid. It should be either 0, or between 2 and 10.
	- 9917: The Leak Rate or TC Rate parameter is invalid. Leak Rate should be greater than TC Rate.
	- 9921: The virtualization instance already exists.
	- 9922: The virtualization instance does not exist.
	- 9923: The virtualization tree is locked.
	- 9924: Invalid virtualization instance name.
	- 9925: The default virtualization instance cannot be added, removed or modified.
	- 9951: The scope already exists for the zone.
	- 9952: The scope does not exist for the zone.
	- 9953: The scope is the same as the default zone scope.
	- 9954: The scope name contains invalid characters.
	- 9955: Operation not allowed when the zone has scopes.
	- 9956: Failed to load zone scope.
	- 9957: Failed to write data file for DNS zone scope. Please verify the file exists and is writable.
	- 9958: The scope name contains invalid characters.
	- 9959: The scope does not exist.
	- 9960: The scope is the same as the default scope.
	- 9961: The operation is invalid on the scope.
	- 9962: The scope is locked.
	- 9963: The scope already exists.
	- 9971: A policy with the same name already exists on this level (server level or zone level) on the DNS server.
	- 9972: No policy with this name exists on this level (server level or zone level) on the DNS server.
	- 9973: The criteria provided in the policy are invalid.
	- 9974: At least one of the settings of this policy is invalid.
	- 9975: The client subnet cannot be deleted while it is being accessed by a policy.
	- 9976: The client subnet does not exist on the DNS server.
	- 9977: A client subnet with this name already exists on the DNS server.
	- 9978: The IP subnet specified does not exist in the client subnet.
	- 9979: The IP subnet that is being added, already exists in the client subnet.
	- 9980: The policy is locked.
	- 9981: The weight of the scope in the policy is invalid.
	- 9982: The DNS policy name is invalid.
	- 9983: The policy is missing criteria.
	- 9984: The name of the the client subnet record is invalid.
	- 9985: Invalid policy processing order.
	- 9986: The scope information has not been provided for a policy that requires it.
	- 9987: The scope information has been provided for a policy that does not require it.
	- 9988: The server scope cannot be deleted because it is referenced by a DNS Policy.
	- 9989: The zone scope cannot be deleted because it is referenced by a DNS Policy.
	- 9990: The criterion client subnet provided in the policy is invalid.
	- 9991: The criterion transport protocol provided in the policy is invalid.
	- 9992: The criterion network protocol provided in the policy is invalid.
	- 9993: The criterion interface provided in the policy is invalid.
	- 9994: The criterion FQDN provided in the policy is invalid.
	- 9995: The criterion query type provided in the policy is invalid.
	- 9996: The criterion time of day provided in the policy is invalid.
	- 10004: A blocking operation was interrupted by a call to WSACancelBlockingCall.
	- 10009: The file handle supplied is not valid.
	- 10013: An attempt was made to access a socket in a way forbidden by its access permissions.
	- 10014: The system detected an invalid pointer address in attempting to use a pointer argument in a call.
	- 10022: An invalid argument was supplied.
	- 10024: Too many open sockets.
	- 10035: A non-blocking socket operation could not be completed immediately.
	- 10036: A blocking operation is currently executing.
	- 10037: An operation was attempted on a non-blocking socket that already had an operation in progress.
	- 10038: An operation was attempted on something that is not a socket.
	- 10039: A required address was omitted from an operation on a socket.
	- 10040: A message sent on a datagram socket was larger than the internal message buffer or some other network limit, or the buffer used to receive a datagram into was smaller than the datagram itself.
	- 10041: A protocol was specified in the socket function call that does not support the semantics of the socket type requested.
	- 10042: An unknown, invalid, or unsupported option or level was specified in a getsockopt or setsockopt call.
	- 10043: The requested protocol has not been configured into the system, or no implementation for it exists.
	- 10044: The support for the specified socket type does not exist in this address family.
	- 10045: The attempted operation is not supported for the type of object referenced.
	- 10046: The protocol family has not been configured into the system or no implementation for it exists.
	- 10047: An address incompatible with the requested protocol was used.
	- 10048: Only one usage of each socket address (protocol/network address/port) is normally permitted.
	- 10049: The requested address is not valid in its context.
	- 10050: A socket operation encountered a dead network.
	- 10051: A socket operation was attempted to an unreachable network.
	- 10052: The connection has been broken due to keep-alive activity detecting a failure while the operation was in progress.
	- 10053: An established connection was aborted by the software in your host machine.
	- 10054: An existing connection was forcibly closed by the remote host.
	- 10055: An operation on a socket could not be performed because the system lacked sufficient buffer space or because a queue was full.
	- 10056: A connect request was made on an already connected socket.
	- 10057: A request to send or receive data was disallowed because the socket is not connected and (when sending on a datagram socket using a sendto call) no address was supplied.
	- 10058: A request to send or receive data was disallowed because the socket had already been shut down in that direction with a previous shutdown call.
	- 10059: Too many references to some kernel object.
	- 10060: A connection attempt failed because the connected party did not properly respond after a period of time, or established connection failed because connected host has failed to respond.
	- 10061: No connection could be made because the target machine actively refused it.
	- 10062: Cannot translate name.
	- 10063: Name component or name was too long.
	- 10064: A socket operation failed because the destination host was down.
	- 10065: A socket operation was attempted to an unreachable host.
	- 10066: Cannot remove a directory that is not empty.
	- 10067: A Windows Sockets implementation may have a limit on the number of applications that may use it simultaneously.
	- 10068: Ran out of quota.
	- 10069: Ran out of disk quota.
	- 10070: File handle reference is no longer available.
	- 10071: Item is not available locally.
	- 10091: WSAStartup cannot function at this time because the underlying system it uses to provide network services is currently unavailable.
	- 10092: The Windows Sockets version requested is not supported.
	- 10093: Either the application has not called WSAStartup, or WSAStartup failed.
	- 10101: Returned by WSARecv or WSARecvFrom to indicate the remote party has initiated a graceful shutdown sequence.
	- 10102: No more results can be returned by WSALookupServiceNext.
	- 10103: A call to WSALookupServiceEnd was made while this call was still processing. The call has been canceled.
	- 10104: The procedure call table is invalid.
	- 10105: The requested service provider is invalid.
	- 10106: The requested service provider could not be loaded or initialized.
	- 10107: A system call has failed.
	- 10108: No such service is known. The service cannot be found in the specified name space.
	- 10109: The specified class was not found.
	- 10110: No more results can be returned by WSALookupServiceNext.
	- 10111: A call to WSALookupServiceEnd was made while this call was still processing. The call has been canceled.
	- 10112: A database query failed because it was actively refused.
	- 11001: No such host is known.
	- 11002: This is usually a temporary error during hostname resolution and means that the local server did not receive a response from an authoritative server.
	- 11003: A non-recoverable error occurred during a database lookup.
	- 11004: The requested name is valid, but no data of the requested type was found.
	- 11005: At least one reserve has arrived.
	- 11006: At least one path has arrived.
	- 11007: There are no senders.
	- 11008: There are no receivers.
	- 11009: Reserve has been confirmed.
	- 11010: Error due to lack of resources.
	- 11011: Rejected for administrative reasons - bad credentials.
	- 11012: Unknown or conflicting style.
	- 11013: Problem with some part of the filterspec or providerspecific buffer in general.
	- 11014: Problem with some part of the flowspec.
	- 11015: General QOS error.
	- 11016: An invalid or unrecognized service type was found in the flowspec.
	- 11017: An invalid or inconsistent flowspec was found in the QOS structure.
	- 11018: Invalid QOS provider-specific buffer.
	- 11019: An invalid QOS filter style was used.
	- 11020: An invalid QOS filter type was used.
	- 11021: An incorrect number of QOS FILTERSPECs were specified in the FLOWDESCRIPTOR.
	- 11022: An object with an invalid ObjectLength field was specified in the QOS provider-specific buffer.
	- 11023: An incorrect number of flow descriptors was specified in the QOS structure.
	- 11024: An unrecognized object was found in the QOS provider-specific buffer.
	- 11025: An invalid policy object was found in the QOS provider-specific buffer.
	- 11026: An invalid QOS flow descriptor was found in the flow descriptor list.
	- 11027: An invalid or inconsistent flowspec was found in the QOS provider specific buffer.
	- 11028: An invalid FILTERSPEC was found in the QOS provider-specific buffer.
	- 11029: An invalid shape discard mode object was found in the QOS provider specific buffer.
	- 11030: An invalid shaping rate object was found in the QOS provider-specific buffer.
	- 11031: A reserved policy element was found in the QOS provider-specific buffer.
	- 11032: No such host is known securely.
	- 11033: Name based IPSEC policy could not be added.
	- 13000: The specified quick mode policy already exists.
	- 13001: The specified quick mode policy was not found.
	- 13002: The specified quick mode policy is being used.
	- 13003: The specified main mode policy already exists.
	- 13004: The specified main mode policy was not found
	- 13005: The specified main mode policy is being used.
	- 13006: The specified main mode filter already exists.
	- 13007: The specified main mode filter was not found.
	- 13008: The specified transport mode filter already exists.
	- 13009: The specified transport mode filter does not exist.
	- 13010: The specified main mode authentication list exists.
	- 13011: The specified main mode authentication list was not found.
	- 13012: The specified main mode authentication list is being used.
	- 13013: The specified default main mode policy was not found.
	- 13014: The specified default main mode authentication list was not found.
	- 13015: The specified default quick mode policy was not found.
	- 13016: The specified tunnel mode filter exists.
	- 13017: The specified tunnel mode filter was not found.
	- 13018: The Main Mode filter is pending deletion.
	- 13019: The transport filter is pending deletion.
	- 13020: The tunnel filter is pending deletion.
	- 13021: The Main Mode policy is pending deletion.
	- 13022: The Main Mode authentication bundle is pending deletion.
	- 13023: The Quick Mode policy is pending deletion.
	- 13024: The Main Mode policy was successfully added, but some of the requested offers are not supported.
	- 13025: The Quick Mode policy was successfully added, but some of the requested offers are not supported.
	- 13800: ERROR_IPSEC_IKE_NEG_STATUS_BEGIN
	- 13801: IKE authentication credentials are unacceptable
	- 13802: IKE security attributes are unacceptable
	- 13803: IKE Negotiation in progress
	- 13804: General processing error
	- 13805: Negotiation timed out
	- 13806: IKE failed to find valid machine certificate. Contact your Network Security Administrator about installing a valid certificate in the appropriate Certificate Store.
	- 13807: IKE SA deleted by peer before establishment completed
	- 13808: IKE SA deleted before establishment completed
	- 13809: Negotiation request sat in Queue too long
	- 13810: Negotiation request sat in Queue too long
	- 13811: Negotiation request sat in Queue too long
	- 13812: Negotiation request sat in Queue too long
	- 13813: No response from peer
	- 13814: Negotiation took too long
	- 13815: Negotiation took too long
	- 13816: Unknown error occurred
	- 13817: Certificate Revocation Check failed
	- 13818: Invalid certificate key usage
	- 13819: Invalid certificate type
	- 13820: IKE negotiation failed because the machine certificate used does not have a private key. IPsec certificates require a private key. Contact your Network Security administrator about replacing with a certificate that has a private key.
	- 13821: Simultaneous rekeys were detected.
	- 13822: Failure in Diffie-Hellman computation
	- 13823: Don't know how to process critical payload
	- 13824: Invalid header
	- 13825: No policy configured
	- 13826: Failed to verify signature
	- 13827: Failed to authenticate using Kerberos
	- 13828: Peer's certificate did not have a public key
	- 13829: Error processing error payload
	- 13830: Error processing SA payload
	- 13831: Error processing Proposal payload
	- 13832: Error processing Transform payload
	- 13833: Error processing KE payload
	- 13834: Error processing ID payload
	- 13835: Error processing Cert payload
	- 13836: Error processing Certificate Request payload
	- 13837: Error processing Hash payload
	- 13838: Error processing Signature payload
	- 13839: Error processing Nonce payload
	- 13840: Error processing Notify payload
	- 13841: Error processing Delete Payload
	- 13842: Error processing VendorId payload
	- 13843: Invalid payload received
	- 13844: Soft SA loaded
	- 13845: Soft SA torn down
	- 13846: Invalid cookie received.
	- 13847: Peer failed to send valid machine certificate
	- 13848: Certification Revocation check of peer's certificate failed
	- 13849: New policy invalidated SAs formed with old policy
	- 13850: There is no available Main Mode IKE policy.
	- 13851: Failed to enabled TCB privilege.
	- 13852: Failed to load SECURITY.DLL.
	- 13853: Failed to obtain security function table dispatch address from SSPI.
	- 13854: Failed to query Kerberos package to obtain max token size.
	- 13855: Failed to obtain Kerberos server credentials for ISAKMP/ERROR_IPSEC_IKE service. Kerberos authentication will not function. The most likely reason for this is lack of domain membership. This is normal if your computer is a member of a workgroup.
	- 13856: Failed to determine SSPI principal name for ISAKMP/ERROR_IPSEC_IKE service (QueryCredentialsAttributes).
	- 13857: Failed to obtain new SPI for the inbound SA from IPsec driver. The most common cause for this is that the driver does not have the correct filter. Check your policy to verify the filters.
	- 13858: Given filter is invalid
	- 13859: Memory allocation failed.
	- 13860: Failed to add Security Association to IPsec Driver. The most common cause for this is if the IKE negotiation took too long to complete. If the problem persists, reduce the load on the faulting machine.
	- 13861: Invalid policy
	- 13862: Invalid DOI
	- 13863: Invalid situation
	- 13864: Diffie-Hellman failure
	- 13865: Invalid Diffie-Hellman group
	- 13866: Error encrypting payload
	- 13867: Error decrypting payload
	- 13868: Policy match error
	- 13869: Unsupported ID
	- 13870: Hash verification failed
	- 13871: Invalid hash algorithm
	- 13872: Invalid hash size
	- 13873: Invalid encryption algorithm
	- 13874: Invalid authentication algorithm
	- 13875: Invalid certificate signature
	- 13876: Load failed
	- 13877: Deleted via RPC call
	- 13878: Temporary state created to perform reinitialization. This is not a real failure.
	- 13879: The lifetime value received in the Responder Lifetime Notify is below the Windows 2000 configured minimum value. Please fix the policy on the peer machine.
	- 13880: The recipient cannot handle version of IKE specified in the header.
	- 13881: Key length in certificate is too small for configured security requirements.
	- 13882: Max number of established MM SAs to peer exceeded.
	- 13883: IKE received a policy that disables negotiation.
	- 13884: Reached maximum quick mode limit for the main mode. New main mode will be started.
	- 13885: Main mode SA lifetime expired or peer sent a main mode delete.
	- 13886: Main mode SA assumed to be invalid because peer stopped responding.
	- 13887: Certificate doesn't chain to a trusted root in IPsec policy.
	- 13888: Received unexpected message ID.
	- 13889: Received invalid authentication offers.
	- 13890: Sent DoS cookie notify to initiator.
	- 13891: IKE service is shutting down.
	- 13892: Could not verify binding between CGA address and certificate.
	- 13893: Error processing NatOA payload.
	- 13894: Parameters of the main mode are invalid for this quick mode.
	- 13895: Quick mode SA was expired by IPsec driver.
	- 13896: Too many dynamically added IKEEXT filters were detected.
	- 13897: ERROR_IPSEC_IKE_NEG_STATUS_END
	- 13898: NAP reauth succeeded and must delete the dummy NAP IKEv2 tunnel.
	- 13899: Error in assigning inner IP address to initiator in tunnel mode.
	- 13900: Require configuration payload missing.
	- 13901: A negotiation running as the security principle who issued the connection is in progress
	- 13902: SA was deleted due to IKEv1/AuthIP co-existence suppress check.
	- 13903: Incoming SA request was dropped due to peer IP address rate limiting.
	- 13904: Peer does not support MOBIKE.
	- 13905: SA establishment is not authorized.
	- 13906: SA establishment is not authorized because there is not a sufficiently strong PKINIT-based credential.
	- 13907: SA establishment is not authorized.  You may need to enter updated or different credentials such as a smartcard.
	- 13908: SA establishment is not authorized because there is not a sufficiently strong PKINIT-based credential. This might be related to certificate-to-account mapping failure for the SA.
	- 13909: ERROR_IPSEC_IKE_NEG_STATUS_EXTENDED_END
	- 13910: The SPI in the packet does not match a valid IPsec SA.
	- 13911: Packet was received on an IPsec SA whose lifetime has expired.
	- 13912: Packet was received on an IPsec SA that does not match the packet characteristics.
	- 13913: Packet sequence number replay check failed.
	- 13914: IPsec header and/or trailer in the packet is invalid.
	- 13915: IPsec integrity check failed.
	- 13916: IPsec dropped a clear text packet.
	- 13917: IPsec dropped an incoming ESP packet in authenticated firewall mode. This drop is benign.
	- 13918: IPsec dropped a packet due to DoS throttling.
	- 13925: IPsec DoS Protection matched an explicit block rule.
	- 13926: IPsec DoS Protection received an IPsec specific multicast packet which is not allowed.
	- 13927: IPsec DoS Protection received an incorrectly formatted packet.
	- 13928: IPsec DoS Protection failed to look up state.
	- 13929: IPsec DoS Protection failed to create state because the maximum number of entries allowed by policy has been reached.
	- 13930: IPsec DoS Protection received an IPsec negotiation packet for a keying module which is not allowed by policy.
	- 13931: IPsec DoS Protection has not been enabled.
	- 13932: IPsec DoS Protection failed to create a per internal IP rate limit queue because the maximum number of queues allowed by policy has been reached.
	- 14000: The requested section was not present in the activation context.
	- 14001: The application has failed to start because its side-by-side configuration is incorrect. Please see the application event log or use the command-line sxstrace.exe tool for more detail.
	- 14002: The application binding data format is invalid.
	- 14003: The referenced assembly is not installed on your system.
	- 14004: The manifest file does not begin with the required tag and format information.
	- 14005: The manifest file contains one or more syntax errors.
	- 14006: The application attempted to activate a disabled activation context.
	- 14007: The requested lookup key was not found in any active activation context.
	- 14008: A component version required by the application conflicts with another component version already active.
	- 14009: The type requested activation context section does not match the query API used.
	- 14010: Lack of system resources has required isolated activation to be disabled for the current thread of execution.
	- 14011: An attempt to set the process default activation context failed because the process default activation context was already set.
	- 14012: The encoding group identifier specified is not recognized.
	- 14013: The encoding requested is not recognized.
	- 14014: The manifest contains a reference to an invalid URI.
	- 14015: The application manifest contains a reference to a dependent assembly which is not installed
	- 14016: The manifest for an assembly used by the application has a reference to a dependent assembly which is not installed
	- 14017: The manifest contains an attribute for the assembly identity which is not valid.
	- 14018: The manifest is missing the required default namespace specification on the assembly element.
	- 14019: The manifest has a default namespace specified on the assembly element but its value is not "urn:schemas-microsoft-com:asm.v1".
	- 14020: The private manifest probed has crossed a path with an unsupported reparse point.
	- 14021: Two or more components referenced directly or indirectly by the application manifest have files by the same name.
	- 14022: Two or more components referenced directly or indirectly by the application manifest have window classes with the same name.
	- 14023: Two or more components referenced directly or indirectly by the application manifest have the same COM server CLSIDs.
	- 14024: Two or more components referenced directly or indirectly by the application manifest have proxies for the same COM interface IIDs.
	- 14025: Two or more components referenced directly or indirectly by the application manifest have the same COM type library TLBIDs.
	- 14026: Two or more components referenced directly or indirectly by the application manifest have the same COM ProgIDs.
	- 14027: Two or more components referenced directly or indirectly by the application manifest are different versions of the same component which is not permitted.
	- 14028: A component's file does not match the verification information present in the component manifest.
	- 14029: The policy manifest contains one or more syntax errors.
	- 14030: Manifest Parse Error : A string literal was expected, but no opening quote character was found.
	- 14031: Manifest Parse Error : Incorrect syntax was used in a comment.
	- 14032: Manifest Parse Error : A name was started with an invalid character.
	- 14033: Manifest Parse Error : A name contained an invalid character.
	- 14034: Manifest Parse Error : A string literal contained an invalid character.
	- 14035: Manifest Parse Error : Invalid syntax for an xml declaration.
	- 14036: Manifest Parse Error : An Invalid character was found in text content.
	- 14037: Manifest Parse Error : Required white space was missing.
	- 14038: Manifest Parse Error : The character '>' was expected.
	- 14039: Manifest Parse Error : A semi colon character was expected.
	- 14040: Manifest Parse Error : Unbalanced parentheses.
	- 14041: Manifest Parse Error : Internal error.
	- 14042: Manifest Parse Error : Whitespace is not allowed at this location.
	- 14043: Manifest Parse Error : End of file reached in invalid state for current encoding.
	- 14044: Manifest Parse Error : Missing parenthesis.
	- 14045: Manifest Parse Error : A single or double closing quote character (\' or \") is missing.
	- 14046: Manifest Parse Error : Multiple colons are not allowed in a name.
	- 14047: Manifest Parse Error : Invalid character for decimal digit.
	- 14048: Manifest Parse Error : Invalid character for hexadecimal digit.
	- 14049: Manifest Parse Error : Invalid unicode character value for this platform.
	- 14050: Manifest Parse Error : Expecting whitespace or '?'.
	- 14051: Manifest Parse Error : End tag was not expected at this location.
	- 14052: Manifest Parse Error : The following tags were not closed: %1.
	- 14053: Manifest Parse Error : Duplicate attribute.
	- 14054: Manifest Parse Error : Only one top level element is allowed in an XML document.
	- 14055: Manifest Parse Error : Invalid at the top level of the document.
	- 14056: Manifest Parse Error : Invalid xml declaration.
	- 14057: Manifest Parse Error : XML document must have a top level element.
	- 14058: Manifest Parse Error : Unexpected end of file.
	- 14059: Manifest Parse Error : Parameter entities cannot be used inside markup declarations in an internal subset.
	- 14060: Manifest Parse Error : Element was not closed.
	- 14061: Manifest Parse Error : End element was missing the character '>'.
	- 14062: Manifest Parse Error : A string literal was not closed.
	- 14063: Manifest Parse Error : A comment was not closed.
	- 14064: Manifest Parse Error : A declaration was not closed.
	- 14065: Manifest Parse Error : A CDATA section was not closed.
	- 14066: Manifest Parse Error : The namespace prefix is not allowed to start with the reserved string "xml".
	- 14067: Manifest Parse Error : System does not support the specified encoding.
	- 14068: Manifest Parse Error : Switch from current encoding to specified encoding not supported.
	- 14069: Manifest Parse Error : The name 'xml' is reserved and must be lower case.
	- 14070: Manifest Parse Error : The standalone attribute must have the value 'yes' or 'no'.
	- 14071: Manifest Parse Error : The standalone attribute cannot be used in external entities.
	- 14072: Manifest Parse Error : Invalid version number.
	- 14073: Manifest Parse Error : Missing equals sign between attribute and attribute value.
	- 14074: Assembly Protection Error : Unable to recover the specified assembly.
	- 14075: Assembly Protection Error : The public key for an assembly was too short to be allowed.
	- 14076: Assembly Protection Error : The catalog for an assembly is not valid, or does not match the assembly's manifest.
	- 14077: An HRESULT could not be translated to a corresponding Win32 error code.
	- 14078: Assembly Protection Error : The catalog for an assembly is missing.
	- 14079: The supplied assembly identity is missing one or more attributes which must be present in this context.
	- 14080: The supplied assembly identity has one or more attribute names that contain characters not permitted in XML names.
	- 14081: The referenced assembly could not be found.
	- 14082: The activation context activation stack for the running thread of execution is corrupt.
	- 14083: The application isolation metadata for this process or thread has become corrupt.
	- 14084: The activation context being deactivated is not the most recently activated one.
	- 14085: The activation context being deactivated is not active for the current thread of execution.
	- 14086: The activation context being deactivated has already been deactivated.
	- 14087: A component used by the isolation facility has requested to terminate the process.
	- 14088: A kernel mode component is releasing a reference on an activation context.
	- 14089: The activation context of system default assembly could not be generated.
	- 14090: The value of an attribute in an identity is not within the legal range.
	- 14091: The name of an attribute in an identity is not within the legal range.
	- 14092: An identity contains two definitions for the same attribute.
	- 14093: The identity string is malformed. This may be due to a trailing comma, more than two unnamed attributes, missing attribute name or missing attribute value.
	- 14094: A string containing localized substitutable content was malformed. Either a dollar sign ($) was followed by something other than a left parenthesis or another dollar sign or an substitution's right parenthesis was not found.
	- 14095: The public key token does not correspond to the public key specified.
	- 14096: A substitution string had no mapping.
	- 14097: The component must be locked before making the request.
	- 14098: The component store has been corrupted.
	- 14099: An advanced installer failed during setup or servicing.
	- 14100: The character encoding in the XML declaration did not match the encoding used in the document.
	- 14101: The identities of the manifests are identical but their contents are different.
	- 14102: The component identities are different.
	- 14103: The assembly is not a deployment.
	- 14104: The file is not a part of the assembly.
	- 14105: The size of the manifest exceeds the maximum allowed.
	- 14106: The setting is not registered.
	- 14107: One or more required members of the transaction are not present.
	- 14108: The SMI primitive installer failed during setup or servicing.
	- 14109: A generic command executable returned a result that indicates failure.
	- 14110: A component is missing file verification information in its manifest.
	- 14111: Two or more components referenced directly or indirectly by the application manifest have the same WinRT ActivatableClass IDs.
	- 15000: The specified channel path is invalid.
	- 15001: The specified query is invalid.
	- 15002: The publisher metadata cannot be found in the resource.
	- 15003: The template for an event definition cannot be found in the resource (error = %1).
	- 15004: The specified publisher name is invalid.
	- 15005: The event data raised by the publisher is not compatible with the event template definition in the publisher's manifest.
	- 15007: The specified channel could not be found.
	- 15008: The specified XML text was not well-formed. See Extended Error for more details.
	- 15009: The events for a direct channel go directly to a log file and cannot be subscribed to.
	- 15010: Configuration error.
	- 15011: The query result is stale or invalid and must be recreated. This may be due to the log being cleared or rolling over after the query result was created.
	- 15012: The query result is currently at an invalid position.
	- 15013: Registered MSXML doesn't support validation.
	- 15014: An expression can only be followed by a change-of-scope operation if the expression evaluates to a node set and is not already part of another change-of-scope operation.
	- 15015: Cannot perform a step operation from a term that does not represent an element set.
	- 15016: Left-hand side arguments to binary operators must be either attributes, nodes or variables. Right-hand side arguments must be constants.
	- 15017: A step operation must involve a node test or, in the case of a predicate, an algebraic expression against which to test each node in the preceeding node set.
	- 15018: This data type is currently unsupported.
	- 15019: A syntax error occurred at position %1!d!
	- 15020: This operator is unsupported by this implementation of the filter.
	- 15021: An unexpected token was encountered.
	- 15022: The requested operation cannot be performed over an enabled direct channel. The channel must first be disabled.
	- 15023: Channel property %1 contains an invalid value. The value has an invalid type, is outside of its valid range, cannot be changed, or is not supported by this type of channel.
	- 15024: Publisher property %1 contains an invalid value. The value has an invalid type, is outside of its valid range, cannot be changed, or is not supported by this type of publisher.
	- 15025: The channel failed to activate.
	- 15026: The XPath expression exceeded the supported complexity. Simplify the expression or split it into multiple expressions.
	- 15027: The message resource is present but the message was not found in the message table.
	- 15028: The message ID for the desired message could not be found.
	- 15029: The substitution string for insert index (%1) could not be found.
	- 15030: The description string for parameter reference (%1) could not be found.
	- 15031: The maximum number of replacements has been reached.
	- 15032: The event definition could not be found for event ID (%1).
	- 15033: The locale specific resource for the desired message is not present.
	- 15034: The resource is too old and is not supported.
	- 15035: The resource is too new and is not supported.
	- 15036: The channel at index %1!d! of the query can't be opened.
	- 15037: The publisher has been disabled and its resource is not available. This usually occurs when the publisher is in the process of being uninstalled or upgraded.
	- 15038: Attempted to create a numeric type that is outside of its valid range.
	- 15080: The subscription fails to activate.
	- 15081: The log of the subscription is in disabled state, and can not be used to forward events to. The log must first be enabled before the subscription can be activated.
	- 15082: When forwarding events from local machine to itself, the query of the subscription can't contain target log of the subscription.
	- 15083: The credential store that is used to save credentials is full.
	- 15084: The credential used by this subscription can't be found in credential store.
	- 15085: No active channel is found for the query.
	- 15100: The resource loader failed to find MUI file.
	- 15101: The resource loader failed to load MUI file because the file fail to pass validation.
	- 15102: The RC Manifest is corrupted with garbage data or unsupported version or missing required item.
	- 15103: The RC Manifest has invalid culture name.
	- 15104: The RC Manifest has invalid ultimatefallback name.
	- 15105: The resource loader cache doesn't have loaded MUI entry.
	- 15106: User stopped resource enumeration.
	- 15107: UI language installation failed.
	- 15108: Locale installation failed.
	- 15110: A resource does not have default or neutral value.
	- 15111: Invalid PRI config file.
	- 15112: Invalid file type.
	- 15113: Unknown qualifier.
	- 15114: Invalid qualifier value.
	- 15115: No Candidate found.
	- 15116: The ResourceMap or NamedResource has an item that does not have default or neutral resource..
	- 15117: Invalid ResourceCandidate type.
	- 15118: Duplicate Resource Map.
	- 15119: Duplicate Entry.
	- 15120: Invalid Resource Identifier.
	- 15121: Filepath too long.
	- 15122: Unsupported directory type.
	- 15126: Invalid PRI File.
	- 15127: NamedResource Not Found.
	- 15135: ResourceMap Not Found.
	- 15136: Unsupported MRT profile type.
	- 15137: Invalid qualifier operator.
	- 15138: Unable to determine qualifier value or qualifier value has not been set.
	- 15139: Automerge is enabled in the PRI file.
	- 15140: Too many resources defined for package.
	- 15141: Resource File can not be used for merge operation.
	- 15142: Load/UnloadPriFiles cannot be used with resource packages.
	- 15143: Resource Contexts may not be created on threads that do not have a CoreWindow.
	- 15144: The singleton Resource Manager with different profile is already created.
	- 15145: The system component cannot operate given API operation
	- 15146: The resource is a direct reference to a non-default resource candidate.
	- 15147: Resource Map has been re-generated and the query string is not valid anymore.
	- 15148: The PRI files to be merged have incompatible versions.
	- 15149: The primary PRI files to be merged does not contain a schema.
	- 15150: Unable to load one of the PRI files to be merged.
	- 15151: Unable to add one of the PRI files to the merged file.
	- 15152: Unable to create the merged PRI file.
	- 15153: Packages for a PRI file merge must all be from the same package family.
	- 15154: Packages for a PRI file merge must not include multiple main packages.
	- 15155: Packages for a PRI file merge must not include bundle packages.
	- 15156: Packages for a PRI file merge must include one main package.
	- 15157: Packages for a PRI file merge must include at least one resource package.
	- 15158: Invalid name supplied for a canonical merged PRI file.
	- 15159: Unable to find the specified package.
	- 15160: No default value for language was specified.
	- 15161: An entity was defined as both resource and scope, which is not allowed.
	- 15200: The monitor returned a DDC/CI capabilities string that did not comply with the ACCESS.bus 3.0, DDC/CI 1.1 or MCCS 2 Revision 1 specification.
	- 15201: The monitor's VCP Version (0xDF) VCP code returned an invalid version value.
	- 15202: The monitor does not comply with the MCCS specification it claims to support.
	- 15203: The MCCS version in a monitor's mccs_ver capability does not match the MCCS version the monitor reports when the VCP Version (0xDF) VCP code is used.
	- 15204: The Monitor Configuration API only works with monitors that support the MCCS 1.0 specification, MCCS 2.0 specification or the MCCS 2.0 Revision 1 specification.
	- 15205: An internal Monitor Configuration API error occurred.
	- 15206: The monitor returned an invalid monitor technology type. CRT, Plasma and LCD (TFT) are examples of monitor technology types. This error implies that the monitor violated the MCCS 2.0 or MCCS 2.0 Revision 1 specification.
	- 15207: The caller of SetMonitorColorTemperature specified a color temperature that the current monitor did not support. This error implies that the monitor violated the MCCS 2.0 or MCCS 2.0 Revision 1 specification.
	- 15250: The requested system device cannot be identified due to multiple indistinguishable devices potentially matching the identification criteria.
	- 15299: The requested system device cannot be found.
	- 15300: Hash generation for the specified hash version and hash type is not enabled on the server.
	- 15301: The hash requested from the server is not available or no longer valid.
	- 15321: The secondary interrupt controller instance that manages the specified interrupt is not registered.
	- 15322: The information supplied by the GPIO client driver is invalid.
	- 15323: The version specified by the GPIO client driver is not supported.
	- 15324: The registration packet supplied by the GPIO client driver is not valid.
	- 15325: The requested operation is not supported for the specified handle.
	- 15326: The requested connect mode conflicts with an existing mode on one or more of the specified pins.
	- 15327: The interrupt requested to be unmasked is not masked.
	- 15400: The requested run level switch cannot be completed successfully.
	- 15401: The service has an invalid run level setting. The run level for a service
must not be higher than the run level of its dependent services.
	- 15402: The requested run level switch cannot be completed successfully since
one or more services will not stop or restart within the specified timeout.
	- 15403: A run level switch agent did not respond within the specified timeout.
	- 15404: A run level switch is currently in progress.
	- 15405: One or more services failed to start during the service startup phase of a run level switch.
	- 15501: The task stop request cannot be completed immediately since
task needs more time to shutdown.
	- 15600: Package could not be opened.
	- 15601: Package was not found.
	- 15602: Package data is invalid.
	- 15603: Package failed updates, dependency or conflict validation.
	- 15604: There is not enough disk space on your computer. Please free up some space and try again.
	- 15605: There was a problem downloading your product.
	- 15606: Package could not be registered.
	- 15607: Package could not be unregistered.
	- 15608: User cancelled the install request.
	- 15609: Install failed. Please contact your software vendor.
	- 15610: Removal failed. Please contact your software vendor.
	- 15611: The provided package is already installed, and reinstallation of the package was blocked. Check the AppXDeployment-Server event log for details.
	- 15612: The application cannot be started. Try reinstalling the application to fix the problem.
	- 15613: A Prerequisite for an install could not be satisfied.
	- 15614: The package repository is corrupted.
	- 15615: To install this application you need either a Windows developer license or a sideloading-enabled system.
	- 15616: The application cannot be started because it is currently updating.
	- 15617: The package deployment operation is blocked by policy. Please contact your system administrator.
	- 15618: The package could not be installed because resources it modifies are currently in use.
	- 15619: The package could not be recovered because necessary data for recovery have been corrupted.
	- 15620: The signature is invalid. To register in developer mode, AppxSignature.p7x and AppxBlockMap.xml must be valid or should not be present.
	- 15621: An error occurred while deleting the package's previously existing application data.
	- 15622: The package could not be installed because a higher version of this package is already installed.
	- 15623: An error in a system binary was detected. Try refreshing the PC to fix the problem.
	- 15624: A corrupted CLR NGEN binary was detected on the system.
	- 15625: The operation could not be resumed because necessary data for recovery have been corrupted.
	- 15626: The package could not be installed because the Windows Firewall service is not running. Enable the Windows Firewall service and try again.
	- 15627: Package move failed.
	- 15628: The deployment operation failed because the volume is not empty.
	- 15629: The deployment operation failed because the volume is offline. For a package update, the volume refers to the installed volume of all package versions.
	- 15630: The deployment operation failed because the specified volume is corrupt.
	- 15631: The deployment operation failed because the specified application needs to be registered first.
	- 15632: The deployment operation failed because the package targets the wrong processor architecture.
	- 15633: You have reached the maximum number of developer sideloaded packages allowed on this device. Please uninstall a sideloaded package and try again.
	- 15634: A main app package is required to install this optional package.  Install the main package first and try again.
	- 15635: This app package type is not supported on this filesystem
	- 15636: Package move operation is blocked until the application has finished streaming
	- 15637: A main or another optional app package has the same application ID as this optional package.  Change the application ID for the optional package to avoid conflicts.
	- 15638: This staging session has been held to allow another staging operation to be prioritized.
	- 15639: A related set cannot be updated because the updated set is invalid. All packages in the related set must be updated at the same time.
	- 15640: An optional package with a FullTrust entry point requires the main package to have the runFullTrust capability.
	- 15641: An error occurred because a user was logged off.
	- 15642: An optional package provision requires the dependency main package to also be provisioned.
	- 15643: The packages failed the SmartScreen reputation check.
	- 15644: The SmartScreen reputation check operation timed out.
	- 15645: The current deployment option is not supported.
	- 15646: Activation is blocked due to the .appinstaller update settings for this app.
	- 15647: Remote drives are not supported; use \\server\share to register a remote package.
	- 15648: Failed to process and write downloaded APPX package data to disk.
	- 15649: The deployment operation was blocked due to a per-package-family policy restricting deployments on a non-system volume. Per policy, this app must be installed to the system drive, but that's not set as the default. In Storage Settings, make the system drive the default location to save new content, then retry the install.
	- 15650: The deployment operation was blocked due to a machine-wide policy restricting deployments on a non-system volume. Per policy, this app must be installed to the system drive, but that's not set as the default. In Storage Settings, make the system drive the default location to save new content, then retry the install.
	- 15651: The deployment operation was blocked because Special profile deployment is not allowed. Please try logging into an account that is not a Special profile. You can try logging out and logging back into the current account, or try logging into a different account.
	- 15652: The deployment operation failed due to a conflicting package's mutable package directory. To install this package remove the existing package with the conflicting mutable package directory.
	- 15653: The package installation failed because a singleton resource was specified and another user with that package installed is logged in. Please make sure that all active users with the package installed are logged out and retry installation.
	- 15654: The package installation failed because a different version of the service is installed. Try installing a newer version of the package.
	- 15655: The package installation failed because a version of the service exists outside of APPX packaging. Please contact your software vendor.
	- 15656: The package installation failed because administrator privileges are required. Please contact an administrator to install this package.
	- 15657: The package deployment failed because the operation would have redirected to default account, when the caller said not to do so.
	- 15658: The package deployment failed because the package requires a capability to natively target this host.
	- 15659: The package deployment failed because its content is not valid for an unsigned package.
	- 15660: The package deployment failed because its publisher is not in the unsigned namespace.
	- 15661: The package deployment failed because its publisher is not in the signed namespace.
	- 15662: The package deployment failed because it must allow external content to be deployed with an external location.
	- 15663: A host runtime dependency resolving to a package with full trust content requires the main package to have the runFullTrust capability.
	- 15664: The package deployment failed because the package requires a capability for mandatory startup tasks.
	- 15665: Package failed host runtime dependency or conflict validation.
	- 15666: The package deployment failed because it uses a machine scope but doesn't have the required capability.
	- 15667: The package deployment failed because it uses classic compatmode but doesn't have the required capability.
	- 15668: AppxUpdateAgent attempted to stage a package that is not applicable.
	- 15669: The application cannot be started for the target user.  Please have the user explicitly install this package.
	- 15670: The provided package name does not match the expected package name. Check the AppXDeployment-Server event log for details.
	- 15671: The provided .appinstaller URI is already being used by another package family. Check the AppXDeployment-Server event log for details.
	- 15672: The package family's auto update settings are being managed at system priority and cannot be changed at default priority. Please contact your system administrator for help with the error.
	- 15700: The process has no package identity.
	- 15701: The package runtime information is corrupted.
	- 15702: The package identity is corrupted.
	- 15703: The process has no application identity.
	- 15704: One or more AppModel Runtime group policy values could not be read. Please contact your system administrator with the contents of your AppModel Runtime event log.
	- 15705: One or more AppModel Runtime group policy values are invalid. Please contact your system administrator with the contents of your AppModel Runtime event log.
	- 15706: The package is currently not available.
	- 15707: The package does not have a mutable directory.
	- 15800: Loading the state store failed.
	- 15801: Retrieving the state version for the application failed.
	- 15802: Setting the state version for the application failed.
	- 15803: Resetting the structured state of the application failed.
	- 15804: State Manager failed to open the container.
	- 15805: State Manager failed to create the container.
	- 15806: State Manager failed to delete the container.
	- 15807: State Manager failed to read the setting.
	- 15808: State Manager failed to write the setting.
	- 15809: State Manager failed to delete the setting.
	- 15810: State Manager failed to query the setting.
	- 15811: State Manager failed to read the composite setting.
	- 15812: State Manager failed to write the composite setting.
	- 15813: State Manager failed to enumerate the containers.
	- 15814: State Manager failed to enumerate the settings.
	- 15815: The size of the state manager composite setting value has exceeded the limit.
	- 15816: The size of the state manager setting value has exceeded the limit.
	- 15817: The length of the state manager setting name has exceeded the limit.
	- 15818: The length of the state manager container name has exceeded the limit.
	- 15841: This API cannot be used in the context of the caller's application type.
	- 15861: This PC does not have a valid license for the application or product.
	- 15862: The authenticated user does not have a valid license for the application or product.
	- 15863: The commerce transaction associated with this license is still pending verification.
	- 15864: The license has been revoked for this user.
