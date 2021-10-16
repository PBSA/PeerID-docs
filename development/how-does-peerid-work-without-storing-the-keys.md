# How does PeerID work without storing the keys ?

### Introduction

With the implementation of Hierarchical Role based Permissions (HRP) in the Peerplays blockchain and the introduction of Custom Authorities, it is now possible to allow a proxy account to perform any operation on the Peerplays blockchain on your behalf. PeerID uses this feature to act as a proxy for any account that has provided the permission to perform a particular operations.

### Custom Permissions

Every account that’s created on Peerplays has two default permissions by default.

1. Owner
2. Active

They have a parent-child relationship by default (owner being the parent). The implicit default permission linked to all operations is active, which sits one level below the owner permission within the hierarchy structure.

As a result, the active permission can do anything the owner permission can, except changing the keys associated with the owner.

With custom permissions, the permissions can be created separately and can be assigned the valid required authorities which satisfies the maximum recursion depth of the blockchain and the permissions can be linked to the operations through custom authorities which specifies the time validity of the permission over the operation. Any given permission of an account can be linked to multiple types of operations.

This gives applications flexibility to use the custom permission of an account and at the same time specify the validity.

### Custom Authorities

In Peerplays (graphene-based chains), an authority consists of one or many entities that authorize an operation, such as transfers or bet placement, etc. Authority consists of one or several pairs of an account name with a weight. In order to obtain a valid transaction, the sum of the weights from signing the parties has to exceed the threshold as defined in the permissions.

Custom Authorities takes this concept to the next level with the help of Custom Permissions by storing the mapping between custom permissions and operations. The custom authorities specify the actual operation on the Peerplays blockchain that a proxy account can perform on behalf of another account and the validity of this arrangement.

### Working of PeerID

As soon as an account is created or an existing Peerplays account logs in using PeerID, we create a custom permission for PeerID on the Peerplays blockchain to perform the `custom_authority_create`, `custom_authority_update`, `custom_authority_delete` operations on behalf of the account. 

PeerID further allows developers to create an app which can request for additional permissions from the user. When the user joins the app by allowing the app to perform some operation on his behalf, PeerID creates a custom authority for the requested operation by using its own custom permission. This way, we don't have to store the user's keys anywhere.

![Working of PeerID](<../.gitbook/assets/Screen Shot 2021-01-25 at 10.28.20 AM.png>)
