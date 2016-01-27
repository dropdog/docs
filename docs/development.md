## Developer notes and best practices
---------------------------------------
Please read all the file and not individual sections. It was written like this for purpose.

A lot of ideas for this page have been taken from the [KIT Feature Specification](http://cgit.drupalcode.org/kit/tree/kitf.txt?id=refs/heads;id2=master).

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

- On the issue you must include
  - steps to reproduce the issue
  - files that are related
  - the webpage(s) that shows the issue
  - the related commit or pull request
  - the team member or group to get notified
  - a screenshot (if needed)
  - the version of the software (eg Drupal core) you are using
  - the error logs if any (Drupal's database_log or system_log)

- Every issue must be as much as possible self hosted on Github. Images, assets, code etc should better live on the Github to avoid missing things etc later.
- Add the related tags (**labels** and **milestones**)! If there is no a tag you are looking for ask to the Admin to create one.
- Closing and reopening issues is not something to avoid. Open any issue if you have to do more job, if you need declaration, if you want to keep it on front etc.
- We are going to refer to issues on the git commits using the #number of the issue.
- Mention other people using ```@mention```. If you want to cc them use ```/cc @user1 @user2``` etc.
- View all your GH issues at [github.com/issues](https://github.com/issues).
- View your [Assigned](https://github.com/issues/assigned) issues.
- View your [Mentioned](https://github.com/issues/mentioned) issues.

### VCS - Using git-flow and related tools
We are using the default **[git-flow](http://nvie.com/posts/a-successful-git-branching-model/) methodology** and its conventions.

See the [git-flow cheatsheet](http://danielkummer.github.io/git-flow-cheatsheet/) for fast learning.

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

### VCS- Git commit best practices
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
Are there side effects or other unintuitive consequenses of this
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
- Only commit when a block of work is complete.
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

A worfklow to add only specific files on a commit:

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

### Applying patches

See also [D.O. - Applying patches](https://www.drupal.org/patch/apply).

- Get into the folder that will apply the patch
- Download the patch fro D.O.
- Apply the patch ```patch -p1 < [patch_file]```
- Check if patch works (running tests and/or with the UI)
- If patch works include it with the commit!

### Installing the distribution
- Using **drush** only (make, site-install, db sync, file dl etc)
- Using git only (we need a full site repo though)
- Using UI software (is that needed?)

### Update the distribution
- Normal method (remove old files, keep backup etc).
- Avoid using composer, just get new code with drush or git.

### Create a (D.O) Release

See also [Developing installation profiles and distributions](https://www.drupal.org/developing/distributions).

Steps to create a new release:

- Prepare files for the new release
- Generate [make](http://drushcommands.com/drush-8x/make/) file if not exist using ```drush make-generate``````
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
- Download the module ```drush dl [module]``` (it will be under /modules/[module])

- Test it works (ui)
- Test it can be uninstalled (ui or drush)
- If all tests pass leave it on folder
- If it is a requirement for a DFeature add it on the DFeature
- Move the module on the [profile] folder (it will be under /profiles/[profile] and it will be tracked from VCS)
- rebuild registry (```drush cr```)

- If tests do not pass DO NOT USE it and try to solve the errors (patches, D.O. issues etc)
- If tests do not pass add an issue on GH

***Example: TBD (screencast)***

### Development flow

| data ↓ | develop (dev) | release (stage) | master (live) |
| --- | --- | --- | --- |
| code |- | - | - |
| database |- | - | - |
| drupal config |- | - | - |
| user files |- | - | - |
| system config |- | - | - |
| drush etc aliases |- | - | - |


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
