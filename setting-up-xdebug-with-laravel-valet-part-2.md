## 2 Profiling PHP Applications with Xdebug


<br/>Date: July 30, 2023 <br/>


### Steps
#### Step 1. Create Laravel Project 
- Create laravel project in your local.
Link: <a href="https://github.com/nhrrob/laravelwiki/blob/master/laravel-from-scratch.md">https://github.com/nhrrob/laravelwiki/blob/master/laravel-from-scratch.md</a>

<br>


#### Step 2. Push to a GitHub repository 
- Popular commands 
Link: <a href="https://github.com/nhrrob/laravelwiki/blob/master/laravel-artisan-commands.md">https://github.com/nhrrob/laravelwiki/blob/master/laravel-artisan-commands.md</a>

<br>


#### Step 3. Pull from GitHub to Live Server
- Keep all your files outside of your public_html folder. That is the root folder (1 level up of public_html folder).
- Login using SSH (or you can use cPanel terminal too)
```
ssh -v username@ip-address -p port-number
```
- Pull the code manually from Github to the VPS/Shared Hosting (via SSH)
```
git clone https://username:token@github.com/nhrrob/project-name.git
```

<br>


#### Step 4. Setup Database 
- Create Database. DB User. And Assign the user to that DB. Use cPanel to do all these things.
- Save all the details. We will use this credentials in our env file.

<br>


#### Step 5. Add .env file
- Add .env and update env details
```
cp .env.example .env
nano .env
```
- Update DB details or follow your local .env file
- nano editor: ctrl o - write meesage to save; hit enter; ctrl x - exit;

<br>


#### Step 6. Setup Project 
- Useful Commands
```
mkdir bootstrap/cache
composer update
php artisan key:generate
php artisan migrate:fresh --seed
```

<br>


#### Step 7. public (project) folder to public_html (live server) 
- Copy all from public folder to public_html
```
cp -a /source/. /dest/
```
- Update index.php (vendor and bootstrap path)

<br>

### We are done!

- Congratulations! You have successfully deployed Laravel applicationn to live server. 

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