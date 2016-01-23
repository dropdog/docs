## Development thoughts
--------------------------

### On ```settings.php```

- Use prefixes by table for the database in order to exclude tables from database import/export processes.
- Store user generated files (```sites/*/files```) on external storage and get files from there for any new build.
- Disable update_manager from Drupal ui and allow updates only from ssh.
- Live site should have the [trusted_host_patterns] to allow http requests.
- Set ```cookie_domain``` to allow logged in users to move between multidomains.
- Use ```local.settings.php``` and ```development.services.yml``` for custom development settings. Do not enable this on live site!
- Move ```config*``` files out of sites/* folder.

### On ```services.yml```

- Modify the ```renderer_cache_contexts``` to alter cache settings.
- Create custom cache tags for rendering caching and add them to ```autoplaceholder_conditions``` variable.


### Other

- Every functionality that is strongly related with the development [parameters](/parameters) should be implemented as **entityreference** (eg the language of a block).
- Dump database should be exported from live site (master) every n hours.
- Create a list of things for the customer to check on every release.
