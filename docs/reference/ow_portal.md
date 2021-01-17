---
layout: default
title: ow.portal
parent: Reference
grand_parent: OpenAF docs
---


## ow.portal

### ow.portal.addRole

__ow.portal.addRole(aAF, aName, aTitleMap, aDescriptionMap, aType) : Map__

````
Adds/Creates a role with aName on the aAF server (portal connection). Optionally you can provide aTitleMap (with localized titles) and/or aDescriptionMap (with localized descriptions) and/or aType (defaults to 0).
````
### ow.portal.addRolesToUserId

__ow.portal.addRolesToUserId(aAF, aUserId, anArrayOfRoles) : Map__

````
Adds all role's ids from anArrayOfRoles to the aUserId on the aAF server (portal connections).
````
### ow.portal.addRoleToUser

__ow.portal.addRoleToUser(aAF, aScreenName, aRoleName) : Map__

````
Adds aRoleName to the user identified by aScreenName from the aAF server connection (portal connection).
````
### ow.portal.addUser

__ow.portal.addUser(aAF, aUserMap)__

````
Adds aUserMap user to aAF server (portal connection). aUserMap can contain the following entries:

var user = {
  "companyId": aCompanyId,
  "autoPassword": false,
  "password1": aPassword,
  "password2": aPassword,
  "autoScreenName": false,
   "screenName": aScreenName,
   "emailAddress": aEmailAddress,
   "facebookId": 0,
   "openId": "",
   "locale": "",
   "firstName": aFirstName,
   "middleName": aMiddleName,
   "lastName": aLastName,
   "prefixId": 0,
   "suffixId": 0,
   "male": isMale,
   "birthdayMonth": 0,
   "birthdayDay": 1,
   "birthdayYear": 1970,
   "jobTitle": "",
   "groupIds": groupIds, // Array of ids
   "organizationIds": organizationIds, // Array of ids
   "roleIds": roleIds, // Array of ids
   "userGroupIds": userGroupIds, // Array of ids
   "sendEmail": false
};

````
### ow.portal.addUserGroup

__ow.portal.addUserGroup(aAF, aGroupName, aGroupDescription)__

````
Adds a new aGroupName with the corresponding aGroupDescription for the aAF server (portal) connection.
````
### ow.portal.assignPasswordPolicy

__ow.portal.assignPasswordPolicy(aAF, aPasswordPolicyId, listOfUsersIds)__

````
Adds aPasswordPolicyId for the listOfUsersIds array for the aAF server (portal) connection.
````
### ow.portal.deactivateUser

__ow.portal.deactivateUser(aAF, aScreenname)__

````
Deactivates a user identified by aScreenname for the aAF server (portal) connection.
````
### ow.portal.deleteRole

__ow.portal.deleteRole(aAF, aRoleId) : Map__

````
Deletes a role with aRoleId on the aAF server (portal connection).
````
### ow.portal.deleteUser

__ow.portal.deleteUser(aAF, aScreenName) : Map__

````
Removes user identified by aScreenName from the aAF server connection (portal connection).
````
### ow.portal.getCompany

__ow.portal.getCompany(aAF, aVirtualHost) : Map__

````
Returns the aAF server (portal connection) portal's company map. Optionally you can provide  a specific aVirtualHost if one is in use (defaults to 'localhost').
````
### ow.portal.getCompanyId

__ow.portal.getCompanyId(aAF, aVirtualHost) : Map__

````
Returns the aAF server (portal connection) portal's company id. Optionally you can provide  a specific aVirtualHost if one is in use (defaults to 'localhost').
````
### ow.portal.getRoleById

__ow.portal.getRoleById(aAF, aRoleId, aCompany) : Map__

````
Returns, from the aAF server (portal connection), the information for aRoleId. Optionally you can provide aCompany (defaults to ow.portal.getCompany).
````
### ow.portal.getRoleByName

__ow.portal.getRoleByName(aAF, aRoleName, aCompany) : Map__

````
Returns, from the aAF server (portal connection), the information for aRoleName. Optionally you can provide aCompany (defaults to ow.portal.getCompany).
````
### ow.portal.getRolesFromUser

__ow.portal.getRolesFromUser(aAF, aUserId) : Map__

````
Returns aUserID information from aAF server (portal connection).
````
### ow.portal.getUserByEmail

__ow.portal.getUserByEmail(aAF, anEmail, aCompany) : Map__

````
Returns, from the aAF server (portal connection), the information for anEmail address. Optionally you can provide aCompany (defaults to ow.portal.getCompany).
````
### ow.portal.getUserByScreenName

__ow.portal.getUserByScreenName(aAF, aScreenName, aCompany) : Map__

````
Returns, from the aAF server (portal connection), the information for aScreenName user. Optionally you can provide aCompany (defaults to ow.portal.getCompany).
````
### ow.portal.getUserGroupsByUser

__ow.portal.getUserGroupsByUser(aAF, aScreenname) : Array__

````
Retrieves the list of the current usergroups currently associated with aScreenname.
````
### ow.portal.getUserList

__ow.portal.getUserList(aAF, aCompany, aLimitNumberOfUsers) : Array__

````
Returns, from the aAF server (portal connection), the list of users. Optionally you can provide aCompany  (defaults to ow.portal.getCompany) and aLimitNumberOfUsers (defaults to 999999).
````
### ow.portal.getUserRoles

__ow.portal.getUserRoles(aAF, aScreenName) : Map__

````
Obtains the list of roles for the user identified by aScreenName from the aAF server connection (portal connection).
````
### ow.portal.removeRoleFromUser

__ow.portal.removeRoleFromUser(aAF, aScreenName, aRoleName) : Map__

````
Removes aRoleName from the user identified by aScreenName from the aAF server connection (portal connection).
````
### ow.portal.removeRoleFromUserId

__ow.portal.removeRoleFromUserId(aAF, aUserId, anArrayOfRoles) : Map__

````
Unsets all role's ids, in anArrayOfRoles, from aUserId on the aAF server (portal connections).
````
### ow.portal.unlockUser

__ow.portal.unlockUser(aAF, userId) : Map__

````
Tries to unlock userId from the aAF server (portal connection). You can use ow.portal.getUserList or ow.portal.getUserByEmail or ow.portal.getUserByScreenName to retrieve the userId.
````
### ow.portal.wedoUserMan.activateUser

__ow.portal.wedoUserMan.activateUser(aAF, aScreenName) : Map__

````
Activates the user identified by aScreenName from the aAF server connection (portal connection)
````
### ow.portal.wedoUserMan.addRoleToUser

__ow.portal.wedoUserMan.addRoleToUser(aAF, aScreenName, aRoleName) : Map__

````
Adds aRoleName to the user identified by aScreenName from the aAF server connection (portal connection).
````
### ow.portal.wedoUserMan.addUser

__ow.portal.wedoUserMan.addUser(aAF, aUserObject) : Map__

````
Adds aUserObject to the aAF server connection (portal connection).
````
### ow.portal.wedoUserMan.addUserGroupToUser

__ow.portal.wedoUserMan.addUserGroupToUser(aAF, aScreenName, aGroupName) : Map__

````
Adds a user group aGroupName to the user identified by aScreenName from the aAF server connection (portal connection).
````
### ow.portal.wedoUserMan.deactivateUser

__ow.portal.wedoUserMan.deactivateUser(aAF, aScreenName, aReasonCode) : Map__

````
Deactivates a user identified by aScreenName from the aAF server connection (portal connection). Optionally you can provide aReasonCode where 0 is unspecified (default) and 1 is inactivity.
````
### ow.portal.wedoUserMan.deleteUser

__ow.portal.wedoUserMan.deleteUser(aAF, aScreenName) : Map__

````
Deletes the user identified by aScreenName from the aAF server connection (portal connection).
````
### ow.portal.wedoUserMan.getUserGroups

__ow.portal.wedoUserMan.getUserGroups(aAF, aScreenName) : Map__

````
Returns the user groups to which the user identified by aScreenName from the aAF server connection (portal connection) belongs to.
````
### ow.portal.wedoUserMan.getUserInfo

__ow.portal.wedoUserMan.getUserInfo(aAF, aScreenName) : Map__

````
Returns a map with user information for the user identified by aScreenName from the aAF server connection (portal connection).
````
### ow.portal.wedoUserMan.getUserRoles

__ow.portal.wedoUserMan.getUserRoles(aAF, aScreenName) : Map__

````
Obtains the list of roles for the user identified by aScreenName from the aAF server connection (portal connection).
````
### ow.portal.wedoUserMan.isAvailable

__ow.portal.wedoUserMan.isAvailable(aAF) : boolean__

````
Determines if the WeDo's User Management web services exist and are available (returns true if yes). Keeping in mind that you might need to add the role wsadmin to the user which you are using to login (see more in ow.portal.addRole and ow.portal.addRoleToUser).
````
### ow.portal.wedoUserMan.removeRoleFromUser

__ow.portal.wedoUserMan.removeRoleFromUser(aAF, aScreenName, aRoleName) : Map__

````
Removes aRoleName from the user identified by aScreenName from the aAF server connection (portal connection).
````
### ow.portal.wedoUserMan.removeUserGroupFromUser

__ow.portal.wedoUserMan.removeUserGroupFromUser(aAF, aScreenName, aGroupName) : Map__

````
Removes a user group aGroupName from the user identified by aScreenName from the aAF server connection (portal connection).
````
### ow.portal.wedoUserMan.resetUserPassword

__ow.portal.wedoUserMan.resetUserPassword(aAF, aScreenName, aPassword) : Map__

````
Resets the password of a user identified by aScreenName from the aAF server connection (portal connection) with a new aPassword.
````
### ow.portal.wedoUserMan.setUserGroups

__ow.portal.wedoUserMan.setUserGroups(aAF, aScreenName, anArrayOfUserGroups) : Map__

````
Assigns all user group's ids in anArrayOfUserGroups to the user identified by aScreenName from the aAF server connection (portal connection).
````
### ow.portal.wedoUserMan.updateUser

__ow.portal.wedoUserMan.updateUser(aAF, aScreenName, aUserObject) : Map__

````
Updates the user identified by aScreenName with aUserObject on the aAF server connection (portal connection).
````
