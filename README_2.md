# Windows GetLastError Messages

![Readme Card](https://github-readme-stats.vercel.app/api/pin/?username=Lateralus138&repo=Windows-GetLastError-Messages)

- [Windows GetLastError Messages](#windows-getlasterror-messages)
  - [Generation Code](#generation-code)
  - [Error list](#error-list)
    - [0x2000 - 0x3FFF : 8192 - 16383](#0x2000---0x3fff--8192---16383)

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
  for (DWORD i = 0x2000; i < 0x3FFF; i++)
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

List 1 can be found here: [README.md](./README.md). 

### 0x2000 - 0x3FFF : 8192 - 16383

Not all values have strings.

|Number|Message|
|------:|:------|
|8200|An error occurred while installing the directory service. For more information, see the event log.|
|8201|The directory service evaluated group memberships locally.|
|8202|The specified directory service attribute or value does not exist.|
|8203|The attribute syntax specified to the directory service is invalid.|
|8204|The attribute type specified to the directory service is not defined.|
|8205|The specified directory service attribute or value already exists.|
|8206|The directory service is busy.|
|8207|The directory service is unavailable.|
|8208|The directory service was unable to allocate a relative identifier.|
|8209|The directory service has exhausted the pool of relative identifiers.|
|8210|The requested operation could not be performed because the directory service is not the master for that type of operation.|
|8211|The directory service was unable to initialize the subsystem that allocates relative identifiers.|
|8212|The requested operation did not satisfy one or more constraints associated with the class of the object.|
|8213|The directory service can perform the requested operation only on a leaf object.|
|8214|The directory service cannot perform the requested operation on the RDN attribute of an object.|
|8215|The directory service detected an attempt to modify the object class of an object.|
|8216|The requested cross-domain move operation could not be performed.|
|8217|Unable to contact the global catalog server.|
|8218|The policy object is shared and can only be modified at the root.|
|8219|The policy object does not exist.|
|8220|The requested policy information is only in the directory service.|
|8221|A domain controller promotion is currently active.|
|8222|A domain controller promotion is not currently active|
|8224|An operations error occurred.|
|8225|A protocol error occurred.|
|8226|The time limit for this request was exceeded.|
|8227|The size limit for this request was exceeded.|
|8228|The administrative limit for this request was exceeded.|
|8229|The compare response was false.|
|8230|The compare response was true.|
|8231|The requested authentication method is not supported by the server.|
|8232|A more secure authentication method is required for this server.|
|8233|Inappropriate authentication.|
|8234|The authentication mechanism is unknown.|
|8235|A referral was returned from the server.|
|8236|The server does not support the requested critical extension.|
|8237|This request requires a secure connection.|
|8238|Inappropriate matching.|
|8239|A constraint violation occurred.|
|8240|There is no such object on the server.|
|8241|There is an alias problem.|
|8242|An invalid dn syntax has been specified.|
|8243|The object is a leaf object.|
|8244|There is an alias dereferencing problem.|
|8245|The server is unwilling to process the request.|
|8246|A loop has been detected.|
|8247|There is a naming violation.|
|8248|The result set is too large.|
|8249|The operation affects multiple DSAs|
|8250|The server is not operational.|
|8251|A local error has occurred.|
|8252|An encoding error has occurred.|
|8253|A decoding error has occurred.|
|8254|The search filter cannot be recognized.|
|8255|One or more parameters are illegal.|
|8256|The specified method is not supported.|
|8257|No results were returned.|
|8258|The specified control is not supported by the server.|
|8259|A referral loop was detected by the client.|
|8260|The preset referral limit was exceeded.|
|8261|The search requires a SORT control.|
|8262|The search results exceed the offset range specified.|
|8263|The directory service detected the subsystem that allocates relative identifiers is disabled. This can occur as a protective mechanism when the system determines a significant portion of relative identifiers (RIDs) have been exhausted. Please see http://go.microsoft.com/fwlink/?LinkId=228610 for recommended diagnostic steps and the procedure to re-enable account creation.|
|8301|The root object must be the head of a naming context. The root object cannot have an instantiated parent.|
|8302|The add replica operation cannot be performed. The naming context must be writeable in order to create the replica.|
|8303|A reference to an attribute that is not defined in the schema occurred.|
|8304|The maximum size of an object has been exceeded.|
|8305|An attempt was made to add an object to the directory with a name that is already in use.|
|8306|An attempt was made to add an object of a class that does not have an RDN defined in the schema.|
|8307|An attempt was made to add an object using an RDN that is not the RDN defined in the schema.|
|8308|None of the requested attributes were found on the objects.|
|8309|The user buffer is too small.|
|8310|The attribute specified in the operation is not present on the object.|
|8311|Illegal modify operation. Some aspect of the modification is not permitted.|
|8312|The specified object is too large.|
|8313|The specified instance type is not valid.|
|8314|The operation must be performed at a master DSA.|
|8315|The object class attribute must be specified.|
|8316|A required attribute is missing.|
|8317|An attempt was made to modify an object to include an attribute that is not legal for its class.|
|8318|The specified attribute is already present on the object.|
|8320|The specified attribute is not present, or has no values.|
|8321|Multiple values were specified for an attribute that can have only one value.|
|8322|A value for the attribute was not in the acceptable range of values.|
|8323|The specified value already exists.|
|8324|The attribute cannot be removed because it is not present on the object.|
|8325|The attribute value cannot be removed because it is not present on the object.|
|8326|The specified root object cannot be a subref.|
|8327|Chaining is not permitted.|
|8328|Chained evaluation is not permitted.|
|8329|The operation could not be performed because the object's parent is either uninstantiated or deleted.|
|8330|Having a parent that is an alias is not permitted. Aliases are leaf objects.|
|8331|The object and parent must be of the same type, either both masters or both replicas.|
|8332|The operation cannot be performed because child objects exist. This operation can only be performed on a leaf object.|
|8333|Directory object not found.|
|8334|The aliased object is missing.|
|8335|The object name has bad syntax.|
|8336|It is not permitted for an alias to refer to another alias.|
|8337|The alias cannot be dereferenced.|
|8338|The operation is out of scope.|
|8339|The operation cannot continue because the object is in the process of being removed.|
|8340|The DSA object cannot be deleted.|
|8341|A directory service error has occurred.|
|8342|The operation can only be performed on an internal master DSA object.|
|8343|The object must be of class DSA.|
|8344|Insufficient access rights to perform the operation.|
|8345|The object cannot be added because the parent is not on the list of possible superiors.|
|8346|Access to the attribute is not permitted because the attribute is owned by the Security Accounts Manager (SAM).|
|8347|The name has too many parts.|
|8348|The name is too long.|
|8349|The name value is too long.|
|8350|The directory service encountered an error parsing a name.|
|8351|The directory service cannot get the attribute type for a name.|
|8352|The name does not identify an object; the name identifies a phantom.|
|8353|The security descriptor is too short.|
|8354|The security descriptor is invalid.|
|8355|Failed to create name for deleted object.|
|8356|The parent of a new subref must exist.|
|8357|The object must be a naming context.|
|8358|It is not permitted to add an attribute which is owned by the system.|
|8359|The class of the object must be structural; you cannot instantiate an abstract class.|
|8360|The schema object could not be found.|
|8361|A local object with this GUID (dead or alive) already exists.|
|8362|The operation cannot be performed on a back link.|
|8363|The cross reference for the specified naming context could not be found.|
|8364|The operation could not be performed because the directory service is shutting down.|
|8365|The directory service request is invalid.|
|8366|The role owner attribute could not be read.|
|8367|The requested FSMO operation failed. The current FSMO holder could not be contacted.|
|8368|Modification of a DN across a naming context is not permitted.|
|8369|The attribute cannot be modified because it is owned by the system.|
|8370|Only the replicator can perform this function.|
|8371|The specified class is not defined.|
|8372|The specified class is not a subclass.|
|8373|The name reference is invalid.|
|8374|A cross reference already exists.|
|8375|It is not permitted to delete a master cross reference.|
|8376|Subtree notifications are only supported on NC heads.|
|8377|Notification filter is too complex.|
|8378|Schema update failed: duplicate RDN.|
|8379|Schema update failed: duplicate OID.|
|8380|Schema update failed: duplicate MAPI identifier.|
|8381|Schema update failed: duplicate schema-id GUID.|
|8382|Schema update failed: duplicate LDAP display name.|
|8383|Schema update failed: range-lower less than range upper.|
|8384|Schema update failed: syntax mismatch.|
|8385|Schema deletion failed: attribute is used in must-contain.|
|8386|Schema deletion failed: attribute is used in may-contain.|
|8387|Schema update failed: attribute in may-contain does not exist.|
|8388|Schema update failed: attribute in must-contain does not exist.|
|8389|Schema update failed: class in aux-class list does not exist or is not an auxiliary class.|
|8390|Schema update failed: class in poss-superiors does not exist.|
|8391|Schema update failed: class in subclassof list does not exist or does not satisfy hierarchy rules.|
|8392|Schema update failed: Rdn-Att-Id has wrong syntax.|
|8393|Schema deletion failed: class is used as auxiliary class.|
|8394|Schema deletion failed: class is used as sub class.|
|8395|Schema deletion failed: class is used as poss superior.|
|8396|Schema update failed in recalculating validation cache.|
|8397|The tree deletion is not finished. The request must be made again to continue deleting the tree.|
|8398|The requested delete operation could not be performed.|
|8399|Cannot read the governs class identifier for the schema record.|
|8400|The attribute schema has bad syntax.|
|8401|The attribute could not be cached.|
|8402|The class could not be cached.|
|8403|The attribute could not be removed from the cache.|
|8404|The class could not be removed from the cache.|
|8405|The distinguished name attribute could not be read.|
|8406|No superior reference has been configured for the directory service. The directory service is therefore unable to issue referrals to objects outside this forest.|
|8407|The instance type attribute could not be retrieved.|
|8408|An internal error has occurred.|
|8409|A database error has occurred.|
|8410|The attribute GOVERNSID is missing.|
|8411|An expected attribute is missing.|
|8412|The specified naming context is missing a cross reference.|
|8413|A security checking error has occurred.|
|8414|The schema is not loaded.|
|8415|Schema allocation failed. Please check if the machine is running low on memory.|
|8416|Failed to obtain the required syntax for the attribute schema.|
|8417|The global catalog verification failed. The global catalog is not available or does not support the operation. Some part of the directory is currently not available.|
|8418|The replication operation failed because of a schema mismatch between the servers involved.|
|8419|The DSA object could not be found.|
|8420|The naming context could not be found.|
|8421|The naming context could not be found in the cache.|
|8422|The child object could not be retrieved.|
|8423|The modification was not permitted for security reasons.|
|8424|The operation cannot replace the hidden record.|
|8425|The hierarchy file is invalid.|
|8426|The attempt to build the hierarchy table failed.|
|8427|The directory configuration parameter is missing from the registry.|
|8428|The attempt to count the address book indices failed.|
|8429|The allocation of the hierarchy table failed.|
|8430|The directory service encountered an internal failure.|
|8431|The directory service encountered an unknown failure.|
|8432|A root object requires a class of 'top'.|
|8433|This directory server is shutting down, and cannot take ownership of new floating single-master operation roles.|
|8434|The directory service is missing mandatory configuration information, and is unable to determine the ownership of floating single-master operation roles.|
|8435|The directory service was unable to transfer ownership of one or more floating single-master operation roles to other servers.|
|8436|The replication operation failed.|
|8437|An invalid parameter was specified for this replication operation.|
|8438|The directory service is too busy to complete the replication operation at this time.|
|8439|The distinguished name specified for this replication operation is invalid.|
|8440|The naming context specified for this replication operation is invalid.|
|8441|The distinguished name specified for this replication operation already exists.|
|8442|The replication system encountered an internal error.|
|8443|The replication operation encountered a database inconsistency.|
|8444|The server specified for this replication operation could not be contacted.|
|8445|The replication operation encountered an object with an invalid instance type.|
|8446|The replication operation failed to allocate memory.|
|8447|The replication operation encountered an error with the mail system.|
|8448|The replication reference information for the target server already exists.|
|8449|The replication reference information for the target server does not exist.|
|8450|The naming context cannot be removed because it is replicated to another server.|
|8451|The replication operation encountered a database error.|
|8452|The naming context is in the process of being removed or is not replicated from the specified server.|
|8453|Replication access was denied.|
|8454|The requested operation is not supported by this version of the directory service.|
|8455|The replication remote procedure call was cancelled.|
|8456|The source server is currently rejecting replication requests.|
|8457|The destination server is currently rejecting replication requests.|
|8458|The replication operation failed due to a collision of object names.|
|8459|The replication source has been reinstalled.|
|8460|The replication operation failed because a required parent object is missing.|
|8461|The replication operation was preempted.|
|8462|The replication synchronization attempt was abandoned because of a lack of updates.|
|8463|The replication operation was terminated because the system is shutting down.|
|8464|Synchronization attempt failed because the destination DC is currently waiting to synchronize new partial attributes from source. This condition is normal if a recent schema change modified the partial attribute set. The destination partial attribute set is not a subset of source partial attribute set.|
|8465|The replication synchronization attempt failed because a master replica attempted to sync from a partial replica.|
|8466|The server specified for this replication operation was contacted, but that server was unable to contact an additional server needed to complete the operation.|
|8467|The version of the directory service schema of the source forest is not compatible with the version of directory service on this computer.|
|8468|Schema update failed: An attribute with the same link identifier already exists.|
|8469|Name translation: Generic processing error.|
|8470|Name translation: Could not find the name or insufficient right to see name.|
|8471|Name translation: Input name mapped to more than one output name.|
|8472|Name translation: Input name found, but not the associated output format.|
|8473|Name translation: Unable to resolve completely, only the domain was found.|
|8474|Name translation: Unable to perform purely syntactical mapping at the client without going out to the wire.|
|8475|Modification of a constructed attribute is not allowed.|
|8476|The OM-Object-Class specified is incorrect for an attribute with the specified syntax.|
|8477|The replication request has been posted; waiting for reply.|
|8478|The requested operation requires a directory service, and none was available.|
|8479|The LDAP display name of the class or attribute contains non-ASCII characters.|
|8480|The requested search operation is only supported for base searches.|
|8481|The search failed to retrieve attributes from the database.|
|8482|The schema update operation tried to add a backward link attribute that has no corresponding forward link.|
|8483|Source and destination of a cross-domain move do not agree on the object's epoch number. Either source or destination does not have the latest version of the object.|
|8484|Source and destination of a cross-domain move do not agree on the object's current name. Either source or destination does not have the latest version of the object.|
|8485|Source and destination for the cross-domain move operation are identical. Caller should use local move operation instead of cross-domain move operation.|
|8486|Source and destination for a cross-domain move are not in agreement on the naming contexts in the forest. Either source or destination does not have the latest version of the Partitions container.|
|8487|Destination of a cross-domain move is not authoritative for the destination naming context.|
|8488|Source and destination of a cross-domain move do not agree on the identity of the source object. Either source or destination does not have the latest version of the source object.|
|8489|Object being moved across-domains is already known to be deleted by the destination server. The source server does not have the latest version of the source object.|
|8490|Another operation which requires exclusive access to the PDC FSMO is already in progress.|
|8491|A cross-domain move operation failed such that two versions of the moved object exist - one each in the source and destination domains. The destination object needs to be removed to restore the system to a consistent state.|
|8492|This object may not be moved across domain boundaries either because cross-domain moves for this class are disallowed, or the object has some special characteristics, e.g.: trust account or restricted RID, which prevent its move.|
|8493|Can't move objects with memberships across domain boundaries as once moved, this would violate the membership conditions of the account group. Remove the object from any account group memberships and retry.|
|8494|A naming context head must be the immediate child of another naming context head, not of an interior node.|
|8495|The directory cannot validate the proposed naming context name because it does not hold a replica of the naming context above the proposed naming context. Please ensure that the domain naming master role is held by a server that is configured as a global catalog server, and that the server is up to date with its replication partners. (Applies only to Windows 2000 Domain Naming masters)|
|8496|Destination domain must be in native mode.|
|8497|The operation cannot be performed because the server does not have an infrastructure container in the domain of interest.|
|8498|Cross-domain move of non-empty account groups is not allowed.|
|8499|Cross-domain move of non-empty resource groups is not allowed.|
|8500|The search flags for the attribute are invalid. The ANR bit is valid only on attributes of Unicode or Teletex strings.|
|8501|Tree deletions starting at an object which has an NC head as a descendant are not allowed.|
|8502|The directory service failed to lock a tree in preparation for a tree deletion because the tree was in use.|
|8503|The directory service failed to identify the list of objects to delete while attempting a tree deletion.|
|8504|Security Accounts Manager initialization failed because of the following error: %1.<br>Error Status: 0x%2. Please shutdown this system and reboot into Directory Services Restore Mode, check the event log for more detailed information.|
|8505|Only an administrator can modify the membership list of an administrative group.|
|8506|Cannot change the primary group ID of a domain controller account.|
|8507|An attempt is made to modify the base schema.|
|8508|Adding a new mandatory attribute to an existing class, deleting a mandatory attribute from an existing class, or adding an optional attribute to the special class Top that is not a backlink attribute (directly or through inheritance, for example, by adding or deleting an auxiliary class) is not allowed.|
|8509|Schema update is not allowed on this DC because the DC is not the schema FSMO Role Owner.|
|8510|An object of this class cannot be created under the schema container. You can only create attribute-schema and class-schema objects under the schema container.|
|8511|The replica/child install failed to get the objectVersion attribute on the schema container on the source DC. Either the attribute is missing on the schema container or the credentials supplied do not have permission to read it.|
|8512|The replica/child install failed to read the objectVersion attribute in the SCHEMA section of the file schema.ini in the system32 directory.|
|8513|The specified group type is invalid.|
|8514|You cannot nest global groups in a mixed domain if the group is security-enabled.|
|8515|You cannot nest local groups in a mixed domain if the group is security-enabled.|
|8516|A global group cannot have a local group as a member.|
|8517|A global group cannot have a universal group as a member.|
|8518|A universal group cannot have a local group as a member.|
|8519|A global group cannot have a cross-domain member.|
|8520|A local group cannot have another cross domain local group as a member.|
|8521|A group with primary members cannot change to a security-disabled group.|
|8522|The schema cache load failed to convert the string default SD on a class-schema object.|
|8523|Only DSAs configured to be Global Catalog servers should be allowed to hold the Domain Naming Master FSMO role. (Applies only to Windows 2000 servers)|
|8524|The DSA operation is unable to proceed because of a DNS lookup failure.|
|8525|While processing a change to the DNS Host Name for an object, the Service Principal Name values could not be kept in sync.|
|8526|The Security Descriptor attribute could not be read.|
|8527|The object requested was not found, but an object with that key was found.|
|8528|The syntax of the linked attribute being added is incorrect. Forward links can only have syntax 2.5.5.1, 2.5.5.7, and 2.5.5.14, and backlinks can only have syntax 2.5.5.1|
|8529|Security Account Manager needs to get the boot password.|
|8530|Security Account Manager needs to get the boot key from floppy disk.|
|8531|Directory Service cannot start.|
|8532|Directory Services could not start.|
|8533|The connection between client and server requires packet privacy or better.|
|8534|The source domain may not be in the same forest as destination.|
|8535|The destination domain must be in the forest.|
|8536|The operation requires that destination domain auditing be enabled.|
|8537|The operation couldn't locate a DC for the source domain.|
|8538|The source object must be a group or user.|
|8539|The source object's SID already exists in destination forest.|
|8540|The source and destination object must be of the same type.|
|8541|Security Accounts Manager initialization failed because of the following error: %1.<br>Error Status: 0x%2. Click OK to shut down the system and reboot into Safe Mode. Check the event log for detailed information.|
|8542|Schema information could not be included in the replication request.|
|8543|The replication operation could not be completed due to a schema incompatibility.|
|8544|The replication operation could not be completed due to a previous schema incompatibility.|
|8545|The replication update could not be applied because either the source or the destination has not yet received information regarding a recent cross-domain move operation.|
|8546|The requested domain could not be deleted because there exist domain controllers that still host this domain.|
|8547|The requested operation can be performed only on a global catalog server.|
|8548|A local group can only be a member of other local groups in the same domain.|
|8549|Foreign security principals cannot be members of universal groups.|
|8550|The attribute is not allowed to be replicated to the GC because of security reasons.|
|8551|The checkpoint with the PDC could not be taken because there too many modifications being processed currently.|
|8552|The operation requires that source domain auditing be enabled.|
|8553|Security principal objects can only be created inside domain naming contexts.|
|8554|A Service Principal Name (SPN) could not be constructed because the provided hostname is not in the necessary format.|
|8555|A Filter was passed that uses constructed attributes.|
|8556|The unicodePwd attribute value must be enclosed in double quotes.|
|8557|Your computer could not be joined to the domain. You have exceeded the maximum number of computer accounts you are allowed to create in this domain. Contact your system administrator to have this limit reset or increased.|
|8558|For security reasons, the operation must be run on the destination DC.|
|8559|For security reasons, the source DC must be NT4SP4 or greater.|
|8560|Critical Directory Service System objects cannot be deleted during tree delete operations. The tree delete may have been partially performed.|
|8561|Directory Services could not start because of the following error: %1.<br>Error Status: 0x%2. Please click OK to shutdown the system. You can use the recovery console to diagnose the system further.|
|8562|Security Accounts Manager initialization failed because of the following error: %1.<br>Error Status: 0x%2. Please click OK to shutdown the system. You can use the recovery console to diagnose the system further.|
|8563|The version of the operating system is incompatible with the current AD DS forest functional level or AD LDS Configuration Set functional level. You must upgrade to a new version of the operating system before this server can become an AD DS Domain Controller or add an AD LDS Instance in this AD DS Forest or AD LDS Configuration Set.|
|8564|The version of the operating system installed is incompatible with the current domain functional level. You must upgrade to a new version of the operating system before this server can become a domain controller in this domain.|
|8565|The version of the operating system installed on this server no longer supports the current AD DS Forest functional level or AD LDS Configuration Set functional level. You must raise the AD DS Forest functional level or AD LDS Configuration Set functional level before this server can become an AD DS Domain Controller or an AD LDS Instance in this Forest or Configuration Set.|
|8566|The version of the operating system installed on this server no longer supports the current domain functional level. You must raise the domain functional level before this server can become a domain controller in this domain.|
|8567|The version of the operating system installed on this server is incompatible with the functional level of the domain or forest.|
|8568|The functional level of the domain (or forest) cannot be raised to the requested value, because there exist one or more domain controllers in the domain (or forest) that are at a lower incompatible functional level.|
|8569|The forest functional level cannot be raised to the requested value since one or more domains are still in mixed domain mode. All domains in the forest must be in native mode, for you to raise the forest functional level.|
|8570|The sort order requested is not supported.|
|8571|The requested name already exists as a unique identifier.|
|8572|The machine account was created pre-NT4. The account needs to be recreated.|
|8573|The database is out of version store.|
|8574|Unable to continue operation because multiple conflicting controls were used.|
|8575|Unable to find a valid security descriptor reference domain for this partition.|
|8576|Schema update failed: The link identifier is reserved.|
|8577|Schema update failed: There are no link identifiers available.|
|8578|An account group cannot have a universal group as a member.|
|8579|Rename or move operations on naming context heads or read-only objects are not allowed.|
|8580|Move operations on objects in the schema naming context are not allowed.|
|8581|A system flag has been set on the object and does not allow the object to be moved or renamed.|
|8582|This object is not allowed to change its grandparent container. Moves are not forbidden on this object, but are restricted to sibling containers.|
|8583|Unable to resolve completely, a referral to another forest is generated.|
|8584|The requested action is not supported on standard server.|
|8585|Could not access a partition of the directory service located on a remote server. Make sure at least one server is running for the partition in question.|
|8586|The directory cannot validate the proposed naming context (or partition) name because it does not hold a replica nor can it contact a replica of the naming context above the proposed naming context. Please ensure that the parent naming context is properly registered in DNS, and at least one replica of this naming context is reachable by the Domain Naming master.|
|8587|The thread limit for this request was exceeded.|
|8588|The Global catalog server is not in the closest site.|
|8589|The DS cannot derive a service principal name (SPN) with which to mutually authenticate the target server because the corresponding server object in the local DS database has no serverReference attribute.|
|8590|The Directory Service failed to enter single user mode.|
|8591|The Directory Service cannot parse the script because of a syntax error.|
|8592|The Directory Service cannot process the script because of an error.|
|8593|The directory service cannot perform the requested operation because the servers involved are of different replication epochs (which is usually related to a domain rename that is in progress).|
|8594|The directory service binding must be renegotiated due to a change in the server extensions information.|
|8595|Operation not allowed on a disabled cross ref.|
|8596|Schema update failed: No values for msDS-IntId are available.|
|8597|Schema update failed: Duplicate msDS-INtId. Retry the operation.|
|8598|Schema deletion failed: attribute is used in rDNAttID.|
|8599|The directory service failed to authorize the request.|
|8600|The Directory Service cannot process the script because it is invalid.|
|8601|The remote create cross reference operation failed on the Domain Naming Master FSMO. The operation's error is in the extended data.|
|8602|A cross reference is in use locally with the same name.|
|8603|The DS cannot derive a service principal name (SPN) with which to mutually authenticate the target server because the server's domain has been deleted from the forest.|
|8604|Writeable NCs prevent this DC from demoting.|
|8605|The requested object has a non-unique identifier and cannot be retrieved.|
|8606|Insufficient attributes were given to create an object. This object may not exist because it may have been deleted and already garbage collected.|
|8607|The group cannot be converted due to attribute restrictions on the requested group type.|
|8608|Cross-domain move of non-empty basic application groups is not allowed.|
|8609|Cross-domain move of non-empty query based application groups is not allowed.|
|8610|The FSMO role ownership could not be verified because its directory partition has not replicated successfully with at least one replication partner.|
|8611|The target container for a redirection of a well known object container cannot already be a special container.|
|8612|The Directory Service cannot perform the requested operation because a domain rename operation is in progress.|
|8613|The directory service detected a child partition below the requested partition name. The partition hierarchy must be created in a top down method.|
|8614|The directory service cannot replicate with this server because the time since the last replication with this server has exceeded the tombstone lifetime.|
|8615|The requested operation is not allowed on an object under the system container.|
|8616|The LDAP servers network send queue has filled up because the client is not processing the results of its requests fast enough. No more requests will be processed until the client catches up. If the client does not catch up then it will be disconnected.|
|8617|The scheduled replication did not take place because the system was too busy to execute the request within the schedule window. The replication queue is overloaded. Consider reducing the number of partners or decreasing the scheduled replication frequency.|
|8618|At this time, it cannot be determined if the branch replication policy is available on the hub domain controller. Please retry at a later time to account for replication latencies.|
|8619|The site settings object for the specified site does not exist.|
|8620|The local account store does not contain secret material for the specified account.|
|8621|Could not find a writable domain controller in the domain.|
|8622|The server object for the domain controller does not exist.|
|8623|The NTDS Settings object for the domain controller does not exist.|
|8624|The requested search operation is not supported for ASQ searches.|
|8625|A required audit event could not be generated for the operation.|
|8626|The search flags for the attribute are invalid. The subtree index bit is valid only on single valued attributes.|
|8627|The search flags for the attribute are invalid. The tuple index bit is valid only on attributes of Unicode strings.|
|8628|The address books are nested too deeply. Failed to build the hierarchy table.|
|8629|The specified up-to-date-ness vector is corrupt.|
|8630|The request to replicate secrets is denied.|
|8631|Schema update failed: The MAPI identifier is reserved.|
|8632|Schema update failed: There are no MAPI identifiers available.|
|8633|The replication operation failed because the required attributes of the local krbtgt object are missing.|
|8634|The domain name of the trusted domain already exists in the forest.|
|8635|The flat name of the trusted domain already exists in the forest.|
|8636|The User Principal Name (UPN) is invalid.|
|8637|OID mapped groups cannot have members.|
|8638|The specified OID cannot be found.|
|8639|The replication operation failed because the target object referred by a link value is recycled.|
|8640|The redirect operation failed because the target object is in a NC different from the domain NC of the current domain controller.|
|8641|The functional level of the AD LDS configuration set cannot be lowered to the requested value.|
|8642|The functional level of the domain (or forest) cannot be lowered to the requested value.|
|8643|The functional level of the AD LDS configuration set cannot be raised to the requested value, because there exist one or more ADLDS instances that are at a lower incompatible functional level.|
|8644|The domain join cannot be completed because the SID of the domain you attempted to join was identical to the SID of this machine. This is a symptom of an improperly cloned operating system install.  You should run sysprep on this machine in order to generate a new machine SID. Please see http://go.microsoft.com/fwlink/?LinkId=168895 for more information.|
|8645|The undelete operation failed because the Sam Account Name or Additional Sam Account Name of the object being undeleted conflicts with an existing live object.|
|8646|The system is not authoritative for the specified account and therefore cannot complete the operation. Please retry the operation using the provider associated with this account. If this is an online provider please use the provider's online site.|
|8647|The operation failed because SPN value provided for addition/modification is not unique forest-wide.|
|8648|The operation failed because UPN value provided for addition/modification is not unique forest-wide.|
|8649|The operation failed because the addition/modification referenced an inbound forest-wide trust that is not present.|
|8650|The link value specified was not found, but a link value with that key was found.|
|8651|The Security Account Manager blocked the use of a weak Windows Hello for Business key.|
|8652|The add object operation failed because the caller was not authorized to add one or more attributes included in the request.|
|8653|The local account policy modification request was rejected because the policy is controlled by a regional authority.|
|8654|The account is controlled by external policy and cannot be modified.|
|8655|The Local Administrator Password Solution password update operation failed because the legacy LAPS schema needs to be added to Active Directory.|
|8656|The Local Administrator Password Solution password update operation failed because the Windows LAPS schema needs to be added to Active Directory.|
|8657|The Local Administrator Password Solution encrypted password update operation failed because Active Directory is not yet running at the minimum required domain functional level (2016).|
|9001|DNS server unable to interpret format.|
|9002|DNS server failure.|
|9003|DNS name does not exist.|
|9004|DNS request not supported by name server.|
|9005|DNS operation refused.|
|9006|DNS name that ought not exist, does exist.|
|9007|DNS RR set that ought not exist, does exist.|
|9008|DNS RR set that ought to exist, does not exist.|
|9009|DNS server not authoritative for zone.|
|9010|DNS name in update or prereq is not in zone.|
|9016|DNS signature failed to verify.|
|9017|DNS bad key.|
|9018|DNS signature validity expired.|
|9101|Only the DNS server acting as the key master for the zone may perform this operation.|
|9102|This operation is not allowed on a zone that is signed or has signing keys.|
|9103|NSEC3 is not compatible with the RSA-SHA-1 algorithm. Choose a different algorithm or use NSEC.|
|9104|The zone does not have enough signing keys. There must be at least one key signing key (KSK) and at least one zone signing key (ZSK).|
|9105|The specified algorithm is not supported.|
|9106|The specified key size is not supported.|
|9107|One or more of the signing keys for a zone are not accessible to the DNS server. Zone signing will not be operational until this error is resolved.|
|9108|The specified key storage provider does not support DPAPI++ data protection. Zone signing will not be operational until this error is resolved.|
|9109|An unexpected DPAPI++ error was encountered. Zone signing will not be operational until this error is resolved.|
|9110|An unexpected crypto error was encountered. Zone signing may not be operational until this error is resolved.|
|9111|The DNS server encountered a signing key with an unknown version. Zone signing will not be operational until this error is resolved.|
|9112|The specified key service provider cannot be opened by the DNS server.|
|9113|The DNS server cannot accept any more signing keys with the specified algorithm and KSK flag value for this zone.|
|9114|The specified rollover period is invalid.|
|9115|The specified initial rollover offset is invalid.|
|9116|The specified signing key is already in process of rolling over keys.|
|9117|The specified signing key does not have a standby key to revoke.|
|9118|This operation is not allowed on a zone signing key (ZSK).|
|9119|This operation is not allowed on an active signing key.|
|9120|The specified signing key is already queued for rollover.|
|9121|This operation is not allowed on an unsigned zone.|
|9122|This operation could not be completed because the DNS server listed as the current key master for this zone is down or misconfigured. Resolve the problem on the current key master for this zone or use another DNS server to seize the key master role.|
|9123|The specified signature validity period is invalid.|
|9124|The specified NSEC3 iteration count is higher than allowed by the minimum key length used in the zone.|
|9125|This operation could not be completed because the DNS server has been configured with DNSSEC features disabled. Enable DNSSEC on the DNS server.|
|9126|This operation could not be completed because the XML stream received is empty or syntactically invalid.|
|9127|This operation completed, but no trust anchors were added because all of the trust anchors received were either invalid, unsupported, expired, or would not become valid in less than 30 days.|
|9128|The specified signing key is not waiting for parental DS update.|
|9129|Hash collision detected during NSEC3 signing. Specify a different user-provided salt, or use a randomly generated salt, and attempt to sign the zone again.|
|9130|NSEC is not compatible with the NSEC3-RSA-SHA-1 algorithm. Choose a different algorithm or use NSEC3.|
|9501|No records found for given DNS query.|
|9502|Bad DNS packet.|
|9503|No DNS packet.|
|9504|DNS error, check rcode.|
|9505|Unsecured DNS packet.|
|9506|DNS query request is pending.|
|9551|Invalid DNS type.|
|9552|Invalid IP address.|
|9553|Invalid property.|
|9554|Try DNS operation again later.|
|9555|Record for given name and type is not unique.|
|9556|DNS name does not comply with RFC specifications.|
|9557|DNS name is a fully-qualified DNS name.|
|9558|DNS name is dotted (multi-label).|
|9559|DNS name is a single-part name.|
|9560|DNS name contains an invalid character.|
|9561|DNS name is entirely numeric.|
|9562|The operation requested is not permitted on a DNS root server.|
|9563|The record could not be created because this part of the DNS namespace has been delegated to another server.|
|9564|The DNS server could not find a set of root hints.|
|9565|The DNS server found root hints but they were not consistent across all adapters.|
|9566|The specified value is too small for this parameter.|
|9567|The specified value is too large for this parameter.|
|9568|This operation is not allowed while the DNS server is loading zones in the background. Please try again later.|
|9569|The operation requested is not permitted on against a DNS server running on a read-only DC.|
|9570|No data is allowed to exist underneath a DNAME record.|
|9571|This operation requires credentials delegation.|
|9572|Name resolution policy table has been corrupted. DNS resolution will fail until it is fixed. Contact your network administrator.|
|9573|Not allowed to remove all addresses.|
|9601|DNS zone does not exist.|
|9602|DNS zone information not available.|
|9603|Invalid operation for DNS zone.|
|9604|Invalid DNS zone configuration.|
|9605|DNS zone has no start of authority (SOA) record.|
|9606|DNS zone has no Name Server (NS) record.|
|9607|DNS zone is locked.|
|9608|DNS zone creation failed.|
|9609|DNS zone already exists.|
|9610|DNS automatic zone already exists.|
|9611|Invalid DNS zone type.|
|9612|Secondary DNS zone requires master IP address.|
|9613|DNS zone not secondary.|
|9614|Need secondary IP address.|
|9615|WINS initialization failed.|
|9616|Need WINS servers.|
|9617|NBTSTAT initialization call failed.|
|9618|Invalid delete of start of authority (SOA)|
|9619|A conditional forwarding zone already exists for that name.|
|9620|This zone must be configured with one or more master DNS server IP addresses.|
|9621|The operation cannot be performed because this zone is shut down.|
|9622|This operation cannot be performed because the zone is currently being signed. Please try again later.|
|9651|Primary DNS zone requires datafile.|
|9652|Invalid datafile name for DNS zone.|
|9653|Failed to open datafile for DNS zone.|
|9654|Failed to write datafile for DNS zone.|
|9655|Failure while reading datafile for DNS zone.|
|9701|DNS record does not exist.|
|9702|DNS record format error.|
|9703|Node creation failure in DNS.|
|9704|Unknown DNS record type.|
|9705|DNS record timed out.|
|9706|Name not in DNS zone.|
|9707|CNAME loop detected.|
|9708|Node is a CNAME DNS record.|
|9709|A CNAME record already exists for given name.|
|9710|Record only at DNS zone root.|
|9711|DNS record already exists.|
|9712|Secondary DNS zone data error.|
|9713|Could not create DNS cache data.|
|9714|DNS name does not exist.|
|9715|Could not create pointer (PTR) record.|
|9716|DNS domain was undeleted.|
|9717|The directory service is unavailable.|
|9718|DNS zone already exists in the directory service.|
|9719|DNS server not creating or reading the boot file for the directory service integrated DNS zone.|
|9720|Node is a DNAME DNS record.|
|9721|A DNAME record already exists for given name.|
|9722|An alias loop has been detected with either CNAME or DNAME records.|
|9751|DNS AXFR (zone transfer) complete.|
|9752|DNS zone transfer failed.|
|9753|Added local WINS server.|
|9801|Secure update call needs to continue update request.|
|9851|TCP/IP network protocol not installed.|
|9852|No DNS servers configured for local system.|
|9901|The specified directory partition does not exist.|
|9902|The specified directory partition already exists.|
|9903|This DNS server is not enlisted in the specified directory partition.|
|9904|This DNS server is already enlisted in the specified directory partition.|
|9905|The directory partition is not available at this time. Please wait a few minutes and try again.|
|9906|The operation failed because the domain naming master FSMO role could not be reached. The domain controller holding the domain naming master FSMO role is down or unable to service the request or is not running Windows Server 2003 or later.|
|9911|The RRL is not enabled.|
|9912|The window size parameter is invalid. It should be greater than or equal to 1.|
|9913|The IPv4 prefix length parameter is invalid. It should be less than or equal to 32.|
|9914|The IPv6 prefix length parameter is invalid. It should be less than or equal to 128.|
|9915|The TC Rate parameter is invalid. It should be less than 10.|
|9916|The Leak Rate parameter is invalid. It should be either 0, or between 2 and 10.|
|9917|The Leak Rate or TC Rate parameter is invalid. Leak Rate should be greater than TC Rate.|
|9921|The virtualization instance already exists.|
|9922|The virtualization instance does not exist.|
|9923|The virtualization tree is locked.|
|9924|Invalid virtualization instance name.|
|9925|The default virtualization instance cannot be added, removed or modified.|
|9951|The scope already exists for the zone.|
|9952|The scope does not exist for the zone.|
|9953|The scope is the same as the default zone scope.|
|9954|The scope name contains invalid characters.|
|9955|Operation not allowed when the zone has scopes.|
|9956|Failed to load zone scope.|
|9957|Failed to write data file for DNS zone scope. Please verify the file exists and is writable.|
|9958|The scope name contains invalid characters.|
|9959|The scope does not exist.|
|9960|The scope is the same as the default scope.|
|9961|The operation is invalid on the scope.|
|9962|The scope is locked.|
|9963|The scope already exists.|
|9971|A policy with the same name already exists on this level (server level or zone level) on the DNS server.|
|9972|No policy with this name exists on this level (server level or zone level) on the DNS server.|
|9973|The criteria provided in the policy are invalid.|
|9974|At least one of the settings of this policy is invalid.|
|9975|The client subnet cannot be deleted while it is being accessed by a policy.|
|9976|The client subnet does not exist on the DNS server.|
|9977|A client subnet with this name already exists on the DNS server.|
|9978|The IP subnet specified does not exist in the client subnet.|
|9979|The IP subnet that is being added, already exists in the client subnet.|
|9980|The policy is locked.|
|9981|The weight of the scope in the policy is invalid.|
|9982|The DNS policy name is invalid.|
|9983|The policy is missing criteria.|
|9984|The name of the the client subnet record is invalid.|
|9985|Invalid policy processing order.|
|9986|The scope information has not been provided for a policy that requires it.|
|9987|The scope information has been provided for a policy that does not require it.|
|9988|The server scope cannot be deleted because it is referenced by a DNS Policy.|
|9989|The zone scope cannot be deleted because it is referenced by a DNS Policy.|
|9990|The criterion client subnet provided in the policy is invalid.|
|9991|The criterion transport protocol provided in the policy is invalid.|
|9992|The criterion network protocol provided in the policy is invalid.|
|9993|The criterion interface provided in the policy is invalid.|
|9994|The criterion FQDN provided in the policy is invalid.|
|9995|The criterion query type provided in the policy is invalid.|
|9996|The criterion time of day provided in the policy is invalid.|
|10004|A blocking operation was interrupted by a call to WSACancelBlockingCall.|
|10009|The file handle supplied is not valid.|
|10013|An attempt was made to access a socket in a way forbidden by its access permissions.|
|10014|The system detected an invalid pointer address in attempting to use a pointer argument in a call.|
|10022|An invalid argument was supplied.|
|10024|Too many open sockets.|
|10035|A non-blocking socket operation could not be completed immediately.|
|10036|A blocking operation is currently executing.|
|10037|An operation was attempted on a non-blocking socket that already had an operation in progress.|
|10038|An operation was attempted on something that is not a socket.|
|10039|A required address was omitted from an operation on a socket.|
|10040|A message sent on a datagram socket was larger than the internal message buffer or some other network limit, or the buffer used to receive a datagram into was smaller than the datagram itself.|
|10041|A protocol was specified in the socket function call that does not support the semantics of the socket type requested.|
|10042|An unknown, invalid, or unsupported option or level was specified in a getsockopt or setsockopt call.|
|10043|The requested protocol has not been configured into the system, or no implementation for it exists.|
|10044|The support for the specified socket type does not exist in this address family.|
|10045|The attempted operation is not supported for the type of object referenced.|
|10046|The protocol family has not been configured into the system or no implementation for it exists.|
|10047|An address incompatible with the requested protocol was used.|
|10048|Only one usage of each socket address (protocol/network address/port) is normally permitted.|
|10049|The requested address is not valid in its context.|
|10050|A socket operation encountered a dead network.|
|10051|A socket operation was attempted to an unreachable network.|
|10052|The connection has been broken due to keep-alive activity detecting a failure while the operation was in progress.|
|10053|An established connection was aborted by the software in your host machine.|
|10054|An existing connection was forcibly closed by the remote host.|
|10055|An operation on a socket could not be performed because the system lacked sufficient buffer space or because a queue was full.|
|10056|A connect request was made on an already connected socket.|
|10057|A request to send or receive data was disallowed because the socket is not connected and (when sending on a datagram socket using a sendto call) no address was supplied.|
|10058|A request to send or receive data was disallowed because the socket had already been shut down in that direction with a previous shutdown call.|
|10059|Too many references to some kernel object.|
|10060|A connection attempt failed because the connected party did not properly respond after a period of time, or established connection failed because connected host has failed to respond.|
|10061|No connection could be made because the target machine actively refused it.|
|10062|Cannot translate name.|
|10063|Name component or name was too long.|
|10064|A socket operation failed because the destination host was down.|
|10065|A socket operation was attempted to an unreachable host.|
|10066|Cannot remove a directory that is not empty.|
|10067|A Windows Sockets implementation may have a limit on the number of applications that may use it simultaneously.|
|10068|Ran out of quota.|
|10069|Ran out of disk quota.|
|10070|File handle reference is no longer available.|
|10071|Item is not available locally.|
|10091|WSAStartup cannot function at this time because the underlying system it uses to provide network services is currently unavailable.|
|10092|The Windows Sockets version requested is not supported.|
|10093|Either the application has not called WSAStartup, or WSAStartup failed.|
|10101|Returned by WSARecv or WSARecvFrom to indicate the remote party has initiated a graceful shutdown sequence.|
|10102|No more results can be returned by WSALookupServiceNext.|
|10103|A call to WSALookupServiceEnd was made while this call was still processing. The call has been canceled.|
|10104|The procedure call table is invalid.|
|10105|The requested service provider is invalid.|
|10106|The requested service provider could not be loaded or initialized.|
|10107|A system call has failed.|
|10108|No such service is known. The service cannot be found in the specified name space.|
|10109|The specified class was not found.|
|10110|No more results can be returned by WSALookupServiceNext.|
|10111|A call to WSALookupServiceEnd was made while this call was still processing. The call has been canceled.|
|10112|A database query failed because it was actively refused.|
|11001|No such host is known.|
|11002|This is usually a temporary error during hostname resolution and means that the local server did not receive a response from an authoritative server.|
|11003|A non-recoverable error occurred during a database lookup.|
|11004|The requested name is valid, but no data of the requested type was found.|
|11005|At least one reserve has arrived.|
|11006|At least one path has arrived.|
|11007|There are no senders.|
|11008|There are no receivers.|
|11009|Reserve has been confirmed.|
|11010|Error due to lack of resources.|
|11011|Rejected for administrative reasons - bad credentials.|
|11012|Unknown or conflicting style.|
|11013|Problem with some part of the filterspec or providerspecific buffer in general.|
|11014|Problem with some part of the flowspec.|
|11015|General QOS error.|
|11016|An invalid or unrecognized service type was found in the flowspec.|
|11017|An invalid or inconsistent flowspec was found in the QOS structure.|
|11018|Invalid QOS provider-specific buffer.|
|11019|An invalid QOS filter style was used.|
|11020|An invalid QOS filter type was used.|
|11021|An incorrect number of QOS FILTERSPECs were specified in the FLOWDESCRIPTOR.|
|11022|An object with an invalid ObjectLength field was specified in the QOS provider-specific buffer.|
|11023|An incorrect number of flow descriptors was specified in the QOS structure.|
|11024|An unrecognized object was found in the QOS provider-specific buffer.|
|11025|An invalid policy object was found in the QOS provider-specific buffer.|
|11026|An invalid QOS flow descriptor was found in the flow descriptor list.|
|11027|An invalid or inconsistent flowspec was found in the QOS provider specific buffer.|
|11028|An invalid FILTERSPEC was found in the QOS provider-specific buffer.|
|11029|An invalid shape discard mode object was found in the QOS provider specific buffer.|
|11030|An invalid shaping rate object was found in the QOS provider-specific buffer.|
|11031|A reserved policy element was found in the QOS provider-specific buffer.|
|11032|No such host is known securely.|
|11033|Name based IPSEC policy could not be added.|
|13000|The specified quick mode policy already exists.|
|13001|The specified quick mode policy was not found.|
|13002|The specified quick mode policy is being used.|
|13003|The specified main mode policy already exists.|
|13004|The specified main mode policy was not found|
|13005|The specified main mode policy is being used.|
|13006|The specified main mode filter already exists.|
|13007|The specified main mode filter was not found.|
|13008|The specified transport mode filter already exists.|
|13009|The specified transport mode filter does not exist.|
|13010|The specified main mode authentication list exists.|
|13011|The specified main mode authentication list was not found.|
|13012|The specified main mode authentication list is being used.|
|13013|The specified default main mode policy was not found.|
|13014|The specified default main mode authentication list was not found.|
|13015|The specified default quick mode policy was not found.|
|13016|The specified tunnel mode filter exists.|
|13017|The specified tunnel mode filter was not found.|
|13018|The Main Mode filter is pending deletion.|
|13019|The transport filter is pending deletion.|
|13020|The tunnel filter is pending deletion.|
|13021|The Main Mode policy is pending deletion.|
|13022|The Main Mode authentication bundle is pending deletion.|
|13023|The Quick Mode policy is pending deletion.|
|13024|The Main Mode policy was successfully added, but some of the requested offers are not supported.|
|13025|The Quick Mode policy was successfully added, but some of the requested offers are not supported.|
|13800|ERROR_IPSEC_IKE_NEG_STATUS_BEGIN|
|13801|IKE authentication credentials are unacceptable|
|13802|IKE security attributes are unacceptable|
|13803|IKE Negotiation in progress|
|13804|General processing error|
|13805|Negotiation timed out|
|13806|IKE failed to find valid machine certificate. Contact your Network Security Administrator about installing a valid certificate in the appropriate Certificate Store.|
|13807|IKE SA deleted by peer before establishment completed|
|13808|IKE SA deleted before establishment completed|
|13809|Negotiation request sat in Queue too long|
|13810|Negotiation request sat in Queue too long|
|13811|Negotiation request sat in Queue too long|
|13812|Negotiation request sat in Queue too long|
|13813|No response from peer|
|13814|Negotiation took too long|
|13815|Negotiation took too long|
|13816|Unknown error occurred|
|13817|Certificate Revocation Check failed|
|13818|Invalid certificate key usage|
|13819|Invalid certificate type|
|13820|IKE negotiation failed because the machine certificate used does not have a private key. IPsec certificates require a private key. Contact your Network Security administrator about replacing with a certificate that has a private key.|
|13821|Simultaneous rekeys were detected.|
|13822|Failure in Diffie-Hellman computation|
|13823|Don't know how to process critical payload|
|13824|Invalid header|
|13825|No policy configured|
|13826|Failed to verify signature|
|13827|Failed to authenticate using Kerberos|
|13828|Peer's certificate did not have a public key|
|13829|Error processing error payload|
|13830|Error processing SA payload|
|13831|Error processing Proposal payload|
|13832|Error processing Transform payload|
|13833|Error processing KE payload|
|13834|Error processing ID payload|
|13835|Error processing Cert payload|
|13836|Error processing Certificate Request payload|
|13837|Error processing Hash payload|
|13838|Error processing Signature payload|
|13839|Error processing Nonce payload|
|13840|Error processing Notify payload|
|13841|Error processing Delete Payload|
|13842|Error processing VendorId payload|
|13843|Invalid payload received|
|13844|Soft SA loaded|
|13845|Soft SA torn down|
|13846|Invalid cookie received.|
|13847|Peer failed to send valid machine certificate|
|13848|Certification Revocation check of peer's certificate failed|
|13849|New policy invalidated SAs formed with old policy|
|13850|There is no available Main Mode IKE policy.|
|13851|Failed to enabled TCB privilege.|
|13852|Failed to load SECURITY.DLL.|
|13853|Failed to obtain security function table dispatch address from SSPI.|
|13854|Failed to query Kerberos package to obtain max token size.|
|13855|Failed to obtain Kerberos server credentials for ISAKMP/ERROR_IPSEC_IKE service. Kerberos authentication will not function. The most likely reason for this is lack of domain membership. This is normal if your computer is a member of a workgroup.|
|13856|Failed to determine SSPI principal name for ISAKMP/ERROR_IPSEC_IKE service (QueryCredentialsAttributes).|
|13857|Failed to obtain new SPI for the inbound SA from IPsec driver. The most common cause for this is that the driver does not have the correct filter. Check your policy to verify the filters.|
|13858|Given filter is invalid|
|13859|Memory allocation failed.|
|13860|Failed to add Security Association to IPsec Driver. The most common cause for this is if the IKE negotiation took too long to complete. If the problem persists, reduce the load on the faulting machine.|
|13861|Invalid policy|
|13862|Invalid DOI|
|13863|Invalid situation|
|13864|Diffie-Hellman failure|
|13865|Invalid Diffie-Hellman group|
|13866|Error encrypting payload|
|13867|Error decrypting payload|
|13868|Policy match error|
|13869|Unsupported ID|
|13870|Hash verification failed|
|13871|Invalid hash algorithm|
|13872|Invalid hash size|
|13873|Invalid encryption algorithm|
|13874|Invalid authentication algorithm|
|13875|Invalid certificate signature|
|13876|Load failed|
|13877|Deleted via RPC call|
|13878|Temporary state created to perform reinitialization. This is not a real failure.|
|13879|The lifetime value received in the Responder Lifetime Notify is below the Windows 2000 configured minimum value. Please fix the policy on the peer machine.|
|13880|The recipient cannot handle version of IKE specified in the header.|
|13881|Key length in certificate is too small for configured security requirements.|
|13882|Max number of established MM SAs to peer exceeded.|
|13883|IKE received a policy that disables negotiation.|
|13884|Reached maximum quick mode limit for the main mode. New main mode will be started.|
|13885|Main mode SA lifetime expired or peer sent a main mode delete.|
|13886|Main mode SA assumed to be invalid because peer stopped responding.|
|13887|Certificate doesn't chain to a trusted root in IPsec policy.|
|13888|Received unexpected message ID.|
|13889|Received invalid authentication offers.|
|13890|Sent DoS cookie notify to initiator.|
|13891|IKE service is shutting down.|
|13892|Could not verify binding between CGA address and certificate.|
|13893|Error processing NatOA payload.|
|13894|Parameters of the main mode are invalid for this quick mode.|
|13895|Quick mode SA was expired by IPsec driver.|
|13896|Too many dynamically added IKEEXT filters were detected.|
|13897|ERROR_IPSEC_IKE_NEG_STATUS_END|
|13898|NAP reauth succeeded and must delete the dummy NAP IKEv2 tunnel.|
|13899|Error in assigning inner IP address to initiator in tunnel mode.|
|13900|Require configuration payload missing.|
|13901|A negotiation running as the security principle who issued the connection is in progress|
|13902|SA was deleted due to IKEv1/AuthIP co-existence suppress check.|
|13903|Incoming SA request was dropped due to peer IP address rate limiting.|
|13904|Peer does not support MOBIKE.|
|13905|SA establishment is not authorized.|
|13906|SA establishment is not authorized because there is not a sufficiently strong PKINIT-based credential.|
|13907|SA establishment is not authorized.  You may need to enter updated or different credentials such as a smartcard.|
|13908|SA establishment is not authorized because there is not a sufficiently strong PKINIT-based credential. This might be related to certificate-to-account mapping failure for the SA.|
|13909|ERROR_IPSEC_IKE_NEG_STATUS_EXTENDED_END|
|13910|The SPI in the packet does not match a valid IPsec SA.|
|13911|Packet was received on an IPsec SA whose lifetime has expired.|
|13912|Packet was received on an IPsec SA that does not match the packet characteristics.|
|13913|Packet sequence number replay check failed.|
|13914|IPsec header and/or trailer in the packet is invalid.|
|13915|IPsec integrity check failed.|
|13916|IPsec dropped a clear text packet.|
|13917|IPsec dropped an incoming ESP packet in authenticated firewall mode. This drop is benign.|
|13918|IPsec dropped a packet due to DoS throttling.|
|13925|IPsec DoS Protection matched an explicit block rule.|
|13926|IPsec DoS Protection received an IPsec specific multicast packet which is not allowed.|
|13927|IPsec DoS Protection received an incorrectly formatted packet.|
|13928|IPsec DoS Protection failed to look up state.|
|13929|IPsec DoS Protection failed to create state because the maximum number of entries allowed by policy has been reached.|
|13930|IPsec DoS Protection received an IPsec negotiation packet for a keying module which is not allowed by policy.|
|13931|IPsec DoS Protection has not been enabled.|
|13932|IPsec DoS Protection failed to create a per internal IP rate limit queue because the maximum number of queues allowed by policy has been reached.|
|14000|The requested section was not present in the activation context.|
|14001|The application has failed to start because its side-by-side configuration is incorrect. Please see the application event log or use the command-line sxstrace.exe tool for more detail.|
|14002|The application binding data format is invalid.|
|14003|The referenced assembly is not installed on your system.|
|14004|The manifest file does not begin with the required tag and format information.|
|14005|The manifest file contains one or more syntax errors.|
|14006|The application attempted to activate a disabled activation context.|
|14007|The requested lookup key was not found in any active activation context.|
|14008|A component version required by the application conflicts with another component version already active.|
|14009|The type requested activation context section does not match the query API used.|
|14010|Lack of system resources has required isolated activation to be disabled for the current thread of execution.|
|14011|An attempt to set the process default activation context failed because the process default activation context was already set.|
|14012|The encoding group identifier specified is not recognized.|
|14013|The encoding requested is not recognized.|
|14014|The manifest contains a reference to an invalid URI.|
|14015|The application manifest contains a reference to a dependent assembly which is not installed|
|14016|The manifest for an assembly used by the application has a reference to a dependent assembly which is not installed|
|14017|The manifest contains an attribute for the assembly identity which is not valid.|
|14018|The manifest is missing the required default namespace specification on the assembly element.|
|14019|The manifest has a default namespace specified on the assembly element but its value is not "urn:schemas-microsoft-com:asm.v1".|
|14020|The private manifest probed has crossed a path with an unsupported reparse point.|
|14021|Two or more components referenced directly or indirectly by the application manifest have files by the same name.|
|14022|Two or more components referenced directly or indirectly by the application manifest have window classes with the same name.|
|14023|Two or more components referenced directly or indirectly by the application manifest have the same COM server CLSIDs.|
|14024|Two or more components referenced directly or indirectly by the application manifest have proxies for the same COM interface IIDs.|
|14025|Two or more components referenced directly or indirectly by the application manifest have the same COM type library TLBIDs.|
|14026|Two or more components referenced directly or indirectly by the application manifest have the same COM ProgIDs.|
|14027|Two or more components referenced directly or indirectly by the application manifest are different versions of the same component which is not permitted.|
|14028|A component's file does not match the verification information present in the component manifest.|
|14029|The policy manifest contains one or more syntax errors.|
|14030|Manifest Parse Error : A string literal was expected, but no opening quote character was found.|
|14031|Manifest Parse Error : Incorrect syntax was used in a comment.|
|14032|Manifest Parse Error : A name was started with an invalid character.|
|14033|Manifest Parse Error : A name contained an invalid character.|
|14034|Manifest Parse Error : A string literal contained an invalid character.|
|14035|Manifest Parse Error : Invalid syntax for an xml declaration.|
|14036|Manifest Parse Error : An Invalid character was found in text content.|
|14037|Manifest Parse Error : Required white space was missing.|
|14038|Manifest Parse Error : The character '>' was expected.|
|14039|Manifest Parse Error : A semi colon character was expected.|
|14040|Manifest Parse Error : Unbalanced parentheses.|
|14041|Manifest Parse Error : Internal error.|
|14042|Manifest Parse Error : Whitespace is not allowed at this location.|
|14043|Manifest Parse Error : End of file reached in invalid state for current encoding.|
|14044|Manifest Parse Error : Missing parenthesis.|
|14045|Manifest Parse Error : A single or double closing quote character (\' or \") is missing.|
|14046|Manifest Parse Error : Multiple colons are not allowed in a name.|
|14047|Manifest Parse Error : Invalid character for decimal digit.|
|14048|Manifest Parse Error : Invalid character for hexadecimal digit.|
|14049|Manifest Parse Error : Invalid unicode character value for this platform.|
|14050|Manifest Parse Error : Expecting whitespace or '?'.|
|14051|Manifest Parse Error : End tag was not expected at this location.|
|14052|Manifest Parse Error : The following tags were not closed: %1.|
|14053|Manifest Parse Error : Duplicate attribute.|
|14054|Manifest Parse Error : Only one top level element is allowed in an XML document.|
|14055|Manifest Parse Error : Invalid at the top level of the document.|
|14056|Manifest Parse Error : Invalid xml declaration.|
|14057|Manifest Parse Error : XML document must have a top level element.|
|14058|Manifest Parse Error : Unexpected end of file.|
|14059|Manifest Parse Error : Parameter entities cannot be used inside markup declarations in an internal subset.|
|14060|Manifest Parse Error : Element was not closed.|
|14061|Manifest Parse Error : End element was missing the character '>'.|
|14062|Manifest Parse Error : A string literal was not closed.|
|14063|Manifest Parse Error : A comment was not closed.|
|14064|Manifest Parse Error : A declaration was not closed.|
|14065|Manifest Parse Error : A CDATA section was not closed.|
|14066|Manifest Parse Error : The namespace prefix is not allowed to start with the reserved string "xml".|
|14067|Manifest Parse Error : System does not support the specified encoding.|
|14068|Manifest Parse Error : Switch from current encoding to specified encoding not supported.|
|14069|Manifest Parse Error : The name 'xml' is reserved and must be lower case.|
|14070|Manifest Parse Error : The standalone attribute must have the value 'yes' or 'no'.|
|14071|Manifest Parse Error : The standalone attribute cannot be used in external entities.|
|14072|Manifest Parse Error : Invalid version number.|
|14073|Manifest Parse Error : Missing equals sign between attribute and attribute value.|
|14074|Assembly Protection Error : Unable to recover the specified assembly.|
|14075|Assembly Protection Error : The public key for an assembly was too short to be allowed.|
|14076|Assembly Protection Error : The catalog for an assembly is not valid, or does not match the assembly's manifest.|
|14077|An HRESULT could not be translated to a corresponding Win32 error code.|
|14078|Assembly Protection Error : The catalog for an assembly is missing.|
|14079|The supplied assembly identity is missing one or more attributes which must be present in this context.|
|14080|The supplied assembly identity has one or more attribute names that contain characters not permitted in XML names.|
|14081|The referenced assembly could not be found.|
|14082|The activation context activation stack for the running thread of execution is corrupt.|
|14083|The application isolation metadata for this process or thread has become corrupt.|
|14084|The activation context being deactivated is not the most recently activated one.|
|14085|The activation context being deactivated is not active for the current thread of execution.|
|14086|The activation context being deactivated has already been deactivated.|
|14087|A component used by the isolation facility has requested to terminate the process.|
|14088|A kernel mode component is releasing a reference on an activation context.|
|14089|The activation context of system default assembly could not be generated.|
|14090|The value of an attribute in an identity is not within the legal range.|
|14091|The name of an attribute in an identity is not within the legal range.|
|14092|An identity contains two definitions for the same attribute.|
|14093|The identity string is malformed. This may be due to a trailing comma, more than two unnamed attributes, missing attribute name or missing attribute value.|
|14094|A string containing localized substitutable content was malformed. Either a dollar sign ($) was followed by something other than a left parenthesis or another dollar sign or an substitution's right parenthesis was not found.|
|14095|The public key token does not correspond to the public key specified.|
|14096|A substitution string had no mapping.|
|14097|The component must be locked before making the request.|
|14098|The component store has been corrupted.|
|14099|An advanced installer failed during setup or servicing.|
|14100|The character encoding in the XML declaration did not match the encoding used in the document.|
|14101|The identities of the manifests are identical but their contents are different.|
|14102|The component identities are different.|
|14103|The assembly is not a deployment.|
|14104|The file is not a part of the assembly.|
|14105|The size of the manifest exceeds the maximum allowed.|
|14106|The setting is not registered.|
|14107|One or more required members of the transaction are not present.|
|14108|The SMI primitive installer failed during setup or servicing.|
|14109|A generic command executable returned a result that indicates failure.|
|14110|A component is missing file verification information in its manifest.|
|14111|Two or more components referenced directly or indirectly by the application manifest have the same WinRT ActivatableClass IDs.|
|15000|The specified channel path is invalid.|
|15001|The specified query is invalid.|
|15002|The publisher metadata cannot be found in the resource.|
|15003|The template for an event definition cannot be found in the resource (error = %1).|
|15004|The specified publisher name is invalid.|
|15005|The event data raised by the publisher is not compatible with the event template definition in the publisher's manifest.|
|15007|The specified channel could not be found.|
|15008|The specified XML text was not well-formed. See Extended Error for more details.|
|15009|The events for a direct channel go directly to a log file and cannot be subscribed to.|
|15010|Configuration error.|
|15011|The query result is stale or invalid and must be recreated. This may be due to the log being cleared or rolling over after the query result was created.|
|15012|The query result is currently at an invalid position.|
|15013|Registered MSXML doesn't support validation.|
|15014|An expression can only be followed by a change-of-scope operation if the expression evaluates to a node set and is not already part of another change-of-scope operation.|
|15015|Cannot perform a step operation from a term that does not represent an element set.|
|15016|Left-hand side arguments to binary operators must be either attributes, nodes or variables. Right-hand side arguments must be constants.|
|15017|A step operation must involve a node test or, in the case of a predicate, an algebraic expression against which to test each node in the preceeding node set.|
|15018|This data type is currently unsupported.|
|15019|A syntax error occurred at position %1!d!|
|15020|This operator is unsupported by this implementation of the filter.|
|15021|An unexpected token was encountered.|
|15022|The requested operation cannot be performed over an enabled direct channel. The channel must first be disabled.|
|15023|Channel property %1 contains an invalid value. The value has an invalid type, is outside of its valid range, cannot be changed, or is not supported by this type of channel.|
|15024|Publisher property %1 contains an invalid value. The value has an invalid type, is outside of its valid range, cannot be changed, or is not supported by this type of publisher.|
|15025|The channel failed to activate.|
|15026|The XPath expression exceeded the supported complexity. Simplify the expression or split it into multiple expressions.|
|15027|The message resource is present but the message was not found in the message table.|
|15028|The message ID for the desired message could not be found.|
|15029|The substitution string for insert index (%1) could not be found.|
|15030|The description string for parameter reference (%1) could not be found.|
|15031|The maximum number of replacements has been reached.|
|15032|The event definition could not be found for event ID (%1).|
|15033|The locale specific resource for the desired message is not present.|
|15034|The resource is too old and is not supported.|
|15035|The resource is too new and is not supported.|
|15036|The channel at index %1!d! of the query can't be opened.|
|15037|The publisher has been disabled and its resource is not available. This usually occurs when the publisher is in the process of being uninstalled or upgraded.|
|15038|Attempted to create a numeric type that is outside of its valid range.|
|15080|The subscription fails to activate.|
|15081|The log of the subscription is in disabled state, and can not be used to forward events to. The log must first be enabled before the subscription can be activated.|
|15082|When forwarding events from local machine to itself, the query of the subscription can't contain target log of the subscription.|
|15083|The credential store that is used to save credentials is full.|
|15084|The credential used by this subscription can't be found in credential store.|
|15085|No active channel is found for the query.|
|15100|The resource loader failed to find MUI file.|
|15101|The resource loader failed to load MUI file because the file fail to pass validation.|
|15102|The RC Manifest is corrupted with garbage data or unsupported version or missing required item.|
|15103|The RC Manifest has invalid culture name.|
|15104|The RC Manifest has invalid ultimatefallback name.|
|15105|The resource loader cache doesn't have loaded MUI entry.|
|15106|User stopped resource enumeration.|
|15107|UI language installation failed.|
|15108|Locale installation failed.|
|15110|A resource does not have default or neutral value.|
|15111|Invalid PRI config file.|
|15112|Invalid file type.|
|15113|Unknown qualifier.|
|15114|Invalid qualifier value.|
|15115|No Candidate found.|
|15116|The ResourceMap or NamedResource has an item that does not have default or neutral resource..|
|15117|Invalid ResourceCandidate type.|
|15118|Duplicate Resource Map.|
|15119|Duplicate Entry.|
|15120|Invalid Resource Identifier.|
|15121|Filepath too long.|
|15122|Unsupported directory type.|
|15126|Invalid PRI File.|
|15127|NamedResource Not Found.|
|15135|ResourceMap Not Found.|
|15136|Unsupported MRT profile type.|
|15137|Invalid qualifier operator.|
|15138|Unable to determine qualifier value or qualifier value has not been set.|
|15139|Automerge is enabled in the PRI file.|
|15140|Too many resources defined for package.|
|15141|Resource File can not be used for merge operation.|
|15142|Load/UnloadPriFiles cannot be used with resource packages.|
|15143|Resource Contexts may not be created on threads that do not have a CoreWindow.|
|15144|The singleton Resource Manager with different profile is already created.|
|15145|The system component cannot operate given API operation|
|15146|The resource is a direct reference to a non-default resource candidate.|
|15147|Resource Map has been re-generated and the query string is not valid anymore.|
|15148|The PRI files to be merged have incompatible versions.|
|15149|The primary PRI files to be merged does not contain a schema.|
|15150|Unable to load one of the PRI files to be merged.|
|15151|Unable to add one of the PRI files to the merged file.|
|15152|Unable to create the merged PRI file.|
|15153|Packages for a PRI file merge must all be from the same package family.|
|15154|Packages for a PRI file merge must not include multiple main packages.|
|15155|Packages for a PRI file merge must not include bundle packages.|
|15156|Packages for a PRI file merge must include one main package.|
|15157|Packages for a PRI file merge must include at least one resource package.|
|15158|Invalid name supplied for a canonical merged PRI file.|
|15159|Unable to find the specified package.|
|15160|No default value for language was specified.|
|15161|An entity was defined as both resource and scope, which is not allowed.|
|15200|The monitor returned a DDC/CI capabilities string that did not comply with the ACCESS.bus 3.0, DDC/CI 1.1 or MCCS 2 Revision 1 specification.|
|15201|The monitor's VCP Version (0xDF) VCP code returned an invalid version value.|
|15202|The monitor does not comply with the MCCS specification it claims to support.|
|15203|The MCCS version in a monitor's mccs_ver capability does not match the MCCS version the monitor reports when the VCP Version (0xDF) VCP code is used.|
|15204|The Monitor Configuration API only works with monitors that support the MCCS 1.0 specification, MCCS 2.0 specification or the MCCS 2.0 Revision 1 specification.|
|15205|An internal Monitor Configuration API error occurred.|
|15206|The monitor returned an invalid monitor technology type. CRT, Plasma and LCD (TFT) are examples of monitor technology types. This error implies that the monitor violated the MCCS 2.0 or MCCS 2.0 Revision 1 specification.|
|15207|The caller of SetMonitorColorTemperature specified a color temperature that the current monitor did not support. This error implies that the monitor violated the MCCS 2.0 or MCCS 2.0 Revision 1 specification.|
|15250|The requested system device cannot be identified due to multiple indistinguishable devices potentially matching the identification criteria.|
|15299|The requested system device cannot be found.|
|15300|Hash generation for the specified hash version and hash type is not enabled on the server.|
|15301|The hash requested from the server is not available or no longer valid.|
|15321|The secondary interrupt controller instance that manages the specified interrupt is not registered.|
|15322|The information supplied by the GPIO client driver is invalid.|
|15323|The version specified by the GPIO client driver is not supported.|
|15324|The registration packet supplied by the GPIO client driver is not valid.|
|15325|The requested operation is not supported for the specified handle.|
|15326|The requested connect mode conflicts with an existing mode on one or more of the specified pins.|
|15327|The interrupt requested to be unmasked is not masked.|
|15400|The requested run level switch cannot be completed successfully.|
|15401|The service has an invalid run level setting. The run level for a service<br>must not be higher than the run level of its dependent services.|
|15402|The requested run level switch cannot be completed successfully since<br>one or more services will not stop or restart within the specified timeout.|
|15403|A run level switch agent did not respond within the specified timeout.|
|15404|A run level switch is currently in progress.|
|15405|One or more services failed to start during the service startup phase of a run level switch.|
|15501|The task stop request cannot be completed immediately since<br>task needs more time to shutdown.|
|15600|Package could not be opened.|
|15601|Package was not found.|
|15602|Package data is invalid.|
|15603|Package failed updates, dependency or conflict validation.|
|15604|There is not enough disk space on your computer. Please free up some space and try again.|
|15605|There was a problem downloading your product.|
|15606|Package could not be registered.|
|15607|Package could not be unregistered.|
|15608|User cancelled the install request.|
|15609|Install failed. Please contact your software vendor.|
|15610|Removal failed. Please contact your software vendor.|
|15611|The provided package is already installed, and reinstallation of the package was blocked. Check the AppXDeployment-Server event log for details.|
|15612|The application cannot be started. Try reinstalling the application to fix the problem.|
|15613|A Prerequisite for an install could not be satisfied.|
|15614|The package repository is corrupted.|
|15615|To install this application you need either a Windows developer license or a sideloading-enabled system.|
|15616|The application cannot be started because it is currently updating.|
|15617|The package deployment operation is blocked by policy. Please contact your system administrator.|
|15618|The package could not be installed because resources it modifies are currently in use.|
|15619|The package could not be recovered because necessary data for recovery have been corrupted.|
|15620|The signature is invalid. To register in developer mode, AppxSignature.p7x and AppxBlockMap.xml must be valid or should not be present.|
|15621|An error occurred while deleting the package's previously existing application data.|
|15622|The package could not be installed because a higher version of this package is already installed.|
|15623|An error in a system binary was detected. Try refreshing the PC to fix the problem.|
|15624|A corrupted CLR NGEN binary was detected on the system.|
|15625|The operation could not be resumed because necessary data for recovery have been corrupted.|
|15626|The package could not be installed because the Windows Firewall service is not running. Enable the Windows Firewall service and try again.|
|15627|Package move failed.|
|15628|The deployment operation failed because the volume is not empty.|
|15629|The deployment operation failed because the volume is offline. For a package update, the volume refers to the installed volume of all package versions.|
|15630|The deployment operation failed because the specified volume is corrupt.|
|15631|The deployment operation failed because the specified application needs to be registered first.|
|15632|The deployment operation failed because the package targets the wrong processor architecture.|
|15633|You have reached the maximum number of developer sideloaded packages allowed on this device. Please uninstall a sideloaded package and try again.|
|15634|A main app package is required to install this optional package.  Install the main package first and try again.|
|15635|This app package type is not supported on this filesystem|
|15636|Package move operation is blocked until the application has finished streaming|
|15637|A main or another optional app package has the same application ID as this optional package.  Change the application ID for the optional package to avoid conflicts.|
|15638|This staging session has been held to allow another staging operation to be prioritized.|
|15639|A related set cannot be updated because the updated set is invalid. All packages in the related set must be updated at the same time.|
|15640|An optional package with a FullTrust entry point requires the main package to have the runFullTrust capability.|
|15641|An error occurred because a user was logged off.|
|15642|An optional package provision requires the dependency main package to also be provisioned.|
|15643|The packages failed the SmartScreen reputation check.|
|15644|The SmartScreen reputation check operation timed out.|
|15645|The current deployment option is not supported.|
|15646|Activation is blocked due to the .appinstaller update settings for this app.|
|15647|Remote drives are not supported; use \\server\share to register a remote package.|
|15648|Failed to process and write downloaded APPX package data to disk.|
|15649|The deployment operation was blocked due to a per-package-family policy restricting deployments on a non-system volume. Per policy, this app must be installed to the system drive, but that's not set as the default. In Storage Settings, make the system drive the default location to save new content, then retry the install.|
|15650|The deployment operation was blocked due to a machine-wide policy restricting deployments on a non-system volume. Per policy, this app must be installed to the system drive, but that's not set as the default. In Storage Settings, make the system drive the default location to save new content, then retry the install.|
|15651|The deployment operation was blocked because Special profile deployment is not allowed. Please try logging into an account that is not a Special profile. You can try logging out and logging back into the current account, or try logging into a different account.|
|15652|The deployment operation failed due to a conflicting package's mutable package directory. To install this package remove the existing package with the conflicting mutable package directory.|
|15653|The package installation failed because a singleton resource was specified and another user with that package installed is logged in. Please make sure that all active users with the package installed are logged out and retry installation.|
|15654|The package installation failed because a different version of the service is installed. Try installing a newer version of the package.|
|15655|The package installation failed because a version of the service exists outside of APPX packaging. Please contact your software vendor.|
|15656|The package installation failed because administrator privileges are required. Please contact an administrator to install this package.|
|15657|The package deployment failed because the operation would have redirected to default account, when the caller said not to do so.|
|15658|The package deployment failed because the package requires a capability to natively target this host.|
|15659|The package deployment failed because its content is not valid for an unsigned package.|
|15660|The package deployment failed because its publisher is not in the unsigned namespace.|
|15661|The package deployment failed because its publisher is not in the signed namespace.|
|15662|The package deployment failed because it must allow external content to be deployed with an external location.|
|15663|A host runtime dependency resolving to a package with full trust content requires the main package to have the runFullTrust capability.|
|15664|The package deployment failed because the package requires a capability for mandatory startup tasks.|
|15665|Package failed host runtime dependency or conflict validation.|
|15666|The package deployment failed because it uses a machine scope but doesn't have the required capability.|
|15667|The package deployment failed because it uses classic compatmode but doesn't have the required capability.|
|15668|AppxUpdateAgent attempted to stage a package that is not applicable.|
|15669|The application cannot be started for the target user.  Please have the user explicitly install this package.|
|15670|The provided package name does not match the expected package name. Check the AppXDeployment-Server event log for details.|
|15671|The provided .appinstaller URI is already being used by another package family. Check the AppXDeployment-Server event log for details.|
|15672|The package family's auto update settings are being managed at system priority and cannot be changed at default priority. Please contact your system administrator for help with the error.|
|15700|The process has no package identity.|
|15701|The package runtime information is corrupted.|
|15702|The package identity is corrupted.|
|15703|The process has no application identity.|
|15704|One or more AppModel Runtime group policy values could not be read. Please contact your system administrator with the contents of your AppModel Runtime event log.|
|15705|One or more AppModel Runtime group policy values are invalid. Please contact your system administrator with the contents of your AppModel Runtime event log.|
|15706|The package is currently not available.|
|15707|The package does not have a mutable directory.|
|15800|Loading the state store failed.|
|15801|Retrieving the state version for the application failed.|
|15802|Setting the state version for the application failed.|
|15803|Resetting the structured state of the application failed.|
|15804|State Manager failed to open the container.|
|15805|State Manager failed to create the container.|
|15806|State Manager failed to delete the container.|
|15807|State Manager failed to read the setting.|
|15808|State Manager failed to write the setting.|
|15809|State Manager failed to delete the setting.|
|15810|State Manager failed to query the setting.|
|15811|State Manager failed to read the composite setting.|
|15812|State Manager failed to write the composite setting.|
|15813|State Manager failed to enumerate the containers.|
|15814|State Manager failed to enumerate the settings.|
|15815|The size of the state manager composite setting value has exceeded the limit.|
|15816|The size of the state manager setting value has exceeded the limit.|
|15817|The length of the state manager setting name has exceeded the limit.|
|15818|The length of the state manager container name has exceeded the limit.|
|15841|This API cannot be used in the context of the caller's application type.|
|15861|This PC does not have a valid license for the application or product.|
|15862|The authenticated user does not have a valid license for the application or product.|
|15863|The commerce transaction associated with this license is still pending verification.|
|15864|The license has been revoked for this user.|