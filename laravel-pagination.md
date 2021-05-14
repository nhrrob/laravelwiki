## Laravel Pagination

<br/>Date: May 14, 2021 <br/>

### Steps
#### Step 1. Controller : use paginate() 
- Fetch data using paginate():
```
$data['users'] = User::latest()->paginate(10);
```

<br>


#### Step 2. View (blade) file
- Add below code
``` 
<!-- Pagination  -->
<div class="d-flex justify-content-center">
    {{ $permissions->links() }}
</div>
```

<br>


#### Step 3. Update AppServiceProvider
- Add bootstrap suport for pagination
<br>Add below code in *boot()* method of app/Providers/AppServiceProvider.php
```
Paginator::useBootstrap();
```

- Dont forget to import Paginator class
```
use Illuminate\Pagination\Paginator;
```
<br>



### We are done!

Congratulations! You have successfully setup and configured Laravel Pagination with default design.

<br>


### <a href='https://github.com/nhrrob/laravelwiki'>Back to Laravel Wiki</a>