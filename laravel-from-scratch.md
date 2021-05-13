## Laravel from Scratch (Building Laravel Get Started Project)


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
composer require laravel/ui
php artisan ui bootstrap --auth
npm install && npm run dev
npm install && npm run dev
php artisan migrate
```
- Laravel 7 (Older version)
```
composer require laravel/ui:^2.4
php artisan ui vue --auth
npm install && npm run dev
php artisan migrate
```

<br>


#### Step 5. Seed an admin user
- Add code in run() : database/seeders/DatabaseSeeder.php
<br>*Dont forget to import User class*
```
User::create([
    'name' => 'Nazmul Hasan Robin',
    'email' => 'admin@admin.com',
    'password' => '$2y$10$92IXUNpkjO0rOQ5byMi.Ye4oKoEa3Ro9llC/.og/at2.uheWG/igi', // password
]);
```
- Run migration and seed
```
php artisan migrate:fresh --seed
```
- Now, login with admin@admin.com/password

<br>


#### Step 6. Install Nhrrob Crudgenerator
- Install a crudgenerator that generate web and api files
```
composer require nhrrob/crudgenerator
php artisan vendor:publish
```
<br>


#### Step 7. Install Laravel Passport for Rest Api  
- Nhrrob Crudgenerator generates basic crud as well as Rest crud files. If we want to use rest api then we need laravel passport.
Its an optional step if we dont need rest api.

Link: https://github.com/nhrrob/laravelwiki/blob/master/laravel-passport-installation.md 
- If you run migrate and seed in the future, you need to re create personal access token. So, run 
```
php artisan migrate:fresh --seed
php artisan passport:install
```

<br>

#### Step 8. Clear cache and dump autoload (do it often)  
- Clear cache and dump autoload files.
```
sudo chmod -R 0777 storage/
sudo chmod -R 0777 bootstrap/cache
composer dump-autoload
php artisan optimize:clear
php artisan cache:clear
php artisan config:clear
php artisan view:clear
php artisan route:clear
clear
```

<br>


#### Step 9. Generate Web and Api Crud for Product
- Thanks to <a href="https://github.com/nhrrob/crudgenerator" target="_blank">nhrrob/crudgenerator</a> to make it happen!
```
php artisan crud:generator
php artisan crud:generator --admin
```
<br>Note: --admin creates crud under Admin folder

- Add title field in migration files
```
$table->string('title');
```
- Run migration
```
php artisan migrate
```
- Browse siteurl/products
- Test create, edit, delete and list
- Cheers!

<br>

## 
Note: If you want to create crud by your own, you may follow these repositories instead of creating by generator.

1. Two rest api crud repositories: <br>
<a href="https://github.com/nhrrob/laravel-8-api-crud" target="_blank">https://github.com/nhrrob/laravel-8-api-crud </a> <br>
<a href="https://github.com/nhrrob/laravel-7-api-crud" target="_blank">https://github.com/nhrrob/laravel-7-api-crud</a><br>

2. Two basic crud repositories:<br>
<a href="https://github.com/nhrrob/laravel-8-crud" target="_blank">https://github.com/nhrrob/laravel-8-crud </a><br>
<a href="https://github.com/nhrrob/laravel-7-crud" target="_blank">https://github.com/nhrrob/laravel-7-crud</a><br>

3. Rest Api Step by Step Guide:
<a href="https://github.com/nhrrob/laravelwiki/blob/master/restful-api-crud-with-passport.md" target="_blank">https://github.com/nhrrob/laravelwiki/blob/master/restful-api-crud-with-passport.md</a><br>
##


#### Step 10. Test Api using Postman
- Thanks to <a href="https://github.com/nhrrob/crudgenerator" target="_blank">nhrrob/crudgenerator</a> to make it happen!
- We need to add Api auth routes first as crudgenerator doesn't add it by itself but provide link to copy the code.
- Add below auth routes to routes/api.php (above your generated routes)
Link: https://gist.github.com/nhrrob/fbc0857c3b5ed8c03ca8cc4ebdead749 
```
Route::post('register', '\App\Http\Controllers\Api\AuthController@register');
Route::post('login', '\App\Http\Controllers\Api\AuthController@login');

Route::group(['middleware' => ['auth:api']], function () {
    Route::post('/logout', '\App\Http\Controllers\Api\AuthController@logout');
});
```
- Testing: Follow below link 
<br>
Link: <a href="https://github.com/nhrrob/laravelwiki/blob/master/restful-api-crud-with-passport.md">https://github.com/nhrrob/laravelwiki/blob/master/restful-api-crud-with-passport.md</a>
<br> Step title: Test Using Postman (maybe: Step 8)

<br>


#### Step 11. Update product view files (Adding Layout)
- We will use laravel default design (provided layout)

- Follow this repo to get the default layout (resources/views/product)
<br>Laravel Get Started Project:
<a href="https://github.com/nhrrob/laravel-get-started-project" target="_blank">https://github.com/nhrrob/laravel-get-started-project</a>

<br>


#### Step 12. Lets Update Stub files for future cruds
- Now, we will update crud generator related stub files. So, future cruds will have our project default layout 

- Sample code can be found here:
<br>Laravel Get Started Project => <a href="https://github.com/nhrrob/laravel-get-started-project" target="_blank">https://github.com/nhrrob/laravel-get-started-project</a>

<br>


#### Step 13. Lets generate another crud (to test stub changes) 
- As we changed stub files, now everything should work fine with project default layout.
```
php artisan crud:generator
php artisan crud:generator --admin
```
- Model Title: Project
- Add title field in migration file
```
$table->string('title');
```
- Run migration and seed demo data
```
php artisan migrate:fresh --seed
php artisan passport:install
```
- Backend: Lets browse siteurl/admin/projects; Also check api using postman.
- Frontend: Lets browse siteurl/projects; Also check api using postman.

<br>


#### Step 14. Add NHR CSS Helper 
- Copy below gist code to public/css/nhrrob-css-helper.css file
<br>CSS Link: <a href="https://gist.github.com/nhrrob/ce5ef7e921104feff1fc3bb8c06c75f3" target="_blank">Gist: NHRRob CSS Helper</a> 

-  Add Helper CSS in your main layout (views/layouts/app.blade.php)
```
<link href="{{ asset('css/nhrrob-css-helper.css') }}" rel="stylesheet">
```
- To test helper css: Example classes=> p-0, p-1, p-2, p-3, p-4 
<br>(p-0 means padding: 0; 1 means 10px; 2= 20px) 

<br>


#### Step 15. Spatie Laravel Permission Setup
- Help link: <a href="https://github.com/nhrrob/laravelwiki/blob/master/spatie-laravel-permission-setup.md" target="_blank">Spatie Laravel Permission Setup</a>

<br>


#### Step 16. Add Dashboard page for all users
- Sample code can be found here:
<br>Laravel Get Started Project => <a href="https://github.com/nhrrob/laravel-get-started-project" target="_blank">https://github.com/nhrrob/laravel-get-started-project</a>

- Check below files
```
- routes/web.php
- app/Http/Controllers/Admin/DashboardController
- resources/views/admin/dashboard/index.blade.php
```

<br>


#### Step 17. Add style, script, admin layout
- Createa two style files and two js files (backend and frontend)
```
- public/css/admin_style.css
- public/css/style.css

- public/js/admin_script.js
- public/js/script.js
```
- Create resources/views/admin/layouts/app.blade.php
add style in header and script in just before body tag.
    - Header (beofre head tag) : Example of frontend layout
    ```
    <link href="{{ asset('css/style.css') }}" rel="stylesheet">

    @yield('header')
    @yield('css')
    ```
    - Footer (before body tag) : Example of frontend layout
    ```
    <script src="{{{{ asset('js/script.js') }}}}"></script>
    @stack('js')
    ```
- update your view files @extend (as we are using admin.layouts.app now)
- Update app name in your .env to "Laravel Get Started"
<br>


#### Step 18: TBA
- TBA

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