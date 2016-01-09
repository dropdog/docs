## Developer notes and best practices
---------------------------------------
Please read all the file and not individual sections. It was written like this for purpose.

### How to work
- Assign a task to your own or pick an existing one.
- Deliver new Feature/Functionality *fast*
- Run tests
- Improve/Refract code
- Recreate the Feature/Functionality
- Push the code on the VCS
- Inform other team members about your contribution
- Done!

- Always document what you 've done. On Code, on the Feature, on the Commit, on these Docs!

### Project folders and structure

### Reporting issues

### Using git and VCS patterns

- Branches
- Merging
- Pulling
- Commiting
- Patches

### Installing the distribution

### Update the distribution

### Setting up the (local) development environment

### Writing a test

### Create a pull request

### Saving Backups

### Restoring Backups

### Setting up Permissions and user Roles

- Every custom module should define its own permissions. Never reuse an existing permission!
- If there is separate functionality on a custom module create all the necessary permissions (eg permission to "Access the display" and to "Adnminister the module" etc).
- All the permissions names and descriptions should start with a common used verb such as: "View ...", "Administer ...", "Delete ..." etc.
- A Drupal user with CRUD allowed will usually have more than 1 Roles. Saying that do not try to *bundle* many permissions per Role and better split them accordingly across Roles.

### Building Content types and Fields

- Avoid taxonomy term reference fields! Instead use Entityreference fields with a Content type that will be used as a "taxonomy".
- Labels should not be displayed inline but blocks (```display: block```)
- Fieldsets should be avoided. If not they should be open by default.
- All fields require a Description to inform the user about their need.
- No field should be shared. Never reuse fields!
- Fields machine name should follow this pattern for the machine name: ```field_[content_type_machine_name]_[short_name]```
- Content types, Views and Custom Blocks should follow this pattern for the machine name: ```[machinename]```. That means you should use only letters and no special character or space. Machine names must be short but descriptive. Avoid very generic machine names or names that have been used already on the site even for another type of functionality (Views, Content types, Blocks, Plugins etc).

### Building (Drupal) Views


### Building Custom configuration (admin) pages
- If you group form items use the parent variable name as prefix for all the children items.
```php
// Parent (Group)
$form['parent_group'] = array();
// Child
$form['parent_group']['parent_group_child'] = array();
```
- Always build such pages with Drupal Console generate function to eliminate errors.

### Building and packaging with Features

- One Feature per Content type (CT). Each Content Type Feature (CTF) will package the CT fields, node form, related views, related blocks and user permissions.

### Adding 3rd party libraries

- Before adding an external library/dependency check if it is already available (here is a [list](http://cgit.drupalcode.org/drupal/tree/core/composer.txt) of the necessary 3rd party libraries for Core ). Do not confuse this with the [Core libraries](http://cgit.drupalcode.org/drupal/tree/core/core.libraries.yml) which is used to load the above libraries within Drupal.
- Prefer tiny and specific libraries.
- Check the library popularity on its official repository. Avoid libraries with no traffic at all.
- If multiple release sources (eg packagist, apt-get etc) are available for the library prefer Github which is most of the times the development source.
- Always use a release of a library (if available) and not a generic branch.
