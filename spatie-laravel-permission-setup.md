## Spatie Laravel Permission Setup (Install and Configuration)

<br/>Date: May 13, 2021 <br/>

### Steps
#### Step 1. **Install package:** 
- Install command: [skip permission command if not needed]
```
composer require spatie/laravel-permission
php artisan vendor:publish --provider="Spatie\Permission\PermissionServiceProvider"
sudo chmod -R 0777 storage/
php artisan optimize:clear
php artisan migrate
```

<br>


#### Step 2. Add **HasRoles** trait on User model (Also import spatie class)
``` 
use HasRoles,
```

<br>


#### Step 3. Add RolesAndPermissionsSeeder and UserSeeder
- Create Seeder Files
```
php artisan make:seeder RolesAndPermissionsSeeder
php artisan make:seeder UserSeeder
```
- Include RolesAndPermissionsSeeder and UserSeeder in DatabaseSeeder file
<br>(Also comment out existing User::create() code in DatabaseSeeder class; As we will use spatie now to create user and assign permission)
```
$this->call(RolesAndPermissionsSeeder::class);
$this->call(UserSeeder::class);
```

- Update RolesAndPermissionsSeeder and UserSeeder
Link: <a href="https://github.com/nhrrob/laravel-get-started-project">https://github.com/nhrrob/laravel-get-started-project</a>

<br>


#### Step 4: Update migration file: add group name field
- Add group_name field on permissions table (Migration file: permissions from spatie)
```
$table->string('group_name')->nullable();
```
- Run migration and seed
```
php artisan migrate:fresh --seed
```

<br>


#### Step 5: Basic Usage (in controller)
- Add below code in your crud controller **__construct** method
<br>Example: **user** permission group
```
$this->middleware('permission:user list')->only('index');
$this->middleware('permission:user create')->only(['create', 'store']);
$this->middleware('permission:user view')->only('view');
$this->middleware('permission:user edit')->only(['edit', 'update']);
$this->middleware('permission:user delete')->only('destroy');
```

<br>


#### Step 6: Update app/Http/kernal.php => $routeMiddleWare 
```
'permission' => \Spatie\Permission\Middlewares\PermissionMiddleware::class,
'role' => \Spatie\Permission\Middlewares\RoleMiddleware::class,
'role_or_permission' => \Spatie\Permission\Middlewares\RoleOrPermissionMiddleware::class,

```

For laravel 11, bootstrap/app.php (`->withMiddleware(function (Middleware $middleware) {`)
```
//
// $middleware->append(\Spatie\Permission\Middlewares\PermissionMiddleware::class);
// $middleware->append(\Spatie\Permission\Middlewares\RoleMiddleware::class);
// $middleware->append(\Spatie\Permission\Middlewares\RoleOrPermissionMiddleware::class);

$middleware->alias([
    // 'subscribed' => EnsureUserIsSubscribed::class,
    'permission' => \Spatie\Permission\Middlewares\PermissionMiddleware::class,
    'role' => \Spatie\Permission\Middlewares\RoleMiddleware::class,
    'role_or_permission' => \Spatie\Permission\Middlewares\RoleOrPermissionMiddleware::class,
]);
```

Note: Dont forget to update storage folder often as spatie uses cache

<br>

#### Step 7: Super Admin configuration
- Link: <a href="https://spatie.be/docs/laravel-permission/v6/basic-usage/super-admin">https://spatie.be/docs/laravel-permission/v3/basic-usage/super-admin</a>
- Add below code in boot method of AuthServiceProvider
```
Gate::before(function ($user, $ability) {
    return $user->hasRole('super-admin') ? true : null;
});
```

### We are done!

Congratulations! You have successfully setup and configured Spatie Laravel Permission.

<br>


### <a href='https://github.com/nhrrob/laravelwiki'>Back to Laravel Wiki</a>
