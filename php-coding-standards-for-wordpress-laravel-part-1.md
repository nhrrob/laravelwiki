## 1 PHP Coding Standards | Using PHPCS (PHP CodeSniffer) in WordPress

<br/>Date: February 09, 2024 <br/>


### Steps
#### Step 1. Installing PHPCS
- Github repo: https://github.com/PHPCSStandards/PHP_CodeSniffer/ 
- Install globally
```
composer global require "squizlabs/php_codesniffer=*"
```
- Now, you can run
```
~/.composer/vendor/bin/phpcs
```
- Or, simply `phpcs` if environment variable is set. 
<br>-i shows all the installed rulesets. First one is standard and will be used.
```
phpcs -i
```
- Use standard argument to use different ruleset.
```
~/.composer/vendor/bin/phpcs wp-config.php --standard=PSR12
```

<br>


#### Step 2. Installing WPCS (WordPress Coding Standards)

- Github repo: https://github.com/WordPress/WordPress-Coding-Standards 
- Installation commands
```
composer global config allow-plugins.dealerdirect/phpcodesniffer-composer-installer true
composer global require --dev wp-coding-standards/wpcs:"^3.0" 
```
- Now WordPress based standards will be added in phpcs.
```
phpcs -i
```
- You can use annotated ruleset just by adding phpcs.xml in your project root.
- Or, simply run this command to change the default standard to WordPress.
```
phpcs --config-set default_standard WordPress
```

<br>

#### Step 3. Using PHPCBF (PHP Code Beautifier And Fixer)
- Doc: https://github.com/PHPCSStandards/PHP_CodeSniffer/wiki/Fixing-Errors-Automatically 
- Helps to fix errors automatically
- Commands to fix errors (assuming environment variable is properly set). From twentytwentyone theme root:
```
phpcbf 404.php
```
- For details report add psvn. Definitions in the doc url.
```
phpcbf -p -s -v -n 404.php
```

<br>

#### Step 4. Setting up PHPCS for VS Code
- Go to extensions tab and install phpcs extension
- Now editor will show errors based on wpcs.

<br>

### We are done!

- Congratulations! You have successfully setup PHPCS (PHP CodeSniffer) in WordPress 

<br>


### Bonus:
- TBA

<br>


### <a href='https://github.com/nhrrob/laravelwiki'>Back to Laravel Wiki</a>