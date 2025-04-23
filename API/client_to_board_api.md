# Board to Board API
## Changelog

|Name|Date|description|
|---|---|---|
|Brooke Leinberger|2025-03-20|Init|

## Objective
Defines the inteface for community members to interact with the Community Board

## Overview
Basic REST API for user interaction.

## Commands

### Handshake
Returns an "about me" style description of the community. E.G. the name, version number, and other TBD values (such as potentially GPS location, network statistics, etc).

### Establish Encryption
Establishes secure end-to-end encryption for inter-board communication.

### MessageMember
Sends a UTF8 message to a member of the community.

### RegisterUser
Creates a user to be able to access a community.

TAKE INSPIRATION FROM COMMANDS:
chmod
chown
chgrp

### Read Permission Enums:
- Not allowed to read (0)
- Allowed to read (1)

### Write Permission Enums:
- Not allowed to write (0)
- Append (1)
- Overwrite (2)

### GrantUserPermissions
<blockquote>
PARAMETERS: <br>
1. User ID <br>
2. Chosen read permission <br>
3. Chosen write permission <br>
4. File path(s)
</blockquote>
<br>
Grants a community member specific permissions for a certain file path.

### CreateGroup
<blockquote>
PARAMETERS: <br>
1. Name <br>
</blockquote>
<br>
Creates a group that can be assigned permissions for a certain file path.

### GrantGroupPermissions
<blockquote>
PARAMETERS: <br>
1. Group ID <br>
2. Chosen read permission <br>
3. Chosen write permission <br>
4. File path(s)
</blockquote>
<br>
Grants a community group specific permissions for a certain file path.

### DeleteGroup
<blockquote>
PARAMETERS: <br>
1. Group ID <br>
</blockquote>
<br>
Deletes a group by ID.


