# Python-LDAP-Reader-Class
Python Class for reading People and Group tree from LDAP

Usage:

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
