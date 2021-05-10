## Laravel Passport Installation (To Manage API Auth)

<br/>Date: May 10, 2021 <br/>

### Steps
#### Step 1. **Install package:** 
- Laravel latest version: <br>
``` 
composer require laravel/passport 
```
- Laravel old versions (Ex. Laravel 7): <br> 
``` 
composer require laravel/passport "~9.0" 
```
- Doc: https://laravel.com/docs/7.x/passport 
<br>

#### Step 2. **Run migration:** <br>
``` 
php artisan migrate 
```
<br>

#### Step 3. **Generate personal access token:** <br>
``` 
php artisan passport:install 
```
<br>

#### Step 4. **Include HasApiTokens trait:**
Add HasApiTokens trait in your User Model:
- Laravel 8: **App\Models\User.php**
- Laravel 7 or old: **App\Models\User.php**<br>
``` 
use HasApiTokens,
```
Replace comma with semicolon if there is no more trait <br><br>
Dont forget to import HasApiTokens. <br> 

``` 
use Laravel\Passport\HasApiTokens; 
```
<br>

#### Step 5. **Call the passport routes in AuthServiceProvider** <br>
Path: **App/Providers/AuthServiceProvider.php**<br>
- Add in **boot** method <br>
``` 
Passport::routes(); 
```

- Dont forget to import the passport class <br>
``` 
use Laravel\Passport\Passport; 
```

- **Uncomment** the policies added in the protected method **$policies** <br>
Example: **'App\Models\Model' => 'App\Policies\ModelPolicy',**
<br>

#### Step 6. **Set the Driver:** <br>
This is our final step. We need to change the api driver from default token to passport.<br>
- Go to **config\auth.php** and locate the **guards** array. In the **api key**, change the driver from **token** to **passport** <br>

- Should look like this (Ex. Laravel 8):
```
'guards' => [
    'web' => ...
    'api' => [
        'driver' => 'passport',
        ...
    ]
]
```
<br>

### We are done!

- Congratulations! You have successfully setup and configure Laravel Passport. <br>

- To build a restful api crud feel free to follow this repo: <br>
<a href="https://github.com/nhrrob/laravel-8-api-crud">https://github.com/nhrrob/laravel-8-api-crud </a> <br>
<a href="https://github.com/nhrrob/laravel-7-api-crud">https://github.com/nhrrob/laravel-7-api-crud</a>


<br>

### <a href='https://github.com/nhrrob/laravelwiki'>Back to Laravel Wiki</a>