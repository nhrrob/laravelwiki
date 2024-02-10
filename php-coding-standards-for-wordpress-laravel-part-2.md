## 2 PHP Coding Standards | Using PHP CS Fixer (PHP Coding Standards Fixer) in Laravel - Laravel Pint

<br/>Date: October 27, 2023 <br/>


### Steps
#### Step 1. Installing Laravel Pint
- Comes by default with the latest Laravel versions.
- Official Doc: https://laravel.com/docs/10.x/pint 

<br>


#### Step 2. Using Laravel Pint

- You may run following commands
```
./vendor/bin/pint
```
- To fix a single file
```
./vendor/bin/pint app/Models/User.php
```
- See detail
```
./vendor/bin/pint -v 
```
- Only show errors, no fix
```
./vendor/bin/pint --test
```
- Apply pint on uncommitted changes
```
./vendor/bin/pint --dirty
```

<br>

#### Step 3. Changing rulesel
- Laravel Pint uses Laravel as default ruleset
- You may change it by using this command
```
pint --preset psr12
```

<br>

### We are done!

- Congratulations! You have successfully setup Laravel Pint for laravel projects. 

<br>


### Bonus:
- TBA

<br>


### <a href='https://github.com/nhrrob/laravelwiki'>Back to Laravel Wiki</a>