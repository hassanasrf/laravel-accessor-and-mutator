# laravel-accessor-and-mutator

What is Accessors ? 
Accessors create a dummy attribute on the object which you can access as if it were a database column. So if your database has user table and it has FirstName and LastName coloumn and you need to get full name then it will be like.

Syntax of Accessors :

```php
get{Attribute}Attribute
```

Example :

```php
public function getFullNameAttribute()
{
  return $this->FirstName. " " .$this->LastName;
}
```
After that you can get full user name with below Accessors.
```php
{{ $user->full_name }}
```

What is Mutator ?
Mutator is use to set value of attribute, A mutator transforms an Eloquent attribute value when it is set.

How to define a mutator,

```PHP
set{Attribute}Attribute
```
above method on your model where {Attribute} is the "studly" cased name of the column you wish to access.

Example : 
```PHP
<?php

namespace App\Models;

use Illuminate\Database\Eloquent\Model;

class Register extends Model
{
    /**
     * Set the user's first name.
     *
     * @param  string  $value
     * @return void
     */
    public function setNameAttribute($value)
    {
        $this->attributes['name'] = strtolower($value);
    }
}
```

Now you can use this in your controller like.
```php
use App\Models\Register;

$register= Register::find(1);

$register->name = 'hassanasrf';
```
