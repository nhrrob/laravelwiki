## Laravel Sanctum Installation (To Manage API Auth)

<br/>Date: Aug 12, 2024 <br/>

### Steps
#### Step 1. **Install package:** 
- Laravel latest version: <br>
``` 
php artisan install:api
```
- routes/api.php will be created if not preset. Better delete and then let sanctum create with proper code.
- Doc: https://laravel.com/docs/11.x/sanctum 
<br>

#### Step 2. **Include HasApiTokens trait:**
Add HasApiTokens trait in your User Model:
- **App\Models\User.php**
``` 
use HasApiTokens,
```
Replace comma with semicolon if there is no more trait <br><br>
Dont forget to import HasApiTokens. <br> 

``` 
use Laravel\Sanctum\HasApiTokens; 
```
<br>

### We are done!

- Congratulations! You have successfully setup and configure Laravel Sanctum. <br>

- To build a restful api crud feel free to follow this repo: <br>
<a href="https://github.com/nhrrob/laravel-10-api-crud">https://github.com/nhrrob/laravel-10-api-crud </a> <br>
<a href="https://github.com/nhrrob/laravel-8-api-crud">https://github.com/nhrrob/laravel-8-api-crud </a> <br>
<a href="https://github.com/nhrrob/laravel-7-api-crud">https://github.com/nhrrob/laravel-7-api-crud</a>


<br>

### <a href='https://github.com/nhrrob/laravelwiki'>Back to Laravel Wiki</a>