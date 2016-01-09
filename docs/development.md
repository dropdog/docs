## Developer notes and best practices
---------------------------------------
Please read all the file and not individual sections. It was written like this for purpose.

### How to work
- Assign a task to your own or pick an existing one.
- Deliver new Feature/Functionality *fast*
- Run tests
- Improve/Refract code
- Recreate the Feature/Functionality
- Push the code on the VCS (pull request)
- Inform other team members, update related issue.
- Done!

- Always document what you 've done. On Code, on the Feature, on the Commit, on these Docs!

### Project folders and structure

### Reporting issues

### Using git and VCS patterns

- Branches
- Merging
- Pulling
- Committing
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
- If there is separate functionality on a custom module create all the necessary permissions (eg permission to "Access the display" and to "Administer the module" etc).
- All the permissions names and descriptions should start with a common used verb such as: "View ...", "Administer ...", "Delete ..." etc.
- A Drupal user with CRUD allowed will usually have more than 1 Roles. Saying that do not try to *package* many permissions per Role and better split them accordingly across Roles.

### Building Content types and Fields

- Avoid taxonomy term reference fields! Instead use Entityreference fields with a Content type that will be used as a "taxonomy".
- Labels should not be displayed inline but blocks (```display: block```)
- Fieldsets should be avoided. If not they should be open by default.
- All fields require a Description to inform the user about their need.
- No field should be shared. Never reuse fields!
- Display view modes should be generic for all Content types and not specific (eg event_full).
- Fields machine name should follow this pattern for the machine name: ```field_[content_type_machine_name]_[short_name]```
- Content types, Views and Custom Blocks should follow this pattern for the machine name: ```[machinename]```. That means you should use only letters and no special character or space. Machine names must be short but descriptive. Avoid very generic machine names or names that have been used already on the site even for another type of functionality (Views, Content types, Blocks, Plugins etc).

### Building (Drupal) Views
- Create one Views per Views Display except if it is a requirement. For example a Block Views and a Page Views for the same Content type should exist on different Views.
- Always rename the machine name of the Views to remove the numerical suffix (```page_1``` should be ```page```)
- Do not add custom CSS classes on the whole Views.
- Always use **Format> Show: Content** for the views row in order to move the row display control on Content types. If there is no available content type view mode create one.
- Always package (with Features) the Views with the associated Entity type (eg Blog) except if there is a special use case of the Views.
- It is required to give a meaningful (Administrative) name, description and tags to the Views. Do not leave the default values.
- Add a tag to me same as your nickname, Github username etc on each Views you create.
- (~) Do not add a Menu for the Views through the Views settings page.
- Always override default system views if they are to be used on the Distro.
- Do not use Ajax by default for a Views.
- Always provide a simple text for "No results behavior". Example: "No results".
- Always use **Access: Permission | ...** for the Views access. Do not use Roles.
- Add useful Administrative comments for each Views.
- Machine name of each Views must be one word, sort and meaningful. See [more details](#building-content-types-and-fields) about this rule above.
- Always provide a Title for the Views.
- If you clone a Views be careful to satisfy the above rules.

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
