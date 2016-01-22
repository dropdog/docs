## Developer notes and best practices
---------------------------------------
Please read all the file and not individual sections. It was written like this for purpose.

### How to work
- Assign a task to your own or pick an existing one.
- Deliver new Feature/Functionality *fast*
- Run tests (localy or on the test server)
- Improve/Refract code
- Recreate the Feature/Functionality
- Push the code on the VCS (pull request)
- If tests are green **move the new code** on the appropriate folder inside ```/profiles/[distro-name]```
- Update related issue and inform the other team members (if they need to).
- Done!

- Always document what you have done. On Code, on the Feature, on the Commit, on these Docs!

### Project folders and structure
- We are only tracking the ```/profiles/[distro-name]``` folder! Not any other files.
- The distribution folder will/may have this structure (see at [github.com/dropdog/play/tree/develop](https://github.com/dropdog/play/tree/develop))
```
├── config/
│   ├── install/
│   │   └── README.txt
│   └── optional/
│       └── README.txt
├── libraries/
│   └── README.txt
├── modules/
│   ├── contrib/
│   │   └── README.txt
│   └── dropdog/
│       └── README.txt
├── src/
│   └── Tests/
│       └── DropdogTest.php
├── themes/
│   └── dropdogy/
│       └── README.txt
├── build-dropdog.make
├── CHANGELOG.txt
├── continuous-integration.yml
├── dropdog.info.yml
├── dropdog.install
├── dropdog.profile
├── drupal-org-core.make
├── drupal-org.make
├── patches.txt
├── README.txt
├── rebuild.sh
├── release.sh
└── server-setup.sh

```


### Reporting issues (error etc)
There are many kind of issues. Most of the times here we refer to a bug or support issue. Not to a Task.

- First search, then submit an issue.
- Create the issue only on Github.
- There must be only one unique issue and no duplicates.
- On the issue you must include
  - steps to reproduce the issue
  - files that are related
  - the webpage(s) that shows the issue
  - the related commit or pull request
  - the team member or group to get notified
  - a screenshot (if needed)
  - the version of the software (eg Drupal core) you are using
- Every issue must be as much as possible self hosted on Github. Images, assets, code etc should better live on the Github to avoid missing things etc later.
- Add the related tags (**labels** and **milestones**)! If there is no a tag you are looking for ask to the Admin to create one.
- Closing and reopening issues is not something to avoid. Open any issue if you have to do more job, if you need declaration, if you want to keep it on front etc.
- We are going to refer to issues on the git commits using the #number of the issue.
- Mention other people using ```@mention```. If you want to cc them use ```/cc @user1 @user2``` etc.
- View all your GH issues at [github.com/issues](https://github.com/issues).
- View your [Assigned](https://github.com/issues/assigned) issues.
- View your [Mentioned](https://github.com/issues/mentioned) issues.

### Using git and VCS patterns
- We are using the [git-flow](http://nvie.com/posts/a-successful-git-branching-model/) methodology and its conventions.
- There is no staging branch. Staging will be each release tag.
- Tests from the CI should run on every pull-request.
- Tests on live servers should run on every Release.
- Each release will have this pattern ```[drupal-version]-profile-release]```. Example **8.0.1-1.0**. Different releases may exist for the same profile version (Drupal version will change).
- Patches that are submitted from D.O. or other places should be commited with the files on git!
- Only the Project manager should be able to merge.
- We are starting development always from **develop** branch except if there is a **hotfix**.
- When we create a pull-request it is better to commit on the same pull-request (using a local branch) and when ready merge it.
- After each successful release there will be a new **make file** from existing files/configuration.

### Installing the distribution
- Using **drush** only (make, site-install, db sync, file dl etc)
- Using git only (we need a full site repo though)
- Using UI software (is that needed?)


### Update the distribution
- Normal method (remove old files, keep backup etc).
- Avoid using composer, just get new code with drush or git.

### Setting up the (local) development environment
- wget
- composer
- drush
- php built-in server (```$ drush runserver```)
- apache
- mysql
- gd2

### Writing a test
TBD

### Create a pull request
See above about VCS and git-flow.

### Saving Backups
TBD

### Restoring Backups
TBD

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
- Always use **Format > Show: Content** for the views row in order to move the row display control on Content types. If there is no available content type view mode create one.
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
