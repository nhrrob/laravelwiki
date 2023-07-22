## 2 Laravel Deployment with Github Actions | Setting up Github Actions - Auto Deployment


<br/>Date: July 11, 2021 <br/>


### Steps
#### Step 1. Add Github Action Secrets
- We will auto deploy using SSH. We can store our secret keys in the Github Repo specific Settings tab. 
```
Github Repo => Settings tab => Secrets and variables => Actions. 
```
- Example url: https://github.com/nhrrob/nazmulrobin_laravel/settings/secrets/actions

<br>


#### Step 2. Add Github Workflows
- In the project root folder, create .github folder. 
- Create a yml file under .github/workflows folder.
```
project_root/.github/workflows/laravel.yml
```
- Gist: laravel.yml file is added in this gist => https://gist.github.com/nhrrob/141e6abb859cec8859e0cb1777835add 

<br>


#### Step 3. Add deploy.sh file
- In the project root folder, create deploy.sh file 
```
project_root/deploy.sh
```
- Gist: deploy.sh file is added in this gist => https://gist.github.com/nhrrob/7d9f1385e941e1ae90a1627b656ca2b4 

<br>


#### Step 4. Now push to production branch and see MAGIC
- Now make changes and push to production branch
```
- git checkout production
- git add .
- git commit -m "Magic"
- git pull origin production
- git push origin production
```
- Now go to your github repository and see Github Action tab (https://github.com/nhrrob/blog_nazmulrobin_com/actions)
- You will see action is running there.

<br>


### We are done!

- Congratulations! You have successfully TBA. <br>


### Note

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