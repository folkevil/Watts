# Watts

**Watts** - A powerful API based CRUD genertor for Lumen micro-services

[![Codeship](https://img.shields.io/codeship/013b03f0-a7c6-0133-63e0-5a0bf9327500.svg)](https://github.com/YABhq/Watts)

Watts is a set of commands for quickly preparing Lumen based micro-services. With single commands create full API based CRUDS with simple service layer structures.

**Author(s):**
* [Matt Lantz](https://github.com/mlantz) ([@mattylantz](http://twitter.com/mattylantz), matt at yabhq dot com)

## Requirements

1. PHP 5.5.9+
2. OpenSSL
3. Laravel 5.1+

### Composer
Start a new Laravel project:
```php
composer create-project laravel/lumen your-project-name
```

Then run the following to add Watts
```php
composer require "yab/watts"
```

### Providers
Add this to the `bootsrap/app.php` in the service providers array:
```php
Yab\Watts\WattsProvider::class
```

### Uncomment!
Taylor Otwell has very kindly left the `bootstrap/app.php` with a handful of parts commented out, which can be easily uncommented. Doing so will enable the authentication layer of Lumen. For more information click on the documentation link below.

Some of the things you will want to uncomment are:
```php
$app->withFacades();
$app->withEloquent();

$app->routeMiddleware([
    'auth' => App\Http\Middleware\Authenticate::class,
]);

$app->register(App\Providers\AppServiceProvider::class);
$app->register(App\Providers\AuthServiceProvider::class);
$app->register(App\Providers\EventServiceProvider::class);
```

You can test run with an existing database using the standard User table structure. All you would need to do is add an `api_token` column to the user table. Or, you could switch it for the suggestion provided by the `watts:generate` command. Either way you'll hit the ground running!

----

## Lumen Documentation
Please consult the documentation here: [http://lumen.laracogs.com/docs](http://lumen.laracogs.com/docs)

## Commands
The console commands provided by Watts are as follows:

### api
----
The api command will provide a unique API_KEY which can be used for authenticating API calls. This is particularily useful for making anonymous micro-service apps.

```php
php artisan watts:api
```

### prepare
----
The prepare action will prepare you micro-service to have a test database connection and allow functionality of the unit tests generated by the CRUD and TABLE CRUD.

```php
php artisan watts:prepare
```

##### crud
The CRUD will generate a Controller, Service, Repository, Model, Migration and some unit tests for the table specified in your command. You can specify the schema or modify that later if you want.

```php
php artisan watts:crud {table} {--migration} {--schema=}
```

##### table-crud
The table CRUD will review the table in your database and build a CRUD around it. Making it very easy to migrate a task to a micro-service.

```php
php artisan watts:table-crud {table} {--migration}
```

## License
Watts is open-sourced software licensed under the [MIT license](http://opensource.org/licenses/MIT)

### Bug Reporting and Feature Requests
Please add as many details as possible regarding submission of issues and feature requests

### Disclaimer
THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.