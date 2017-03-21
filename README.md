## Multi-Pass

![Lilu Dallas](https://s-media-cache-ak0.pinimg.com/564x/54/f5/68/54f568be0db4765002160044ce099d89.jpg)x
## Abstract
A simple method of maintaining a list of social media accounts with the ability to verify ownership using a smart contract on the Ethereum classic chain. Multi pass accounts are anchored to social media accounts by linking to a post declaring the multi pass exists. A simple zK proofing system for indicating ownership is built in with the verifier function. Only the person in control of the owner key can update the verifier text. This can be used to prove active ownership of all accounts. 

## Deploying
Some steps to deploy on parity
1) copy and paste contract
2) deploys
3) add Owner info
4) start adding accounts
## Anchoring posts
A post on a social media site referencing your multipass that is stored on the multi pass. I.E. the url from a tweet indicating  control of multipass contract at 0x…. that is stored on ones multi pass
## Verifying
Multi pass addresses are intended to be shared. An owner can prove that they are in control of a multi pass by use of the verify() function. 
Example:
Victor and Paula are on a new social media site together. Paula is famous and she has many impersonators.  Victor would like Paula to show proof that she is, in fact, the real Paula. 
Victor knows that the real Paula has social media accounts sm(1), sm(2), sm(n). The real Paula has made anchoring posts on all of her sm sites as part of establishing her multi pass. And Victor knows the real Paula’s multi pass contract. 
In order to test Paula, Victor gives her a phrase to change the verifying phrase on the multi pass too, and watches the contract for the change. Only the owner of the multi pass can change the verifying phrase. If the phrase changes, Victor can better trust that Paula is in fact real. Repeating this process ensures victor that the Paula he is in contact with is most likely the real Paula. 


## Terms
#### Split ABI

#### Owner ABI
Used by the contract owner for maintenance of the contract
`[{"constant":true,"inputs":[{"name":"_index","type":"uint256"}],"name":"userName","outputs":[{"name":"","type":"string"}],"payable":false,"type":"function"},{"constant":true,"inputs":[],"name":"verifier","outputs":[{"name":"","type":"string"}],"payable":false,"type":"function"},{"constant":true,"inputs":[{"name":"_index","type":"uint256"}],"name":"aSites","outputs":[{"name":"","type":"string"}],"payable":false,"type":"function"},{"constant":true,"inputs":[],"name":"extUrl","outputs":[{"name":"","type":"string"}],"payable":false,"type":"function"},{"constant":false,"inputs":[],"name":"kill","outputs":[],"payable":false,"type":"function"},{"constant":true,"inputs":[],"name":"title","outputs":[{"name":"","type":"string"}],"payable":false,"type":"function"},{"constant":false,"inputs":[],"name":"bailout","outputs":[],"payable":false,"type":"function"},{"constant":false,"inputs":[{"name":"_msg","type":"string"}],"name":"veriPass","outputs":[],"payable":false,"type":"function"},{"constant":true,"inputs":[{"name":"_index","type":"uint256"}],"name":"getSite","outputs":[{"name":"","type":"string"}],"payable":false,"type":"function"},{"constant":true,"inputs":[],"name":"avatar","outputs":[{"name":"","type":"string"}],"payable":false,"type":"function"},{"constant":true,"inputs":[{"name":"_index","type":"uint256"}],"name":"GetProfile","outputs":[{"name":"","type":"string"}],"payable":false,"type":"function"},{"constant":true,"inputs":[],"name":"description","outputs":[{"name":"","type":"string"}],"payable":false,"type":"function"},{"constant":true,"inputs":[],"name":"author","outputs":[{"name":"","type":"string"}],"payable":false,"type":"function"},{"constant":false,"inputs":[{"name":"_author","type":"string"},{"name":"_title","type":"string"},{"name":"_description","type":"string"},{"name":"_extUrl","type":"string"},{"name":"_avatar","type":"string"}],"name":"startMultipass","outputs":[],"payable":false,"type":"function"},{"constant":true,"inputs":[],"name":"creationTime","outputs":[{"name":"","type":"uint256"}],"payable":false,"type":"function"},{"constant":false,"inputs":[{"name":"_action","type":"uint256"},{"name":"_index","type":"uint256"},{"name":"_aSite","type":"string"},{"name":"_aUsrname","type":"string"},{"name":"_aUrl","type":"string"}],"name":"modPass","outputs":[],"payable":false,"type":"function"},{"anonymous":false,"inputs":[{"indexed":false,"name":"site","type":"string"},{"indexed":false,"name":"username","type":"string"},{"indexed":false,"name":"url","type":"string"}],"name":"newComment","type":"event"},{"anonymous":false,"inputs":[{"indexed":false,"name":"verification","type":"string"}],"name":"verification","type":"event"}]`

#### User ABI
To be used by parties looking to verify an account. Could be intigrated into block explorers that are cabable of displaying tokens and other similar abi

`[{"constant":true,"inputs":[],"name":"creationTime","outputs":[{"name":"","type":"uint256"}],"payable":false,"type":"function"},{"constant":true,"inputs":[],"name":"avatar","outputs":[{"name":"","type":"string"}],"payable":false,"type":"function"},{"constant":true,"inputs":[],"name":"author","outputs":[{"name":"","type":"string"}],"payable":false,"type":"function"},{"constant":true,"inputs":[],"name":"title","outputs":[{"name":"","type":"string"}],"payable":false,"type":"function"},{"constant":true,"inputs":[],"name":"description","outputs":[{"name":"","type":"string"}],"payable":false,"type":"function"},{"constant":true,"inputs":[],"name":"extUrl","outputs":[{"name":"","type":"string"}],"payable":false,"type":"function"},{"constant":true,"inputs":[],"name":"verifier","outputs":[{"name":"","type":"string"}],"payable":false,"type":"function"},{"constant":true,"inputs":[{"name":"_index","type":"uint256"}],"name":"getSite","outputs":[{"name":"","type":"string"}],"payable":false,"type":"function"},{"constant":true,"inputs":[{"name":"_index","type":"uint256"}],"name":"userName","outputs":[{"name":"","type":"string"}],"payable":false,"type":"function"},{"constant":true,"inputs":[{"name":"_index","type":"uint256"}],"name":"GetProfile","outputs":[{"name":"","type":"string"}],"payable":false,"type":"function"}]`

#### Variables

Author - the owner of the contract

avatar - a html link to an image of the owner

Creation Time - when the contract was deployed

Description - A brief biox

Ext Url - A main link for the owner

aSite - A social media site i.e. Twitter

aUsrName - the owners handle on the site

aUrl - a link to the profile

Verifier - used to post verification messages

## Functions

#### startMultipass

Starts the multipass. fills out thie initial public information 

TODO: add abality to register at a central list

#### veriPass

A string that can oly be changed by the owner but read by anyone

#### modPass

Used to add and remove accounts to a multipass

### Mode 1 - Add a new account

requires: 

Action number (1)

index (ignored)

aSite (the social site name. i.e. twitter)

aUsrname (the owners handle)

aUrl (url of profile)

#### Mode 2 = Delete a listed account

Action number (2)

index (index of account to remove)

### Mode 3 - Add a new account

requires: 

Action number (3)

index (index of account to modify)

aSite (the social site name. i.e. twitter)

aUsrname (the owners handle)

aUrl (url of profile)







