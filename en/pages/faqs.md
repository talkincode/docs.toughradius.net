## 常见问题


#### Regarding dialing 691, why is the password correct? Dial-up authentication will also prompt 691 password error?

Is 691 a general error defined by the authentication protocol, but it does not mean that it is a password error. He indicates that the backend authentication has an error, which causes the authentication to fail. The reason for the authentication failure may be that the account expires, the password is incorrect, and the account does not exist. The MAC or VLAN is incorrectly bound, the account is online, etc. You can use the system log to query the user for the authentication failure. In the system log interface, enter the user name as the keyword to query.

