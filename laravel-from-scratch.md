## Laravel from Scratch


<br/>Date: May 11, 2021 <br/>

Note: *For sample code follow repository mentioned below (at the end)* <br>


### Steps
#### Step 1. Install Laravel 
- Laravel 8
<br>Note: If laravel installed globally (```composer global require laravel/installer```)
```
laravel new blog
```

- Laravel 7 (older version)

```
composer create-project --prefer-dist laravel/laravel:^7.0 blog
```

<br>


#### Step 2. Add DB settings in .env file
- Create DB and Add in .env file

<br>


#### Step 2.1 (Optional) Create virtual host
- Create vhost for  projectpath/public folder
- Browse example.rob (virtual host)
- You can also ignore vhost and simply run
```
php artisan serve
```
<br>


#### Step 3. Add permission to storage folder
- Storage folder needs write permission
```
sudo chmod -R 0777 storage/
```
Note: For Linux and MacOS only

- Now, you should be able to access project url (vhost or serve url)
<br>


#### Step 4. Laravel Auth Setup
We will use laravel default auth
- Laravel 8
```

```
- Laravel 7 (Older version)


<br>


### We are done!

- Congratulations! You have successfully built a Laravel Get Started Project. <br>


### Note
- If you run ```php artisan migrate:fresh --seed``` then you will lose personal access token of passport.
- So, in that case run again: 
```
php artisan passport:install 
```
<br>

### Bonus:
- You can always run below commands
```
php artisan optimize:clear
sudo chmod -R 0777 storage/
sudo chmod -R 0777 bootstrap/cache
php artisan cache:clear
php artisan config:clear
php artisan route:clear
php artisan view:clear
composer dump-autoload
```

<br>


### <a href='https://github.com/nhrrob/laravelwiki'>Back to Laravel Wiki</a>