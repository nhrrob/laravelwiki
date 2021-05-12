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
```
- Add title field in migration file
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

#### Step 12. Update crudgenerator stub files (Adding Layout)
- Now we will add layout to crudgenerator stub files. Doing so, our future crud generated files will automatically have site default design. So we dont need to do anything on view files regarding layout design

- Follow this repo to get updated stub files (resources/stubs=>
update model_snake folder to add design/layout)
<br>Laravel Get Started Project:
<a href="https://github.com/nhrrob/laravel-get-started-project" target="_blank">https://github.com/nhrrob/laravel-get-started-project</a>

<br>


#### Step 13. Test Crud Generator : New Layout/Design
1. Generate a Demo Crud

    - Run crud generator command
    ```
    php artisan crud:generator
    ```
    Note: provide mode title=> Demo

    - Add title field in migration file
    ```
    $table->string('title');
    ```

    - Run migration
    ```
    php artisan migrate
    ```

    - Browse siteurl/demos.

    - Test Rest api too.

    <br>
    Congrats! Now your all new cruds will have site default design.

2. Delete Demo Crud files
    - Run delete command to delete all files at a time.
    ```
    php artisan crud:generator:delete
    ```
    - Now, manually remove migration file
    - Remove demo crud related routes from web.php and api.php

<br>


#### Step 14. Update Folder Structure
- Admin folder: For Controllers and resources/views
- admin: prefix of url and route name

- Update routes (web and api): 
    - Api (routes/api.php): Sample code
    ```
    Route::group([ 'namespace'=> 'App\Http\Controllers\Api\Admin', 'prefix' => 'admin',  'as'=>'admin.', 'middleware' => ['auth:api'] ], function () {
        Route::get('/products/search/{title}', 'ProductController@search');
        Route::apiResource('products', 'ProductController');
    });
    ```
     - Web (routes/web.php): Sample code
    ```
    Route::group([ 'namespace'=> 'App\Http\Controllers\Admin', 'prefix' => 'admin',  'as'=>'admin.', 'middleware' => 'auth' ], function () { 
        Route::resource('products', 'ProductController'); 
    });
    ```   

- Add admin folder for views and Admin folder for controllers (including Api)
    - Sample File/Folder Structure:

    ```
    #Controllers
    app/Http/Controllers/
    app/Http/Controllers/Admin
    
    #Views
    resources/views/
    resources/views/admin
    
    ------------------------------

    #API Controllers
    app/Http/Controllers/Api
    app/Http/Controllers/Api/Admin
    ```
    - Update namespace and Import class where needed.
    - Add **admin** prefix in view() and route names within **Controllers**.
    - Add **admin** prefix in route names within **view blade files**.


<br>Hurray! We have successfully added admin prefix for our project.

<br>


#### Step 15. Lets Update Stub files for future cruds
- Now, we will update crud generator related stub files. So, when we generate crud everything should work fine with prefix admin. Also files under Admin folder in case of backend.

- For frontend, we can again update stub files (just removing Admin and admin)
- Sample code can be found here:
<br>Laravel Get Started Project => <a href="https://github.com/nhrrob/laravel-get-started-project" target="_blank">https://github.com/nhrrob/laravel-get-started-project</a>

**Note: For future crud routes: we neeed to cut and paste within the route group**
<br>


#### Step 16. Lets generate another crud (to test stub changes) 
- As we changed stub files, now everything should work fine with proper namespace and route names as well as view path.
```
php artisan crud:generator
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
- Route: Cut and paste generated route lines into the route group (prefix: admin)
<br>Update controller name keeping only the name; no namespace as it is added in the route group

- Move controllers under Admin and Api\Admin folders (check namespace too)
- Move view folder ```project``` into admin
- Lets browse siteurl/admin/projects; Also check api using postman.
<br>


#### Step 17. Add NHR CSS Helper 
- Copy below gist code to resources/css/nhrrob-css-helper.css file
<br>CSS Link: <a href="https://gist.github.com/nhrrob/ce5ef7e921104feff1fc3bb8c06c75f3" target="_blank">Gist: NHRRob CSS Helper</a> 

-  Add Helper CSS in your main layout (views/layouts/app.blade.php)
```
<link href="{{ asset('css/nhrrob-css-helper.css') }}" rel="stylesheet">
```
- To test helper css: Example classes=> p-0, p-1, p-2, p-3, p-4 
<br>(p-0 means padding: 0; 1 means 10px; 2= 20px) 
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