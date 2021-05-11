## Laravel from Scratch


<br/>Date: May 11, 2021 <br/>

Note: *For sample code follow repository mentioned below (at the end)* <br>


### Steps
#### Step 1. TBA 
- TBA

<br>


#### Step 2. TBA
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

### Bonus: Resource Routes
- Login: 
<br>Param: email (admin@admin.com) and password (password). 
<br>Get Bearer token
```
POST /api/login
```

- All Products: 
<br>Param: No parameter needed 
<br>View list of products
```
GET /api/products
```

- Create Product:
<br>Param: title 
<br>View new created product
```
POST /api/products
```

- Edit Product:
<br>Param: title 
<br>View new edited product
```
PUT /api/products/1
```

- View Single Product:
<br>Param: No parameter needed 
<br>View single product
```
GET /api/products/1
```

- Delete a Product:
<br>Param: No parameter needed 
<br>View deleted product
```
DELETE /api/products/1
```

<br>


### Bonus 2:
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