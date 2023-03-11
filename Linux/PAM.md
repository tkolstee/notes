Linux Pluggable Authentication Modules


```toc
```
## Syntax
lines are:

```service type control module-path module-arguments```

Incorrectly-formatted lines, missing modules, etc. tend to return failure and log the error.

### Service
account - management of account, not authorization
auth - authentication and authorization
password - Updating authentication tokens
session - manage steps before and after accessing service

### Type

#### Bracket Notation

```[value1=action1 value2=action2 ...]```

##### Value:
- It's common to just use "success" and "default"
- Default includes all others not mentioned.

Complete list:
success, open_err, symbol_err, service_err, system_err, buf_err,
perm_denied, auth_err, cred_insufficient, authinfo_unavail,
user_unknown, maxtries, new_authtok_reqd, acct_expired,
session_err, cred_unavail, cred_expired, cred_err, no_module_data,
conv_err, authtok_err, authtok_recover_err, authtok_lock_busy,
authtok_disable_aging, try_again, ignore, abort, authtok_expired,
module_unknown, bad_item, conv_again, incomplete, and default.

##### Action

| Keyword   | Continue Processing?        | Contribution to stack return code                |
| --------- | --------------------------- | ------------------------------------------------ |
| ignore    | yes                         | none                                             |
| bad       | yes                         | failure                                          |
| die       | no                          | failure                                          |
| ok        | yes                         | success if no failures elsewhere                 |
| done      | no                          | success if no prior failures                     |
| (integer) | skip *n* rules and continue | depends upon module                              |
| reset     | yes                         | clear all prior state and start with next module |

#### Preset types and bracket notation equivalents
| name       | success= | new_authtok_required= | ignore= | default= |
| ---------- | -------- | --------------------- | ------- | -------- |
| required   | ok       | ok                    | ignore  | bad      |
| requisite  | ok       | ok                    | ignore  | die      |
| sufficient | done     | done                  | ignore  |          |
| optional   | ok       | ok                    | ignore  |          |

### Module-path
- absolute or relative path of the PAM module to use
- relative paths are to the default path, /lib/security or /lib64/security depending upon platform

### Module Arguments
- Space-separated list of tokens that are specific to the module.
- If an argument includes spaces, surround it with square brackets:
```
	squid auth required pam_mysql.so user=passwd_query passwd=mada \
		db=eminence [query=select user_name from internet_service \
		where user_name='%u' and password=PASSWORD('%p') and service='web_proxy']
```

----
# Sources
[linux-pam](http://www.linux-pam.org/Linux-PAM-html/sag-configuration-file.html)

