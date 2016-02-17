## Learning tasks for Developers
-----------------------------------

### Useful 8.x cheatsheets

 - [Drupal 8 entity API](http://wizzlern.nl/sites/wizzlern.nl/files/artikel/drupal-content-entity-8.0.pdf)
 - [Drupal 7 to 8](http://nuvole.org/sites/default/files/Drupal-7-to-Drupal-8-Cheatsheet.pdf)
 - [Drupal 8 Configuration schema](http://hojtsy.hu/files/ConfigSchemaCheatSheet1.5.pdf)

### Using Composer

### Using Drupal Console

### Building with Features

### Create a multilingual website
Create a multilingual installation with Dummy content and inspect the database.

Use this distro: [drupal.org/project/multilingual_demo](https://www.drupal.org/project/multilingual_demo)

### Play with git and VCS

Git essentials and how git works:

 - [Video: Essentials of Git: A Journey into the Sixth Dimension](https://www.youtube.com/watch?v=eVgQEL7x4Q4)
 - [Video: Introduction to Git with Scott Chacon of GitHub](https://www.youtube.com/watch?v=ZDR433b0HJY)

Useful git cheatsheets:

 - [Official git reference](https://git-scm.com/docs)
 - [training.github.com, github-git-cheat-sheet](https://training.github.com/kit/downloads/github-git-cheat-sheet.pdf)
 - [git-tower, git-cheat-sheet](https://www.git-tower.com/blog/git-cheat-sheet/)
 - [Advanced git cheat-sheet](http://www.cheat-sheets.org/saved-copy/git-cheat-sheet.pdf)

Interactive tools to learn git commands and terminology:

 - [Visual git cheat-sheet](http://ndpsoftware.com/git-cheatsheet.html)
 - [Learn git in 15 minutes](https://try.github.io)
 - [Learn git branching](http://pcottle.github.io/learnGitBranching/)
 - [Git How To_ Guided Git Tutorial, step by step](https://githowto.com/)

CLI tools (shortcuts) you can (should) use:

 - [git-flow](https://github.com/nvie/gitflow). A method as also as a collection of commands for successful git branching and development.
 - (Optional) [git hub](https://hub.github.com/). A tool to help create pull requests, compare commits, view issues and make your life on GH better.
 - (Optional) [git extras](https://github.com/tj/git-extras). Some useful git aliases/wrappers for humans (summary, undo, ignore, changelog etc)!

GUI Clients you can use. They are mostly used to see visual graphs of the commits, to solve conflicts, to browse repos etc.
 - [git-scm.com/downloads/guis](https://git-scm.com/downloads/guis)
 - [tig, Text-mode interface for git](https://github.com/jonas/tig)

### Setup a development environment

### Debug Drupal

**Drush**

 - [drush core-status](http://drushcommands.com/drush-8x/core/core-status/). Example: ```drush st --full```
 - [drush core-cli](http://drushcommands.com/drush-8x/core/core-cli/). Example: ```drush php```
 - [drush sql-cli](http://drushcommands.com/drush-8x/sql/sql-cli/). Example: ```drush sqlc```
 - [drush watchdog-show](http://drushcommands.com/drush-8x/watchdog/watchdog-show/). Example: ```drush ws --tail --extended```
 - [drush pm-projectinfo](http://drushcommands.com/drush-8x/pm/pm-projectinfo/). Example: ```drush pmpi --format=table```
 - [drush pm-list](http://drushcommands.com/drush-8x/pm/pm-list/). Example: ```drush pml --type=module --format=table --no-core --status=enabled```
 - [drush pm-releases](http://drushcommands.com/drush-8x/pm/pm-releases/). Example: ```drush rl --format=table drupal```
 - [drush config-list](http://drushcommands.com/drush-8x/config/config-list/). Example: ```drush cli system --format=list | grep article```
 - [drush config-get](http://drushcommands.com/drush-8x/config/config-get/). Example: ```drush cget system.site --format=yaml```
 - [drush field-info](http://drushcommands.com/drush-8x/field/field-info/) (Not ready at the moment. Please check this [issue](https://github.com/drush-ops/drush/issues/230))
 - [drush features-status](http://drushcommands.com/drush-8x/features/features-status/)

**Drupal Console** ([Drupal Console](https://drupalconsole.com/))

 - [drupal config:debug](https://hechoendrupal.gitbooks.io/drupal-console/content/en/commands/config-debug.html)
 - [drupal container:debug](https://hechoendrupal.gitbooks.io/drupal-console/content/en/commands/container-debug.html)
 - [drupal cron:debug](https://hechoendrupal.gitbooks.io/drupal-console/content/en/commands/cron-debug.html)
 - [drupal database:log:debug](https://hechoendrupal.gitbooks.io/drupal-console/content/en/commands/database-log-debug.html)
 - [drupal database:table:debug](https://hechoendrupal.gitbooks.io/drupal-console/content/en/commands/database-table-debug.html)
 - [drupal module:debug](https://hechoendrupal.gitbooks.io/drupal-console/content/en/commands/module-debug.html)
 - [drupal rest:debug](https://hechoendrupal.gitbooks.io/drupal-console/content/en/commands/rest-debug.html)
 - [drupal router:debug](https://hechoendrupal.gitbooks.io/drupal-console/content/en/commands/router-debug.html)
 - [drupal settings:debug](https://hechoendrupal.gitbooks.io/drupal-console/content/en/commands/settings-debug.html)
 - [drupal site:debug](https://hechoendrupal.gitbooks.io/drupal-console/content/en/commands/site-debug.html)
 - [drupal state:debug](https://hechoendrupal.gitbooks.io/drupal-console/content/en/commands/state-debug.html)
 - [drupal test:debug](https://hechoendrupal.gitbooks.io/drupal-console/content/en/commands/test-debug.html)
 - [drupal theme:debug](https://hechoendrupal.gitbooks.io/drupal-console/content/en/commands/theme-debug.html)
 - [drupal update:debug](https://hechoendrupal.gitbooks.io/drupal-console/content/en/commands/update-debug.html)
 - [drupal user:debug](https://hechoendrupal.gitbooks.io/drupal-console/content/en/commands/user-debug.html)
 - [drupal views:debug](https://hechoendrupal.gitbooks.io/drupal-console/content/en/commands/views-debug.html)

**Drupal modules**

 - [devel](https://www.drupal.org/project/devel) (devel, webprofiler). See the docs for the [WebProfiler](https://github.com/lussoluca/webprofiler).

**PHP debug and testing**

 - [blackfire.io](https://blackfire.io/). See [24 Days of Blackfire](https://blackfire.io/docs/24-days/index)

**Database debug**

 - [MySQL Workbench ](https://www.mysql.com/products/workbench/)

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
 - All modules, themes and distributions (Drupal projects) have the same type of configuration (under <project_name>/config/* folders).
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
 - We can override the paths for the ASD storage (eg on ```settings.php```).
 - All config. is tracked.
 - Diff. is availble to inspect the changes.
 - Config. is saved per content entity.
 - Config. can be individually imported/exported.
 - Config. synchronization requires all files to be present (missing config. files or settings will delete the configuration!)
 - Core config. system is working for the same only Drupal installation.
 - Exported config. files with UUID cannot be reused on another installation.
 - Always use the Config. API to export/import config. Do not edit files or database entries manually.
 - We can "override" a config. setting on the fly in the settings.php file.
 - Useful modules that can export, import or manage config. are [features](https://www.drupal.org/project/features), [config_update](https://www.drupal.org/project/config_update), [config_devel](https://www.drupal.org/project/config_devel), [config_sync](https://www.drupal.org/project/config_sync), [config_tools](https://www.drupal.org/project/config_tools), [config_share](https://www.drupal.org/project/config_share).

### Create an issue

### Create a pull request

### Contribute to documentation

### Get familiar with the new API (+API docs)

### Useful browser extensions and plugins

### Other

(Vagrant/Otto, Docker, Continuous Integration ...)
