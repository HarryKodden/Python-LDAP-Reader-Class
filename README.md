# Python-LDAP-Reader-Class
Python Class for reading People and Group tree from LDAP

## Usage:

```Python
    from LDAP import LDAP as ldap_connection
    from dotenv import load_dotenv

    ...
    try:
        logger.debug("Connection to LDAP...")

        load_dotenv()

        with ldap_connection(
            os.environ.get("LDAP_HOST", "localhost"),
            os.environ.get("LDAP_BASE", "dc=example,dc=com"),
            os.environ.get("LDAP_BIND", "cn=admin,dc=example,dc=com"),
            os.environ.get("LDAP_PASS", ""),
            os.environ.get("LDAP_MODE", "IP_V4_ONLY"),    
        ) as src:

        ...
        logger.debug("LDAP Tree: {}".format(src))
        ...


    except Exception as e:
        logger.error("Exception: " + str(e))

    ...
```

## Configuration

The configuration is controlled via environment variables. You can provide them for example via a **.env** file. See example file.

Config | Meaning | Example | default
--- | --- | --- | ---
LDAP_HOST | ldap host address | "ldaps://example.org" | none
LDAP_BASE | ldap base location | "dc=...,dc=example,dc=org" | none
LDAP_BIND | ldap bind username | "cn=admin,dc=...,dc=example,dc=org" | none
LDAP_PASS | ldap bind password | "admin-password" | none
LDAP_MODE | ldap network mode | "IP_V4_ONLY" | "IP_V6_PREFERRED"
LDAP_USER_KEY | the attribute identifying a person | "cn | "uid"
LDAP_GROUP_KEY | the attribute identifying a group | "cn" | "cn"
LDAP_FILTER | the filter identifying groupmembership | "objectCLass=member" | "objectCLass=groupOfMembers"

