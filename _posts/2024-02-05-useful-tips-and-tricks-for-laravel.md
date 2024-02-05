---
title: Useful Tips And Tricks for Laravel
author: bo3bdo
date: 2024-02-05 11:33:00 +0800
categories: [Laravel, Tutorial]
tags: [laravel, tutorial]
pin: false
math: false
mermaid: false
image:
  path: assets/img/50616.jpg
  lqip: data:image/webp;base64,UklGRpoAAABXRUJQVlA4WAoAAAAQAAAADwAABwAAQUxQSDIAAAARL0AmbZurmr57yyIiqE8oiG0bejIYEQTgqiDA9vqnsUSI6H+oAERp2HZ65qP/VIAWAFZQOCBCAAAA8AEAnQEqEAAIAAVAfCWkAALp8sF8rgRgAP7o9FDvMCkMde9PK7euH5M1m6VWoDXf2FkP3BqV0ZYbO6NA/VFIAAAA
  alt: image
---

# Elevate your application’s performance with these expert tips and tricks.

![alt text](../assets/img/50616.jpg)

#### Laravel is one of the most widely used PHP frameworks in the world. Its simplicity, ease of use, and robust features have made it a popular choice for developers who want to create high-quality web applications with ease. However, even seasoned Laravel developers can sometimes struggle with certain aspects of the framework.

#### The Laravel tips and tricks tutorial covers a variety of advanced techniques for developers using the Laravel PHP framework to build more efficient and effective web applications. Let’s get started!

## Make your code more elegant using Eloquent

1. Local query scopes

Make your code more elegant using Eloquent
Local query scopes

```php
$admins = User::where('active', '=', 1)->where('is_admin', '=', 1)->get();
```

To achieve this, we can utilize Local Query Scopes to improve code readability and reduce repetition. As an example, we can create the following functions in our model:

```php
public function scopeActive($query)
{
    return $query->where('active', '=', 1);
}

public function scopeAdmin($query)
{
    return $query->where('is_admin', '=', 1);
}
```

Now, our original query would look like this:

```php
$admins = User::active()->admin()->get();
```

2. Global query scopes

The global query scope allows you to apply a constraint to all queries on a model by default.

Let’s create a new global scope class.

```php
<?php

namespace App\Scopes;

use Illuminate\Database\Eloquent\Builder;
use Illuminate\Database\Eloquent\Model;
use Illuminate\Database\Eloquent\Scope;

class ActiveScope implements Scope
{
    public function apply(Builder $builder, Model $model)
    {
        $builder->where('active', '=', 1);
    }
}
```

Now, we will add scope to our model. So that when we use Eloquent ORM, it applies automatically.

```php
<?php

namespace App;

use Illuminate\Database\Eloquent\Model;
use App\Scopes\ActiveScope;

class User extends Model
{
    protected static function boot()
    {
        parent::boot();

        static::addGlobalScope(new ActiveScope);
    }
}
```

How to use

```php
$users = User::all();
// in the above query we will get only active users.

$users = User::withoutGlobalScope(ActiveScope::class)->get();
// In the above query we will get all users.
```

### Model boot() method

The static boot() method is automatically executed when a model is instantiated, making it an ideal location to add behavior or event bindings. In this case, setting the default value of the is_admin field during the creation of the model object is a suitable example. However, the sentence structure could be improved by breaking it into two or more sentences for better readability.

```php
<?php

namespace App;

use Illuminate\Database\Eloquent\Model;

class User extends Model
{
        self::creating(function($model) {
            $model->is_admin = 0;
        });
}
```

### is() method in Laravel

Determines whether two models belong to the same table and share identical IDs.

```php
$user = User::find(1);
$sameUser = User::find(1);
$diffUser = User::find(2);
$user->is($sameUser);       // true
$user->is($diffUser);       // false
```

## Model properties

There are some properties of an Eloquent model:

```php
<?php

namespace App;

use Illuminate\Database\Eloquent\Model;

class User extends Model
{
   protected $table = 'users'; // users table is associated with model we can change here.

   protected $connection = 'sqlite'; // we can customize our database connection.

   protected $fillable = ['name', 'email', 'password']; // The attributes that are mass assignable.

   protected $dates = ['created_at', 'deleted_at']; // attributes that should be mutated to dates so we can change format like format('M d Y')

   protected $appends = ['field_name']; // we can add additional field to json response

   protected $primaryKey = 'uuid'; // which field will be primary key of the model

   public $incrementing = false; // disable auto-increment id for the model!

   protected $perPage = 30; // we can override default 15 pagination using $perPage variable

   const CREATED_AT = 'created';

   const UPDATED_AT = 'updated'; // we can change field name of created_at and updated_at.

   public $timestamps = false; // disable timestamp for current model.

   protected $with = []; // relations to eager load on every query.

   protected $withCount = []; // The relationship counts that should be eager loaded on every query.
}
```

## Eloquent where date methods

In Eloquent, check the date with functions whereDay(), whereMonth(), whereYear(), whereDate() and whereTime().

```php
$products = Product::whereDate('created_at', '2023-01-31')->get();
$products = Product::whereMonth('created_at', '12')->get();
$products = Product::whereDay('created_at', '31')->get();
$products = Product::whereYear('created_at', date('Y'))->get();
$products = Product::whereTime('created_at', '=', '14:13:58')->get();
```

## Conclusion

Laravel is a powerful PHP framework that can help developers build robust and scalable web applications. By using some of the tips and tricks outlined in this tutorial, you can take your Laravel development skills to the next level and create high-quality web applications that meet your users’ needs.
