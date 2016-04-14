## Learning tasks for Developers
-----------------------------------

### Useful 8.x cheatsheets

 - [Drupal 8 entity API](http://wizzlern.nl/sites/wizzlern.nl/files/artikel/drupal-content-entity-8.0.pdf)
 - [Drupal 7 to 8](http://nuvole.org/sites/default/files/Drupal-7-to-Drupal-8-Cheatsheet.pdf)
 - [Drupal 8 Configuration schema](http://hojtsy.hu/files/ConfigSchemaCheatSheet1.5.pdf)

### Drupal books

Suggested Drupal 8.x books for advanced developers.

 - [Drupal 8 Development Cookbook](https://www.packtpub.com/web-development/drupal-8-development-cookbook)
 - [Drupal 8 Module Development](https://www.packtpub.com/web-development/drupal-8-module-development)
 - [Programmer's Guide to Drupal, 2nd Edition](http://shop.oreilly.com/product/0636920034612.do)
 - [High Performance Drupal](http://shop.oreilly.com/product/0636920012269.do)

 - [Drupal Watchdog magazine](https://drupalwatchdog.com/)

### Using Composer
Drupal 8.x supports (and promotes) usage of [Composer](https://getcomposer.org/).
Core and contrib projects may require external libraries that can be attached to
the Drupal app using composer.

Composer uses a specific file named [composer.json](http://cgit.drupalcode.org/drupal/tree/composer.json)
that keeps the configuration in one place as also as [composer.lock](http://cgit.drupalcode.org/drupal/tree/composer.lock)
that locks the dependencies of a project to a known state (specific versions).

Composer can install libraries from [Packagist - The PHP Package Repository](https://packagist.org/)
as also as any other package hub that supports composer.

  - Learn more about composer commands [online](https://github.com/composer/composer/blob/master/doc/03-cli.md) or by running:

```
// Show available composer commands
composer list
```

 - Common composer commands for a PHP project are:

```
// Creates a basic composer.json file in current directory.
composer init

// Installs the project dependencies from the composer.lock file if present,
// or falls back on the composer.json.
composer install

// Adds required packages to your composer.json and installs them.
composer require

// Updates your dependencies to the latest version according to composer.json,
and updates the composer.lock file.
composer update

// Removes a package from the require or require-dev.
composer remove

// Dumps the autoloader
composer dump-autoload

// Create new project from a package into given directory.
composer create-project
```

  - Example of adding requirements of the [address](https://www.drupal.org/project/address) module:

```
// Go to the Drupal root
cd <APP_ROOT>

// Add the requirements abd update composer.json
composer require commerceguys/intl
composer require commerceguys/addressing
composer require commerceguys/zone

```

  - Example of a Drupal build made by composer:

```
// Set the source of Drupal packages
composer config repositories.drupal composer https://packagist.drupal-composer.org

// Download drupalcommerce/project-base
composer create-project drupalcommerce/project-base <PROJECT_FOLDER> --stability dev
```

### Building with Features

### Create a multilingual website
Create a multilingual installation with Dummy content and inspect the database.

Use this distro: [drupal.org/project/multilingual_demo](https://www.drupal.org/project/multilingual_demo)

### Play with git and VCS

#### Git essentials and how git works:

 - [Video: Essentials of Git: A Journey into the Sixth Dimension](https://www.youtube.com/watch?v=eVgQEL7x4Q4)
 - [Video: Introduction to Git with Scott Chacon of GitHub](https://www.youtube.com/watch?v=ZDR433b0HJY)

#### Useful git cheatsheets:

 - [Official git reference](https://git-scm.com/docs)
 - [training.github.com, github-git-cheat-sheet](https://training.github.com/kit/downloads/github-git-cheat-sheet.pdf)
 - [git-tower, git-cheat-sheet](https://www.git-tower.com/blog/git-cheat-sheet/)
 - [Advanced git cheat-sheet](http://www.cheat-sheets.org/saved-copy/git-cheat-sheet.pdf)

#### Interactive tools to learn git commands and terminology:

 - [Visual git cheat-sheet](http://ndpsoftware.com/git-cheatsheet.html)
 - [Learn git in 15 minutes](https://try.github.io)
 - [Learn git branching](http://pcottle.github.io/learnGitBranching/)
 - [Git How To_ Guided Git Tutorial, step by step](https://githowto.com/)

#### CLI tools (shortcuts) you can (should) use:

 - [git-flow](https://github.com/nvie/gitflow). A method as also as a collection of commands for successful git branching and development.
 - (Optional) [git hub](https://hub.github.com/). A tool to help create pull requests, compare commits, view issues and make your life on GH better.
 - (Optional) [git extras](https://github.com/tj/git-extras). Some useful git aliases/wrappers for humans (summary, undo, ignore, changelog etc).

#### GUI Clients you can use.

Git GUI clients are mostly used to see visual graphs of the commits, to solve conflicts, to browse repos etc.

 - [git-scm.com/downloads/guis](https://git-scm.com/downloads/guis)
 - [tig, Text-mode interface for git](https://github.com/jonas/tig)

#### Rewriting git history

Many times, when working with Git, you may want to **revise your commit history** for some reason.

This can involve changing the order of the commits, changing messages or modifying files in a commit, squashing together or splitting apart commits, or removing commits entirely – all before you share your work with others.

Rewriting git history may cause unpredictable issues and really big headaches so here are some useful manuals you should read before going on as also as a decision diagram that helps you decide what to do.

 - [Git Tools - Rewriting History](http://git-scm.com/book/en/v2/Git-Tools-Rewriting-History)
 - [Git: Revert a Commit Already Pushed to a Remote Repository](http://christoph.ruegg.name/blog/git-howto-revert-a-commit-already-pushed-to-a-remote-reposit.html)

![How to handle a git mess](http://justinhileman.info/article/git-pretty/git-pretty.png 'How to handle a git mess')
[Download as pdf](http://justinhileman.info/article/git-pretty/git-pretty.pdf)

#### Configure git

See the [online docs](https://git-scm.com/book/en/v2/Customizing-Git-Git-Configuration). Here are some basic information.

To configure git globally run ```git config --global --edit``` 

 - Enable [rerere](https://git-scm.com/blog/2010/03/08/rerere.html)
 - Do not let git to auto-convert CRLF line endings into LF (`autocrlf`)
 - Do not track filemode
 - Use the `git push` with `simple` option

Example of a global `.gitconfig` file (part of):

```ini
[core]
  autocrlf = false
  safecrlf = false
  ignorecase = false
  editor = /usr/bin/subl -n -w
	filemode = false

[push]
  default = simple

[branch]
  autosetuprebase = always

[diff]
  renames = copies

[color]
  ui = true

[rerere]
  enabled = true
  autoupdate = true

[merge]
  tool = <YOUR_GIT_DIFF_GUI>
```


### Git-flow commands scriptplay

### Setup a development environment

### Debug Drupal

**Drush**

 - You can always **simulate a drush command** without executing by adding the `--simulate` argument at the end.
 - You can debug a drush command using the `--verbose` and `--debug` arguments.

 - [drush core-status](http://drushcommands.com/drush-8x/core/core-status/ 'Provides a birds-eye view of the current Drupal installation, if any.'). Example: ```drush st --full```
 - [drush core-cli](http://drushcommands.com/drush-8x/core/core-cli/ 'Open an interactive shell on a Drupal site.'). Example: ```drush php```
 - [drush sql-cli](http://drushcommands.com/drush-8x/sql/sql-cli/ 'Open a SQL command-line interface using Drupal's credentials.'). Example: ```drush sqlc```
 - [drush watchdog-show](http://drushcommands.com/drush-8x/watchdog/watchdog-show/ 'Show watchdog messages.'). Example: ```drush ws --tail --extended```
 - [drush pm-projectinfo](http://drushcommands.com/drush-8x/pm/pm-projectinfo/ 'Show a report of available projects and their extensions.'). Example: ```drush pmpi --format=table```
 - [drush pm-list](http://drushcommands.com/drush-8x/pm/pm-list/, 'Show a list of available extensions (modules and themes).'). Example: ```drush pml --type=module --format=table --no-core --status=enabled```
 - [drush pm-releases](http://drushcommands.com/drush-8x/pm/pm-releases/ 'Print release information for given projects.'). Example: ```drush rl --format=table drupal```
 - [drush config-list](http://drushcommands.com/drush-8x/config/config-list/ 'List config names by prefix.'). Example: ```drush cli system --format=list | grep article```
 - [drush config-get](http://drushcommands.com/drush-8x/config/config-get/ 'Display a config value, or a whole configuration object.'). Example: ```drush cget system.site --format=yaml```
 - [drush field-info](http://drushcommands.com/drush-8x/field/field-info/ 'View information about fields, field_types, and widgets.') (Not ready at the moment. Please check this [issue](https://github.com/drush-ops/drush/issues/230))
 - [drush features-status](http://drushcommands.com/drush-8x/features/features-status/ 'Display current Features settings.')
 - [drush php-eval](http://drushcommands.com/drush-8x/core/php-eval/ 'Evaluate arbitrary php code after bootstrapping Drupal (if available).'). Example: ```drush ev 'node_access_rebuild()'```
 - [drush entity-updates](http://drushcommands.com/drush-8x/core/entity-updates/ 'Apply pending entity schema updates.'). Example: ```drush entup```

**Drupal Console** ([Drupal Console](https://drupalconsole.com/))

 - [drupal site:mode dev](https://hechoendrupal.gitbooks.io/drupal-console/content/en/commands/site-mode.html 'Switch system performance configuration, dev|prod')
 - [drupal config:debug](https://hechoendrupal.gitbooks.io/drupal-console/content/en/commands/config-debug.html 'Show the current configuration.')
 - [drupal container:debug](https://hechoendrupal.gitbooks.io/drupal-console/content/en/commands/container-debug.html 'Displays current services for an application.')
 - [drupal cron:debug](https://hechoendrupal.gitbooks.io/drupal-console/content/en/commands/cron-debug.html 'List of modules implementing a cron')
 - [drupal database:log:debug](https://hechoendrupal.gitbooks.io/drupal-console/content/en/commands/database-log-debug.html ' Display current log events for the application.')
 - [drupal database:table:debug](https://hechoendrupal.gitbooks.io/drupal-console/content/en/commands/database-table-debug.html 'Show all tables in a given database.')
 - [drupal module:debug](https://hechoendrupal.gitbooks.io/drupal-console/content/en/commands/module-debug.html 'Display current modules available for application.')
 - [drupal rest:debug](https://hechoendrupal.gitbooks.io/drupal-console/content/en/commands/rest-debug.html 'Display current rest resource for the application.')
 - [drupal router:debug](https://hechoendrupal.gitbooks.io/drupal-console/content/en/commands/router-debug.html 'Displays current routes for the application.')
 - [drupal settings:debug](https://hechoendrupal.gitbooks.io/drupal-console/content/en/commands/settings-debug.html 'List user Drupal Console settings.')
 - [drupal site:debug](https://hechoendrupal.gitbooks.io/drupal-console/content/en/commands/site-debug.html 'List all known local and remote sites.')
 - [drupal state:debug](https://hechoendrupal.gitbooks.io/drupal-console/content/en/commands/state-debug.html 'Show the current State keys.')
 - [drupal test:debug](https://hechoendrupal.gitbooks.io/drupal-console/content/en/commands/test-debug.html 'List Test Units available for the application.')
 - [drupal theme:debug](https://hechoendrupal.gitbooks.io/drupal-console/content/en/commands/theme-debug.html 'Displays current themes for the application.')
 - [drupal update:debug](https://hechoendrupal.gitbooks.io/drupal-console/content/en/commands/update-debug.html 'Display current updates available for the application.')
 - [drupal user:debug](https://hechoendrupal.gitbooks.io/drupal-console/content/en/commands/user-debug.html 'Displays current users for the application.')
 - [drupal views:debug](https://hechoendrupal.gitbooks.io/drupal-console/content/en/commands/views-debug.html 'Display current views resources for the application.')

**Drupal modules**

 - [devel](https://www.drupal.org/project/devel) (devel, webprofiler). See the docs for the [WebProfiler](https://github.com/lussoluca/webprofiler).

**PHP debug and testing**

 - [blackfire.io](https://blackfire.io/). See [24 Days of Blackfire](https://blackfire.io/docs/24-days/index).

**Database debug**

 - [MySQL Workbench](https://www.mysql.com/products/workbench/)

**Code review (for Drupal)**

 - [coder](https://www.drupal.org/project/coder) (see the [installation instructions](http://cgit.drupalcode.org/coder/tree/README.md))
 - [PHP_CodeSniffer (phpcs)](http://www.squizlabs.com/php-codesniffer)
 - [PHP Code Beautifier and Fixer](https://github.com/squizlabs/PHP_CodeSniffer/wiki/Fixing-Errors-Automatically#using-the-php-code-beautifier-and-fixer)

### Drupal IDE

**[phpstorm](https://confluence.jetbrains.com/display/PhpStorm/PhpStorm+Early+Access+Program)**

 - [Drupal Development using PhpStorm](https://confluence.jetbrains.com/display/PhpStorm/Drupal+Development+using+PhpStorm)
 - [Phpstorm - Preparing for Drupal Development in PhpStorm](https://www.jetbrains.com/phpstorm/help/preparing-for-drupal-development-in-phpstorm.html)
 - [Phpstorm - Drupal-Specific Coding Assistance](https://www.jetbrains.com/phpstorm/help/drupal-specific-coding-assistance.html)
 - [Setting up PhpStorm for Drupal's Coding Standards](https://www.drupal.org/node/1962108)

### Drupal 8.x configuration system

Here are some facts about the new [Drupal 8.x core configuration ("config.") system](https://www.drupal.org/documentation/administer/config).

 - Config. is made to work for deployment not for packaging.
 - All modules, themes and distributions (Drupal projects) have the same type of configuration (under <project_name>/config/* folder).
 - ```<project_name>/config/install``` has the required config. ```<project_name>/config/optional``` has the optional config. (may not be installed).
 - Configuration files are of **yml** type.
 - A config. file name should be unique.
 - Config. is a group of key-value data.
 - Configuration is decoupled from modules after installation. After installation the Drupal system "owns" the configuration.
 - There are 2 types of config. storage: **Active (currently used from the website) and Staging**.
 - We can have multiple config. stores (not only 2).
 - Active storage is stored on the database by default.
 - Active storage on the database is using UUIDs for each configuration setting.
 - The tables that are created on the database are ```cache_config, config```.
 - By default Drupal creates the Staging folder inside the public files folder.
 - We can override the paths for the config. storage (usually on ```settings.php```).
 - All config. is tracked by default.
 - Diff. is availble to inspect the changes.
 - Config. is saved per content entity.
 - Config. can be individually imported/exported.
 - Config. synchronization requires all files to be present (missing config. files or settings will delete the configuration!)
 - Core config. system is working for the same only Drupal installation.
 - Exported config. files with UUID cannot be reused on another installation.
 - Always use the Config. API to export/import config. Do not edit files or database entries manually.
 - We can "override" a config. setting on the fly in the settings.php file.
 - We can see an overview (Report) of the config. changes at [example.com/admin/config/development/configuration/report](http://example.com/admin/config/development/configuration/report)
 - Useful modules that can export, import or manage config. are [features](https://www.drupal.org/project/features), [config_update](https://www.drupal.org/project/config_update), [config_devel](https://www.drupal.org/project/config_devel), [config_sync](https://www.drupal.org/project/config_sync), [config_tools](https://www.drupal.org/project/config_tools), [config_share](https://www.drupal.org/project/config_share).

### Drush and Drupal console commands for configuration management

  - [config](https://www.drupal.org/project/drupal) (core)

| Tool | Command | Alias | Description |
|------|---------|-------|-------------|
|drush| config-edit | cedit | Open a config file in a text editor. Edits are imported into active configuration after closing editor.|
|drush| config-export | cex | Export configuration to a directory.|
|drush| config-get | cget | Display a config value, or a whole configuration object.|
|drush| config-import | cim | Import config from a config directory.|
|drush| config-list | cli | List config names by prefix.|
|drush| config-pull | cpull | Export and transfer config from one environment to another.|
|drush| config-set | cset | Set config value directly.|
|drush| config-merge | cm | Merge configuration data from two sites. See [docs](http://drushcommands.com/drush-7x/config/config-merge/) |

  - [config_update](https://www.drupal.org/project/config_update) (see [config_update_ui drush inc](http://cgit.drupalcode.org/config_update/tree/config_update_ui/config_update_ui.drush.inc))

| Tool | Command | Alias | Description |
|------|---------|-------|-------------|
|drush|config-added-report | cra | Display a list of config items that did not come from your installed modules, themes, or install profile |
|drush|config-diff |cfd | Display line-by-line differences for one config item between your active config and the version currently being provided by an installed module, theme, or install profile |
|drush|config-different-report|crd|Display a list of config items that differ from the versions imported from your installed modules, themes, or install profile. See config-diff to show what the differences are|
|drush|config-inactive-report|cri|Display a list of optional config items from your installed modules, themes, or install profile that are not currently in your active config|
|drush|config-list-types|clt|List config types|
|drush|config-missing-report|crm|Display a list of config items from your installed modules, themes, or install profile that are not currently in your active config. |

  - [config_devel](https://www.drupal.org/project/config_devel)

| Tool | Command | Alias | Description |
|------|---------|-------|-------------|
| drush | config-devel-export | cde, cd-em | Write back configuration to module's config/install directory. List which configuration settings you want to export in the module's info file by listing them under 'config_devel'|
|drush | config-devel-import| cdi, cd-im | Write back configuration to module's config/install directory. List which configuration settings you want to export in the module's info file by listing them under 'config_devel'|
|drush|config-devel-import-one | cdi1, cd-i1 | Write back configuration to module's config/install directory. List which configuration settings you want to export in the module's info file by listing them under 'config_devel'|

 - [config_sync](https://www.drupal.org/project/config_sync)
 TBD, see [Add Drush support to Configuration Synchronizer](https://www.drupal.org/node/2445463)

### Create an issue on Github

### Create a pull request

### Get familiar with the new API (+API docs)

### Useful browser extensions and plugins

### Run tests

### OOP - how to
 See [Drupal 8 - Background & Prerequisites](https://www.drupal.org/getting-started-d8-bkg-prereq)

 Also [oop_examples](https://www.drupal.org/project/oop_examples)

 - Definitions (Namespaces, Dependency Injection, Annotations, Plugin, Factory, Interface etc)
 - Best practices
 - Examples
 - IDE in the rescue

### Docker
[Docker](https://www.docker.com/) allows you to package an application with all of its
dependencies into a standardized unit for software development.

Docker resources can be found at [Awesome-docker, A curated list of Docker resources and projects](https://veggiemonk.github.io/awesome-docker/).

You can use Docker with many ways while developing. Some common scenario usages are:

 - Test git branches and/or functionality (using the UI or the Drupal testing system)
 - Take backups of the system (eg get the database of the build)
 - Automate Continuous Integration (CI)
 - Automate Continuous Delivery (CD)
 - Reproduce issues and errors and share them with the team
 - Test Drupal core or contrib modules updates

### Other

(Vagrant, Otto, Jenkins, Continuous Integration ...)
