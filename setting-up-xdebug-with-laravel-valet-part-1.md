## 1 Setting up Xdebug with Laravel Valet & VSCode


<br/>Date: October 27, 2023 <br/>


### Steps
#### Step 1. Create A Laravel Project
- Create project
```
composer create-project laravel/laravel example-app
sudo chmod -R 0777 storage
sudo chmod -R 0777 bootstrape/cache
```

<br>


#### Step 2. Install pecl on macOS (already installed)

- Check if pecl is installed (By default installed in macOS)
```
pecl
```

<br>

#### Step 3. Check PHP version (System and CLI)
- CLI: Check PHP version and php.ini path (CLI version)
```
which php
php --ini
```
- Browser: Check phpinfo() in your project (project/public/index.php)
- Compare System and CLI PHP installation path (if different, then we need to add custom code in php.ini after Xdebug installation)

<br>

#### Step 4. Install Xdebug using pecl
- https://xdebug.org/docs/install
- You can verify what your PHP's architecture is with:
```
file `which php`
```
- arm64e
```
arch -arm64 sudo pecl install xdebug
```
- x86_64
```
arch -x86_64 sudo pecl install xdebug
```
- Otherwise
```
sudo pecl install xdebug
```
- Verify Xdebug installation => CLI:
```
php --version
php --ini
```
- Verify Xdebug installation => phpinfo in browser
- If xdebug not shown, then add some code in php.ini (path same as phpinfo or, xdebug installed path - get when info shows after installation)
- V2
```
zend_extension=xdebug.so
xdebug.remote_enable=1
xdebug.remote_log=/tmp/xdebug.log
```
- V3
```
xdebug.remote_log=/tmp/xdebug.log
xdebug.mode=debug
xdebug.start_with_request=yes
xdebug.discover_client_host=1
```
- Restart everything
```
brew services restart php
valet restart
```
- <b>Troubleshooting</b>:
- Delete pecl folder if exists or failed to mkdir error on Xdebug installation
- Copy installed Xdebug path to php.ini

<br>

#### Step 5. Install Chrome and VSCode Extension
- Chrome: xdebug helper
- VSCode: php debug by xdebug

<br>

#### Step 6. Start Debugging
- VSCode from memu => Start Debugging and Select everything from left bottom settings. Then add breakpoints in your code. Create json file if needed (default code).
<br>

### We are done!

- Congratulations! You have successfully setup Xdebug with Laravel Valet & VSCode. 

<br>


### Bonus:
- TBA

<br>


### <a href='https://github.com/nhrrob/laravelwiki'>Back to Laravel Wiki</a>