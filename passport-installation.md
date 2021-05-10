## Passport Installation (To Manage API Auth)

### Steps
1. **Install package:** 
    - Laravel latest version: <br>
``` composer require laravel/passport ```
    - Laravel old versions (Ex. Laravel 7): <br> 
``` composer require laravel/passport "~9.0" ```
    - Doc: https://laravel.com/docs/7.x/passport 

2. **Run migration:** <br>
``` php artisan migrate ```

3. **Generate personal access token:** <br>
``` php artisan passport:install ```

4. **Add HasApiTokens trait in your User Model:**
    - Laravel 8: <span style="color:#38761D">**App\Models\User.php**</span>
    - Laravel 7 or old: **App\Models\User.php**<br>
    ``` use HasApiTokens,```<br> 
    Replace comma with semicolon if there is no more trait <br><br> 
    Dont forget to import HasApiTokens. <br> 
    ``` use Laravel\Passport\HasApiTokens; ```

5. **Call the passport routes in AuthServiceProvider** <br>
Path: **App/Providers/AuthServiceProvider.php**<br>
    - Add in **boot** method <br>
    ``` Passport::routes(); ```

    - Dont forget to import the passport class <br>
    ``` use Laravel\Passport\Passport; ```

    - **Uncomment** the policies added in the protected method **$policies** <br>
    Example: **'App\Models\Model' => 'App\Policies\ModelPolicy',**

6. **Set the Driver:** <br>
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


### We are done!

- Congratulations! You have successfully setup and configure Laravel Passport. <br>

- To build a restful api crud feel free to follow this repo: <br>
<a href="https://github.com/nhrrob/laravel-8-api-crud">https://github.com/nhrrob/laravel-8-api-crud </a> <br>
<a href="https://github.com/nhrrob/laravel-7-api-crud">https://github.com/nhrrob/laravel-7-api-crud</a>



### <a href='https://github.com/nhrrob/laravelwiki'>Back to Laravel Wiki</a>