## Building a RESTful API Crud with Laravel Passport


<br/>Date: May 10, 2021 <br/>

Note: *For sample code follow repositories mentioned below (at the end)* <br>


### Steps
#### Step 1. **Setup and Configure Laravel Passport** 
- <a href="https://github.com/nhrrob/laravelwiki/blob/master/passport-installation.md" target="_blank">Passport Installation Guide</a>

#### Step 2. Create Model with Migration
- Run below command
```
php artisan make:model Product -m
php artisan migrate
```
<br>

#### Step 3. Create a Resource
- Laravel provides a resource class that helps transforming models and the model collections into JSON. 
```
php artisan make:resource ProductResource
```
<br>


#### Step 4. Create controller under Api folder 
- Dont forget to update namespace with Api;

```
php artisan make:controller Api/AuthController
```
- Also import classes where needed (e.x. Hash and User)
<br>


#### Step 5. Create AuthController under Api folder 
- Dont forget to update namespace with Api;

```
php artisan make:controller Api/AuthController
```
- Also import classes where needed (e.x. Hash and User)
<br>

#### Step 6. Create ProductController under Api folder 
- Dont forget to update namespace with Api;

```
php artisan make:controller Api/ProductController --api --model=Product
```
- Also import classes where needed.
<br>


#### Step 7. Add Routes in routes/api.php 
- Every route has prefix /api for this file

- Laravel 8 : Dont forget to import classes.
```
Route::post('register', [AuthController::class, 'register']);
Route::post('login', [AuthController::class, 'login']);

Route::group(['middleware' => ['auth:api']], function () {
    Route::post('/logout', [AuthController::class, 'logout']);
    Route::get('/products/search/{name}', [ProductController::class, 'search']);
});
Route::apiResource('products', ProductController::class)->middleware('auth:api');
```
- Laravel 7

```
Route::group(['namespace'=>'Api'], function () {
    Route::post('register', 'AuthController@register');
    Route::post('login', 'AuthController@login');
    
    Route::group(['middleware' => ['auth:api']], function () {
        Route::post('/logout', 'AuthController@logout');
        Route::get('/products/search/{name}', 'ProductController@search');
        Route::apiResource('products', 'ProductController');
    });
});
```

<br>

#### Step 8. Test Using Postman
- Request /api/login 
- Create a default user using DatabaseSeeder: admin@admin.com/password
- Get bearer token from login route
- Add bearer token in Authorization tab: Select type bearer token and add your token as value
- In Headers tab: 
```
Add: Content-Type => application/json  
Add: Accept => application/json
```
- In Body tab:
```
Select: x-www-form-urlencode
Add: title=> "your demo title"
```
- Now you should be able to send and fetch all requests.

<br>


### We are done!

- Congratulations! You have successfully built a RESTful API Crud with Laravel Passport. <br>

- Two rest api crud repositories: <br>
<a href="https://github.com/nhrrob/laravel-8-api-crud">https://github.com/nhrrob/laravel-8-api-crud </a> <br>
<a href="https://github.com/nhrrob/laravel-7-api-crud">https://github.com/nhrrob/laravel-7-api-crud</a>

<br>


### Note
- If you run ```php artisan migrate:fresh --seed``` then you will lose personal access token of passport.
- So, in that case run again: 
```
php artisan passport:install 
```
<br>


### <a href='https://github.com/nhrrob/laravelwiki'>Back to Laravel Wiki</a>