## Laravel Artisan Commands

<br/>Date: May 11, 2021 <br/>

### Popular Commands

<br>


#### 1. Laravel Version Check
``` 
php artisan --version 
```

<br>


#### 2. Cache Clear
``` 
php artisan cache:clear
php artisan config:clear
php artisan route:clear
php artisan view:clear
```

<br>


#### 3. Clear All (Cache, Config, Route, View)
``` 
php artisan optimize:clear
```

<br>


#### 4. Laravel Migration Run
- Migrate new migrations
``` 
php artisan migrate
```
- Drop all tables and run migration (with/out seed)
```
php artisan migrate:fresh --seed
php artisan migrate:refresh --seed
```

<br>


#### 5. Seed (Import data to db)
```
php artisan db:seed
php artisan migrate:fresh --seed
```

<br>


#### 6. Storage folder permission
- From project root
```
sudo chmod -R 0777 storage/
```

<br>


#### 7. bootstrap/cache folder permission
- From project root
```
sudo chmod -R 0777 bootstrap/cache/
```

<br>


#### 8. Composer commands
- Composer install/update
```
composer install
composer update
composer dump-autoload
```

<br>


#### 9. Git commands
- init, add, commit, pull, push
```
git init
git status
git branch
git add .
git commit -m "first commit"
git pull origin master
git push origin master
```

<br>


#### 10. Git Branch commands
- create, switch, delete
```
git branch
git checkout -b new_branch
git branch -D new_branch
git branch another_new_branch
git checkout another_new_branch
```


#### 11. Git merge branches
- pull, merge, add, commit, push
```
git branch
git status
git fetch --all
git checkout -b new_branch
git add .
git commit -m "changes from new branch"
git pull origin new_branch
git push origin new_branch
git checkout master
git pull origin master
git merge new_branch
git add .
git commit -m "merged with new branch"
git pull origin master
git push origin master
git status
```

<br>


#### 12. Artisan make commands
- Create model, migration, route, controller (All in one)
```
php artisan make:model Product -mrc
```
- Create one at a time
```
php artisan make:model Product
php artisan make:controller ProductController
php artisan make:migration create_products_table
php artisan make:request ProductRequest
php artisan make:resource ProductResource
php artisan make:seeder ProductSeeder
php artisan make:factory ProductFactory
```

<br>


#### 13. Serve Laravel Project
- Serve locally
```
php artisan serve
```

<br>


#### 14. Package install
- Install nhrrob/crudgenerator package
```
composer require nhrrob/crudgenerator
```

<br>


#### 15. Publish package files
- publish vendor files
```
php artisan vendor:publish
```

<br>


#### 16. Release package (tags)
- Add tag in your project
```
git tag
git tag v1.0.0
git push --tag
```

<br>


#### 100. TBA
- TBA

<br>


### We are done!

- Congratulations! You have found out almost all popular commands. <br>


### <a href='https://github.com/nhrrob/laravelwiki'>Back to Laravel Wiki</a>