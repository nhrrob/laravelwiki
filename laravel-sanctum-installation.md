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

#### Step 3. **Add routes:**
Add register login and logout routes in routes/api.php
Update Versioning (e.x. V3)
``` 
Route::post('v1/egister', '\App\Http\Controllers\Api\V1\AuthController@register');
Route::post('v1/login', '\App\Http\Controllers\Api\V1\AuthController@login');

Route::group(['middleware' => ['auth:sanctum']], function () {
    Route::post('v1/logout', '\App\Http\Controllers\Api\V1\AuthController@logout');
});
``` 

<br>

#### Step 4. **Add methods in AuthController:**
Add methods in controller
``` 
public function register(Request $request) {
    $validatedData = $request->validate([
        'name' => 'required|max:55',
        'email' => 'email|required|unique:users',
        // 'password' => 'required|confirmed'
        'password' => 'required'
    ]);

    $validatedData['password'] = Hash::make($request->password);

    $user = User::create($validatedData);

    $accessToken = $user->createToken('authToken')->accessToken;

    return response(['user' => $user, 'access_token' => $accessToken], 201);
}

public function login(Request $request) {
    $loginData = $request->validate([
        'email' => 'email|required',
        'password' => 'required'
    ]);

    if (!auth()->attempt($loginData)) {
        return response(['message' => 'User does not exist, please check your details'], 400);
    }

    // $accessToken = auth()->user()->createToken('authToken')->accessToken;
    $accessToken = auth()->user()->createToken('authToken')->plainTextToken;
    // $user = User::where('email', $request->email)->first();
    // $accessToken = $user->createToken('auth-token')->plainTextToken;

    return response(['user' => auth()->user(), 'access_token' => $accessToken]);
}

public function logout(Request $request) {
    auth()->user()->tokens()->delete();

    return [
        'message' => 'Logged out'
    ];
}
``` 

#### Step 5. **Get Access Token**  
- Use login request to get access token
- Add this token as bearer token on each api request.
<br>

### We are done!

- Congratulations! You have successfully setup and configure Laravel Sanctum. <br>

- To build a restful api crud feel free to follow this repo: <br>
<a href="https://github.com/nhrrob/laravel-10-api-crud">https://github.com/nhrrob/laravel-10-api-crud </a> <br>
<a href="https://github.com/nhrrob/laravel-8-api-crud">https://github.com/nhrrob/laravel-8-api-crud </a> <br>
<a href="https://github.com/nhrrob/laravel-7-api-crud">https://github.com/nhrrob/laravel-7-api-crud</a>


<br>

### <a href='https://github.com/nhrrob/laravelwiki'>Back to Laravel Wiki</a>
