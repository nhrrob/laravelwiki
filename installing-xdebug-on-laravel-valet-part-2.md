## 2 Profiling PHP Applications with Xdebug


<br/>Date: July 30, 2023 <br/>


### Steps
#### Step 1. Setup profiling with Xdebug
- Add profiler settings in php.ini (where Xdebug is loaded)
```
php --ini
sudo nano /opt/homebrew/etc/php/8.2/php.ini
```

Add below settings
```
xdebug.mode=profile
xdebug.output_dir=/tmp/profiles
xdebug.profiler_output_name=cachegrind.out.%R.%u
xdebug.use_compression=false
```

- Create directory
```
mkdir /tmp/profiles
```

- Check Xdebug info
```
php -r 'xdebug_info();' | less -R
```

- Restart valet
```
valet restart
```

<br>


#### Step 2. Analysing Data
- We will be using <b>QCacheGrind</b> for analysing data.

- Install (Takes a lot (~20mins) of time for me)
```
brew install qcachegrind
```

- Browse WordPress homepage and few other pages

- Check how many profile files  are created. One file for each request.
```
ls -l /tmp/profiles
```

- Open a file with QCacheGrid
```
qcachegrind /tmp/profiles/filename
```

- QCacheGrind tour

- Check which functions are taking most times and memories.

<br>

### We are done!

- Congratulations! You have successfully completed analysing profile report using Xdebug with Laravel Valet.

<br>


### Bonus:
- KCacheGrind for Linux users. QCacheGrind for MacOS and Windows.
- For QCacheGrind, turn off compression. Otherwise it will show "unknown file format". xdebug.use_compression=false 

<br>


### <a href='https://github.com/nhrrob/laravelwiki'>Back to Laravel Wiki</a>