# Governance

## Change levels

The level of change correlates strongly with the *risk* introduced by the change.

### Non-functional

Non-functional don't affect the user experience at all.

For example: 

* Changes to code comments
* Changes documentation within the repository
* Typo fixes in strings displayed to users


### Minor

Minor changes affect user experience but are unlikely to introduce problems for users. 

For example:

* Changes to user-displayed strings which alter the meaning of concepts displayed to users
* Adding an optional new field to an API.



### Major

Major changes affect user experience and have some risk of introducing problems for users.

For example:

* Changes which alter the values returned from the same API call. 
* DB schema changes
* Adding new pages/forms


