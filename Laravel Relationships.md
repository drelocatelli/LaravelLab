# Laravel Relationships

## One to One

```php
<?php

namespace App;

use Illuminate\Database\Eloquent\Model;

class User extends Model
{
    public function passport() {
        return $this->hasOne(App\Passport::class);
    }
}
```

## Belongs To

```php
<?php

namespace App;

use Illuminate\Database\Eloquent\Model;

class Passport extends Model
{
    public function user() {
        return $this->belongsTo(App\User::class);
    }
}
```

## Belongs To Many

```php
<?php

namespace App;

use Illuminate\Database\Eloquent\Model;

class Invoice extends Model
{
    public function products() {
        return $this->belongsToMany(App\Product::class);
    }
}
```

---

# Linking a model through another model

## Has One Throught

```php
suppliers:
- id
products:
- id
- supplier_id
product_history:
- id
- product_id
```

```php
<?php

namespace App;

use Illuminate\Database\Eloquent\Model;

class Supplier extends Model
{
    public function productHistory() {
        return $this->hasOneThrough(History::class, Product::class);
    }
}
```

## Has Many Through

```php
<?php

namespace App;

use Illuminate\Database\Eloquent\Model;

class Supplier extends Model
{
    public function productHistory() {
        return $this->hasManyThrough(App\History::class, App\Product::class);
    }
}
```