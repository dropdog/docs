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

Useful git cheatsheets:

 - [Official git reference](https://git-scm.com/docs)
 - [training.github.com, github-git-cheat-sheet](https://training.github.com/kit/downloads/github-git-cheat-sheet.pdf)
 - [git-tower, git-cheat-sheet](https://www.git-tower.com/blog/git-cheat-sheet/)
 - [Advanced git cheat-sheet](http://www.cheat-sheets.org/saved-copy/git-cheat-sheet.pdf)

Interactive tools to learn git commands and terminology:

 - [Visual git cheat-sheet](http://ndpsoftware.com/git-cheatsheet.html)
 - [Learn git in 15 minutes](https://try.github.io)
 - [Learn git branching](http://pcottle.github.io/learnGitBranching/)

CLI tools (shortcuts) you can (should) use:

 - [git-flow](https://github.com/nvie/gitflow). A method as also as a collection of commands for successful git branching and development.
 - (Optional) [git hub](https://hub.github.com/). A tool to help create pull requests, compare commits, view issues and make your life on GH better.
 - (Optional) [git extras](https://github.com/tj/git-extras). Some useful git aliases/wrappers for humans (summary, undo, ignore, changelog etc)!

GUI Clients you can use. They are mostly used to see visual graphs of the commits, to solve conflicts, to browse repos etc.
 - [git-scm.com/downloads/guis](https://git-scm.com/downloads/guis)

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
 - [drush config-list](http://drushcommands.com/drush-8x/config/config-list/). Example: ```drush cli system --format=list```
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

### Create an issue

### Create a pull request

### Contribute to documentation

### Get familiar with the new API (+API docs)

### Useful browser extensions and plugins

### Other (Vagrant/Otto, Docker, Continuous Integration)...
