## Development thoughts
--------------------------

### On file ```settings.php```

- Use prefixes by table for the database in order to exclude tables from database import/export processes.
- Store user generated files (```sites/*/files```) on external storage and get files from there for any new build.
- Disable update_manager from Drupal ui and allow updates only from ssh.
- Live site should have the [trusted_host_patterns] to allow http requests.
- Set ```cookie_domain``` to allow logged in users to move between multidomains.
- Use ```local.settings.php``` and ```development.services.yml``` for custom development settings. Do not enable this on live site!
- Move ```config*``` files out of sites/* folder.
- Use `$settings['file_public_base_url']` variable to have the public files on external folder.

### On file ```services.yml```

- Modify the ```renderer_cache_contexts``` to alter cache settings. See the related [Drupal.org API](https://www.drupal.org/developing/api/8/cache/contexts).
- Create custom cache tags for rendering caching and add them to ```autoplaceholder_conditions``` variable.

### On packaging, distribution

 - When creating Drupal Features it is better to add dependencies of D.O. modules and not of custom modules that belong to the profile.
 Except if the required feature has necessary settings. This way each feature could be more "independent".

### Other

- Every functionality that is strongly related with the development [parameters](/parameters) should be implemented as **entityreference** (eg the language of a block).
- Dump database should be exported from live site (master) every n hours.
- Create a list of things for the customer to check on every release.
