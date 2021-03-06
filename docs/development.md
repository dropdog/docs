## Developer notes and best practices
---------------------------------------

How to develop stuff guides. Please read all the file and not individual sections. It was written like this for purpose.

A lot of ideas for this page have been taken from the [KIT Feature Specification](http://cgit.drupalcode.org/kit/tree/kitf.txt?id=refs/heads;id2=master).

### How to work
 - Assign a task to your own or pick an existing one.
 - Deliver new Feature/Functionality *fast*.
 - Run tests (localy or on the test server).
 - Improve/Refract code.
 - Recreate the Feature/Functionality.
 - Test the new code locally on a clean installation.
 - Push the new code on the VCS (pull request).
 - If tests are green **move the new code** on the appropriate folder inside ```/profiles/[distro-name]```.
 - Update related issue and inform the other team members (if they need to).
 - Done!

 - Always document what you have done. On Code, on the Feature, on the Commit, on these Docs!

> If you add a new module dependency and you don't want to recreate the distribution then follow these steps:

  1. Enable the new project(s) (eg module) on your installation.
  2. Commit and publish the files with the dependencies using git.

### Project folders and structure
 - We are only tracking the ```/profiles/[distro-name]``` folder! Not any other files.
 - The distribution folder will/may have this structure (see at [github.com/dropdog/docs/tree/master/docs/structure/profile](https://github.com/dropdog/docs/tree/master/docs/structure/profile))

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

### Reporting issues (errors etc)
There are many kind of issues. Most of the times here we refer to a bug or support issue. Not to a Task.

Tasks are also issues but with a different label.

 - First search, then submit an issue.
 - Create the issue only on Github.
 - There must be only one unique issue and no duplicates.
 - If an issue refers to an old issue reopen it and don't create a new issue.
 - Every issue must be as much as possible self hosted on Github. Images, assets, code etc should better live on the Github to avoid missing things etc later.
 - Add the related tags (**labels** and **milestones**)! If there is no a tag you are looking for ask to the Admin to create one.
 - Closing and reopening issues is not something to avoid. Open any issue if you have to do more job, if you need declaration, if you want to keep it on front etc.
 - We are going to refer to issues on the git commits using the #number of the issue.
 - Mention other people using ```@mention```. If you want to cc them use ```/cc @user1 @user2``` etc.
 - View all your GH issues at [github.com/issues](https://github.com/issues).
 - View your [Assigned](https://github.com/issues/assigned) issues.
 - View your [Mentioned](https://github.com/issues/mentioned) issues.

On the issue you must include:

  - steps to reproduce the issue
  - files that are related
  - the webpage(s) that shows the issue
  - the related commit or pull request
  - the team member or group to get notified
  - a screenshot (if needed)
  - the version of the software (eg Drupal core) you are using
  - the error logs if any (Drupal's database_log or system_log)

### VCS - Using git-flow and related tools

We are using the default **[git-flow](http://nvie.com/posts/a-successful-git-branching-model/) methodology** and its conventions.

 - See the [git-flow cheatsheet](http://danielkummer.github.io/git-flow-cheatsheet/) for fast learning.
 - See the [command line manual](https://github.com/nvie/gitflow/wiki/Command-Line-Arguments)
 - See the [Comparison of using `git flow` commands VS raw `git` commands](https://gist.github.com/JamesMGreene/cdd0ac49f90c987e45ac)

**git-flow commands - short diagram**

![git-flow commands - short diagram](http://danielkummer.github.io/git-flow-cheatsheet/img/git-flow-commands.png 'git-flow commands - short diagram')


 - The main project branches are ```develop, [releases], master```.
 - There is no staging branch. Staging will be each release tag.
 - Tests from the CI should run on every pull-request.
 - Tests on live servers should run on every [Release].
 - Each release will have this name pattern ```[drupal-version]-profile-release]```. Example **8.0.1-1.0**. Different releases may exist for the same profile version (so only the Drupal version will change).
 - Patches that are submitted from D.O. or other places should be commited with the files on git!
 - Only the Project manager should be able to merge.
 - We are starting development always from **develop** branch except if there is a **hotfix**.
 - When we create a pull-request you have to commit on the same pull-request (using a local branch) and when ready merge it.
 - After each successful release there will be a new **make file** from existing files/configuration.
 - Modules that are used for development (devel, masquarade etc) will be commited to Github but **they will not be imported to the make file** except if they are requirements for any of the modules of the distribution.
 - If you need a publish a branch that should NOT be merged use this naming pattern ```no-merge-[branch_name]```.
 - If you want to see what are the raw git commands running after a git-flow command add the `--showcommands` argument at the end.
 - Avoid pushing online too many similar branches (eg branches of Content types). First find the working formula for a type of branch and then copy this successful methodology to other. Event then there is no need to create a dozen of branches online.

### VCS - Git commit best practices
[Git Commit](https://git-scm.com/docs/git-commit) messages are so important for a good team collaboration as also as for a sustainable development workflow.

Here are the 7 rules of a great git commit message. Taken from [How to Write a Git Commit Message](http://chris.beams.io/posts/git-commit/).

 - Separate subject from body with a blank line.
 - Limit the subject line to 50 characters, Github and many other tools use the title on their UI.
 - Capitalize the subject line.
 - Do not end the subject line with a period!
 - **Use the imperative mood** in the subject line.
 - Wrap the body at 72 characters.
 - Use the body to explain **what and why** vs **how**.

In practice in order to open the editor to write the commit do not use the ```-m``` flag because it prevents from opening the editor. Instead use:

```git commit``` which opens the default editor for git.

To change the default editor (let's say to vim) type:

```git config --global core.editor "/usr/bin/vim -n -w"```

A **masterpiece of a commit** may look like this:

```
Summarize changes in around 50 characters or less

More detailed explanatory text, if necessary. Wrap it to about 72
characters or so. In some contexts, the first line is treated as the
subject of the commit and the rest of the text as the body. The
blank line separating the summary from the body is critical (unless
you omit the body entirely); various tools like `log`, `shortlog`
and `rebase` can get confused if you run the two together.

Explain the problem that this commit is solving. Focus on why you
are making this change as opposed to how (the code explains that).
Are there side effects or other unintuitive consequences of this
change? Here's the place to explain them.

Further paragraphs come after blank lines.

 - Bullet points are okay, too
 - Typically a hyphen or asterisk is used for the bullet, preceded
   by a single space, with blank lines in between, but conventions
   vary here

If you use an issue tracker, put references to them at the bottom,
like this:

Resolves: #123
See also: #456, #789
```

### VCS - Atomic commits

See more at [seesparkbox - Atomic Commits with Git](http://seesparkbox.com/foundry/atomic_commits_with_git), [freshconsulting - Developer Tip: Keep Your Commits “Atomic”](http://www.freshconsulting.com/atomic-commits/).

Avoid committing “at the end of the work day”, or “whenever I feel like it”, or whenever a batch of fixes are complete. This way the VCS is just a backup of your work.

Similar to the definition of "Atomic design" the "Atomic commit" refers to a commit of code that can be reused, ignored, separated etc. On the atomic development approach we make changes through commits as small and “atomic” as possible.

Here are the principles of atomic commits:

 - Focus on one feature/fix etc at a time.
 - Create a separate branch for each task that will finish up as a group of commits. git-flow in the resque.
 - Commit each fix or task as a separate change.
 - Only commit when a block of work is complete. Don't commit half-done work.
 - Commit each layout change separately.
 - Joint commit for layout file, code behind file, and additional resources.

Here are the benefits:

 - Easy to roll back without affecting other changes.
 - Easy to review your code and see each incremental change.
 - Easy to make other changes on the fly (eg using [git cherry-pick](https://git-scm.com/docs/git-cherry-pick)).
 - Easy to merge features to other branches.

Examples of atomic commits:

 - The css for an element/theme_region/page etc.
 - A DFeature
 - A different display style of a webpage (eg a theme skin)
 - A js effect/functionality (eg a js function)
 - A fix for a bug
 - A UI for a Drupal module
 - A new Dblock position on a Dtheme.

In practice in order to open the editor to write the commit do not use the ```-a``` flag because it adds all the modified files to the commit!

A workflow to add only specific files on a commit:

```git
$ git status
    Modified: contact.html
    Modified: contact.php

$ git add contact.html

$ git status
    # Other file is ready to be commited
    Modified: contact.php

$ git commit
# Opens the default git editor so you can create the commit message.

# Add the commit but do not push!

# Continue with another commit.

# When ready push.

```

A worfklow to add specific parts of a file!

```git
$ git status
    Modified: contact.html
    Modified: contact.php

$ git add -p contact.html
# Shows the first changed hunk in the file 'contact.html'
# and then asks you if you want to stage it or not!

$ git commit
# Opens the default git editor so you can create the commit message.

# Add the commit but do not push!

# Continue with another commit.

# When ready push.

```

**Github specific autolinked-references**

See more at [Github docs - Autolinked references and urls](https://help.github.com/articles/autolinked-references-and-urls).

 - If you write `#26` on a commit message Github will look for Issue No 26 or Pull Request No 26 and will create a link to it if exists.
 - You can **refer to commits** using the commit hash (usually the first 7 characters are enough). So if you write on commit message `9889c6e` Github will make a link to that commit.
 - Links that are generated are **bidirectional** (for example, if you refer to a Pull Request from an Issue this reference will also appear on the Pull Request page)

### Applying patches

See also [D.O. - Applying patches](https://www.drupal.org/patch/apply).

 - Get into the folder that will apply the patch
 - Download the patch fro D.O.
 - Apply the patch ```patch -p1 < [patch_file]```
 - Check if patch works (running tests and/or with the UI)
 - If patch works include it with the commit!

 - Revert a patch with ```patch -p1 -R < path/file.patch```
 - Create a patch from a diff: ```git diff <COMMITISH-FROM> <COMMITISH-FROM> > <PATCH_NAME>.suffix``` (example: ```git diff 04a2 b36f > patchfile.patch```)

### Installing the distribution
 - Using **drush** only (make, site-install, db sync, file dl etc. Check ```drush make --help```)
 - Using git only (from the full site repo including Drupal core)
 - Using composer (see [Composer in relation to Drush Make](https://www.drupal.org/node/2471553))

Example of a build using Drush.

```cli
git clone --branch <branch_name>

git@github.com:<org_name>/<repository>.git

cd <repository>

drush make --prepare-install build-<profile_name>.make <my/www/path>

cd <my/www/path>

drush site-install <profile_name> --db-url="mysql://<db_user>:<db_pass>@localhost/<db_name>"
```

### Update the distribution
- Normal method (remove old files, keep backup etc).
- Avoid using composer, just get new code with drush or git.

### Create a (D.O) Release

See also [Developing installation profiles and distributions](https://www.drupal.org/developing/distributions).

Steps to create a new release (for the Profile Administrator):

 - Prepare files for the new release
 - Generate [make](http://drushcommands.com/drush-8x/make/) file if not exist using ```drush make-generate```
 - Update make file if exist using ```drush make-update```
 - Verify the make file using ```drush verify-makefile``` (this step requires the drush plugin [drupalorg_drush](https://www.drupal.org/project/drupalorg_drush))
 - Update CHANGELOG.txt
 - Update [profile].info.yml (you can see the list of modules using ```drush pm-list --type=module --status=enabled --format=list```)
 - Inform related services for the new release (eg CI webhooks)
 - (Optional) Update PATCHES.txt
 - Create a git tag for the release and push the new tag on the repository

### Setting up the (local) development environment

Required software (to install and use Drupal). See also [Drupal installation requirements](https://www.drupal.org/requirements/) on D.O.

 - wget
 - composer
 - drush
 - php 5.6+
 - php built-in server (```$ drush runserver```)
 - apache
 - mysql
 - gd2

Development software (check also at [D.O. Development tools](https://www.drupal.org/node/147789))

 - [docker](https://www.docker.com/)
 - IDE (eg phpstorm, netbeans etc)
 - [php codesniffer](https://github.com/squizlabs/PHP_CodeSniffer)
 - [DrupalConsole](https://drupalconsole.com/) (Drupal development tool)
 - [blackfire.io](https://blackfire.io/) (performance testing tool)

### How to add new modules

 - Download the module ```drush dl [module]```.
 - Test it works (using UI, if has a UI)
 - Test it can be uninstalled (using the UI or drush)
 - If all tests pass leave it on folder
 - If it is a requirement for a DFeature add it on the DFeature
 - Move the module on the [profile] folder (it will be under **/profiles/[profile]** and it will be tracked from VCS)
 - rebuild registry (```drush cr```)
 - If tests do not pass DO NOT USE it and try to solve the errors (patches, D.O. issues etc)
 - If tests do not pass add an issue on GH

### Development flow

| data ↓ | develop (dev) | release (stage) | master (live) |
| ---               | --- | --- | --- |
| code              | from local branches | from dev | from stage (release) |
| database          |from live | from live | - |
| drupal config (1) |from live | from live | - |
| user files        |from live | from live | - |
| system config     | dev | same as live | - |
| drush etc aliases | common | common | none |

(1) Probably config should merge between environments.

### Import/export Drupal site Configuration

This is referred to the new Drupal 8.x Configuration Management (CM) API.
Please check the details of the CM at [learn/#drupal-8x-configuration-system](learn/#drupal-8x-configuration-system).

Form more details about CM workflow see the docs at [Managing configuration in Drupal 8](https://www.drupal.org/documentation/administer/config).

1. [Configuration Management Workflow using Drush](https://www.drupal.org/node/2416591)
2. [Configuration Management Workflow using the Drupal UI](https://www.drupal.org/node/2416545)

### Create a pull request
See above about VCS and git-flow.

### Dealing with Backups

**Database**

 - For development use the [backup_migrate](https://www.drupal.org/project/backup_migrate) or [backup_db](https://www.drupal.org/project/backup_db) module (truncate all caches from the cache_* tables for the default backup profile).
 - Save database regularly backups with a cron job.
 - For the live site will need **in addition** to the backup_migrate backups full database backups using ```mysqldump``` (see [drush sql-dump](http://drushcommands.com/drush-8x/sql/sql-dump/) command).
 - Backups should be saved on another server (different from the Drupal installation).
 - Backups should be tested on specific times (eg once a week) to check they are working normally.
 - Backup pattern is ```[database_name]-[c].sql``` where [c] is the [ISO 8601 date (php 5+)](http://php.net/manual/en/function.date.php). Example: *livedb-2016-01-29T14:04:46+02:00.sql*.
 - For the dump database (without the backup_migrate module) avoid compressing the sql file. If you have to (eg the file is too large) use the [gzip compression](http://www.gzip.org/) only. Example: *livedb-2016-01-29T14:04:46+02:00.sql.gz*
 - We cannot have VCS for database files.

**User generated public and private files**

 - Best option is to keep these files on a separate filestorage out of Drupal.
 - User generated files (eg sites/default/files) should be backup separately from the database.
 - We cannot have VCS for these files.

**Restoring Backups**

 - Always take a **backup of current site** (database dump, database from backup_migrate or backup_db, public/private files) before restoring a backup!
 - Never restore on the live site before testing the backups on a copy of the live site!
 - If a backup causes errors add an issue on GH and explain/ask for help.

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
 - No field should be shared. Never reuse fields except if a field needs to be the same across content types (eg a SKU)!
 - Display view modes should be generic for all Content types and not specific (eg event_full)
 - Machine names of Content types and fields should disallow name conflicts (eg ```nameone``` and ```nameoneplus``` may cause issues)
 - Fields machine name should follow this pattern for the machine name: ```field_[content_type_machine_name]_[short_name]```
 - Content types, Views and Custom Blocks should follow this pattern for the machine name: ```[machinename]```. That means you should use only letters and no special character or space. Machine names must be short but descriptive. Avoid very generic machine names or names that have been used already on the site even for another type of functionality (Views, Content types, Blocks, Plugins etc).
 - Better do NOT use the default (core) Body field but a custom one for each CT. Body field may break our sass patterns and automated tests since it doesn't follow the machine name pattern described above.

According to the above we are supposed to use Entityreference instead of Taxonomy Term reference.
This is the rule except if there are cases that are met.

These cases are:

 - We need a web page (views) to show the referenced items (taxonomy built-in option)
 - We need advanced filtering for views (exposed filters etc)
 - We need tree structure of the references (taxonomy built-in option)
 - We need autocomplete (instant creation) fields when creating references
 - We need a related functionality that works only (or better) with Taxonomy (eg search_api)
 - We don't need revisions, publishing options and other things that are possible only with Content Types.

So, if 2 or more of the above cases are in need then we could discuss to use Taxonomy.

Field description best practices.

 - Write the description for the **end user** of the website not for the developers.
 - First of all describe what is the field about.
 - Write any special (technical) requirements (eg the minimum image dimensions).
 - At the end show real examples of the value(s) that should be used.
 - Let the user know if the field will not be published.
 - Let the user ask for help if she does not understand what is the field about (eg link to a wiki).
 - Keep the description pattern solid across the fields.
 - Don't use ```<p>``` inside a description! Use only ```<br>``` to change lines.
 - Don't write details about things that will be handled from Drupal on submission (eg that a field is required).
 - Link (```href```) to another internal page should be relative, should contain a title and open in a new window.

Example of an image field description.

```
This image will be used on the top of the page and it will have a 100% width.
<br>Best image dimensions is width: 1200px, height: 260px.
Larger or smaller images will be cropped (or stretched accordingly) to these dimensions.
<br>You can see the usage of the image on the <a href="/internal/styleguides#hero-image" title="hero image real example" tagret="_blank">Styleguides</a>.
<br>Get an image with such dimensions <a href="/path/to/1200_260/image" target="_blank" title="1200px*260px image">here</a>.
```

### Building Custom Blocks (using Drupal block_content module)

 - Treat machine_name, fields, view modes etc like any other Content type (see above)
 - On the machine_name do NOT add the `block` prefix (Drupal will add this anyway before the machine_name)
 - Do NOT add the <profile_name> anywhere in the machine_name
 - On the machine_name add a basic, generic name that will describe the block **functionality**. Eg `banner`, `list`, `header` etc
 - On the machine_name do NOT add any region/theme/placement etc related info
 - Make the machine_name following the atomic design patterns (see above)

Examples of a machine_name of a custom Block type: ```largebanner```, ```productlist``` etc.

### Building (Drupal) Views

 - Create one Views per Views Display except if it is a requirement. For example a Block Views and a Page Views for the same Content type should exist on different Views.
 - Always rename the machine name of the Views to remove the numerical suffix (```page_1``` should be ```page```)
 - Do not add custom CSS classes on the whole Views.
 - Always use **Format > Show: Content** for the views row in order to move the row display control on Content types. If there is no available content type view mode create one.
 - Always package (with Features) the Views with the associated Entity type (eg Blog) except if there is a special use case of the Views.
 - It is required to give a meaningful (Administrative) name, description and tags to the Views. Do not leave the default values.
 - Add a tag to be the same as your nickname, Github username etc on each Views you create.
 - (~) Do not add a Menu for the Views through the Views settings page.
 - Always override default system views if they are to be used on the Distro.
 - Do not use Ajax by default for a View.
 - Always provide a simple text for "No results behavior". Example: "No results".
 - Always use **Access: Permission | ...** for the Views access. Do not use Roles.
 - Add useful Administrative comments for each Views.
 - Machine name of each Views must be one word, sort and meaningful. See [more details](#building-content-types-and-fields) about this rule above.
 - Always provide a Title for the Views.
 - If you clone a View be careful to satisfy the above rules.

### Building Custom configuration (admin) pages

 - If you group form items use the parent variable name as prefix for all the children items.
```php
// Parent (Group)
$form['parent_group'] = array();
// Child
$form['parent_group']['parent_group_child'] = array();
```
 - Always build such pages with Drupal Console generate function to eliminate errors.

### Building and packaging with (Drupal) Features

 - One Feature per Entity type (Content, Taxonomy, User etc)
 - Enable "Allow conflicts" (checkbox on the UI).
 - After exporting a DFeature check that all the **configuration files** exist in place.
 - After exporting a DFeature check that there is **no dependency to itself**.
 - Use the current installation <Profile_machine_name> as Bundle name. Do not add DFeatures with the Default Features Bundle.
 - Each Content Type Feature (CTF) will package the CT fields, node form, related views, related blocks and user permissions.
 - Better add the "[profile_machine_name]" before each Feature name to avoid misconceptions with other modules and make it easier to search for a Feature.


### Adding 3rd party libraries

 - Before adding an external library/dependency check if it is already available (here is a [list](http://cgit.drupalcode.org/drupal/tree/core/composer.txt) of the necessary 3rd party libraries for Core ). Do not confuse this with the [Core libraries](http://cgit.drupalcode.org/drupal/tree/core/core.libraries.yml) which is used to load the above libraries within Drupal.
 - Prefer tiny and specific libraries.
 - Check the library popularity on its official repository. Avoid libraries with no traffic at all.
 - If multiple release sources (eg packagist, apt-get etc) are available for the library prefer Github which is most of the times the development source.
 - Always use a release of a library (if available) and not a generic branch.
 - If a library needs to be loaded with composer add it without the helper module [composer_manager](https://www.drupal.org/project/composer_manager) but with core composer.

### Using Docker

#### Docker images

We use Docker to create private or public images. Images can be of several types such as:

 - A generic public LAMP image ready to install any Drupal 8.x website (see [image dropdog/docker](https://hub.docker.com/r/dropdog/docker/))
 - A specific private image that installs Drupal 8.x with the current profile (using image `dropdog/docker`)
 - A specific private image to run tests (using the above image as base)

#### How to use Docker for development

See the related chapter at [learn#docker](learn#docker) file.

### Examples of using Docker

```
// Create a new development folder.
mkdir /var/www/html/[NEW_FOLDER]

// Clone Drupal installation files.
git clone [GIT_REPOSITORY] --branch [GIT_BRANCH] /var/www/html/[NEW_FOLDER]

// Login to Docker hub (hub.docker.com), may need sudo.
docker login (may need sudo)

// Pull private Docker image, may need sudo
docker pull [PRIVATE_DOCKER_IMAGE_REPO]:[tag]

// Run of a new Docker container with volumes
// The web ui can be found at http://localhost:8090
docker run -d -p 8090:80 -p 8022:22 -v /var/www/html/[NEW_FOLDER]/profiles:/var/www/profiles -t [PRIVATE_DOCKER_IMAGE_REPO]:[tag]
...

```

### Text formats and WYSIWYG editor

The text formats that will be available are:

 1. plain_text
 2. html

- Both 1 and 2 will be available for non-admin authenticated users (Authors, Managers etc).
- Administrators should NOT use any extra format (full_html etc) that will not be available for Authors since all the Content must be editable by the portal Managers/Authors etc.
- All users should NOT have the option to change between plain_text and html.
- If we need extra html goodies (eg more allowed html tags) to be added on the **html** format then all the users with access to this format will need that too.
- Insecure piece of content (eg php) should be added programmatically from code and not on the editor.
- The WYSIWYG editor buttons should be the same as the HTML filters. Nothing more, nothing less.
