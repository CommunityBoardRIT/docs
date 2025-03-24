# Board to Board API
## Changelog

## Objective

Defines the inteface for the bidirectional communication between different instances of the CommunityBoard application.

The heart of the community board (as it stands at the moment), is to enable the disemination of information across a small community, without relying on existing infrastructure outside of the community's control.

## Overview
TBD

## Commands

### Handshake
Returns an "about me" style description of the community. E.G. the name, version number, and other TBD values (such as potentially GPS location, network statistics, etc).

### Establish Encryption
Establishes secure end-to-end encryption for inter-board communication.

### MessageMember
Sends a UTF8 message to a member of the community.

### RequestAssociation
Sends an assosciation request to the admin of the community. Enables information sharing, as defined by the target community's infosec policy.

### DeleteAssociation
Removes a previously established association

### InitiateSync
Syncs files permitted by the communities' infosec policies