As Laravel follows [Semantic Versioning](https://semver.org/) and it has it's major framework releases come to light of version 12.x at 24th February. Let’s take a quick look at what this version offers and come with new features and improvements. 

#### A) Caution! When Using Named Arguments in Laravel:
Laravel's backward compatibility guidelines do not cover **named arguments**. This means the Laravel team may rename function arguments in future updates to improve the codebase. Therefore, when using named arguments in Laravel, you should be cautious and understand that parameter names may change in future versions.

###### Example: 

Laravel may change function argument names in future releases.  
In Laravel 12, the `response()->json()` function may look like this:
```php
public function json(array $data, int $status = 200)
```

But in Laravel 13, it could be changed to:
```php
public function json(array $responseBody, int $httpStatusCode = 200)
```

Now, the following code that worked in Laravel 12 will break in Laravel 13:
```php
return response()->json(data: ['message' => 'Success'], status: 200);
```
Since `data:` and `status:` have been renamed, **Laravel will not recognize these arguments** and will throw an **error**.

#### B) Support Policies

> ***Version 11*** 
> PHP support version (8.2 - 8.4)      
> Laravel will fix bugs untill September 3rd, 2025      
> Laravel will provide security fixes untill March 12th, 2026      


> ***Version 12.x*** 
> PHP support version (8.2 - 8.4)     
> Laravel will fix bugs untill August 13th, 2026     
> Laravel will provide security fixes untill February 24th, 2027   


#### C) WorkOS AuthKit:
Laravel included [WorkOS AuthKit](https://authkit.com/) for user authentication which offers social authentication, passkeys, and SSO support to it's new releases starter kits for React, Vue, and Livewire. **WorkOS offers free authentication**. 

Many, including myself, may find it surprising that why has **'WorkOS AuthKit'** been added in Laravel 12.x despite the presence of **'Socialite'**? Well, Let's take a look at the key differences between these two, which will probably help us understand the reasons why Laravel included this feature in 12.x version. 

###### i) WorkOS AuthKit vs Laravel Socialite: Key Differences:

**Laravel Socialite** and **WorkOS AuthKit** both provide authentication solutions, but they are designed for different use cases. Here's a breakdown of what they are and how they differ:


> ***WorkOS AuthKit:*** 
> WorkOS AuthKit is a new authentication solution introduced in Laravel 12's starter kits (React, Vue, Livewire). It provides:      
> ✔ Enterprise authentication out of the box.    
> ✔ Social login (Google, Microsoft, etc.).    
> ✔ Passkeys (passwordless authentication).    
> ✔ Single Sign-On (SSO) for corporate users.    
> It’s integrated into Laravel’s starter kits, making it easier to implement authentication without additional setup.  

    
> ***Laravel Socialite:*** 
> Socialite is Laravel’s existing package for OAuth-based authentication. It allows authentication via:  
> ✔ Google  
> ✔ Facebook  
> ✔ GitHub  
> ✔ Twitter  
> ✔ Other OAuth providers  
> It’s developer-friendly but requires manual setup, including registering OAuth credentials, handling callbacks, and storing user data.  


###### ii) When to Use Which? 
> ***WorkOS AuthKit:*** 
> Use WorkOS AuthKit if you're building an app with Laravel 12 starter kits (React, Vue, Livewire) and need enterprise authentication, SSO, or passkeys.            

> ***Laravel Socialite:*** 
> Use Laravel Socialite if you need OAuth-based login (Google, Facebook, GitHub, etc.) but don't require SSO or passkeys.         

Laravel **Socialite** is great for basic social logins, while **WorkOS AuthKit** is a more advanced authentication solution with enterprise features. Laravel 12 does not replace Socialite but provides WorkOS AuthKit as an alternative for applications needing SSO, passkeys, or enterprise authentication.  


#### D) Minimal Breaking Changes:
According their doc Laravel mainly focuses during the release cycle are:

> ✔ Minimizing breaking changes.  
> ✔ Do not break existing applications.  
> ✔ Minor "maintenance release" in order to upgrade existing dependencies.  
> ✔ May upgrade to Laravel 12 without changing any application code.


#### E) Laravel 12 introduces new application starter kits:
Laravel 12 introduces new application starter kits for React, Vue, and Livewire. Let's see what are they: 
 
###### Starter Kit for React

> 🔹 The React starter kit utilize [Inertia 2](https://inertiajs.com/), TypeScript, [shadcn/ui](https://ui.shadcn.com/), and Tailwind    
> 🔹 It's Utilize Laravel's built-in authentication system to offer login, registration, password reset, email verification, and more    
> 🔹 introducing a [WorkOS AuthKit](https://authkit.com/) powered variant offering social authentication, passkeys, and SSO support.

###### Starter Kit for Vue

> 🔹 The Vue starter kit utilize [Inertia 2](https://inertiajs.com/), TypeScript, [shadcn/ui](https://ui.shadcn.com/), and Tailwind  
> 🔹 It's Utilize Laravel's built-in authentication system to offer login, registration, password reset, email verification, and more  
> 🔹 introducing a [WorkOS AuthKit](https://authkit.com/) powered variant offering social authentication, passkeys, and SSO support.

###### Starter Kit for Livewire

> 🔹 Livewire starter kits utilizes the Tailwind based [Flux UI](https://fluxui.dev/) component library and Laravel [Volt](https://github.com/livewire/volt)  
> 🔹 It's Utilize Laravel's built-in authentication system to offer login, registration, password reset, email verification, and more  
> 🔹 introducing a [WorkOS AuthKit](https://authkit.com/) powered variant offering social authentication, passkeys, and SSO support.

###### There are nice official doc of Laravel 12 new application starter kits:     
* [New Application Starter Kits Official Docs](https://laravel.com/docs/12.x/starter-kits)      
* [Examples, Live Preview, Features, Deployment, Laravel Cloud and More](https://laravel.com/starter-kits)    

#### F) Laravel Breeze and Laravel Jetstream will no longer receive additional updates:  
With the introduction of Laravel's new application starter kits, **Laravel Breeze** and **Laravel Jetstream** will no longer receive additional updates.   

#### G) Upgrading from 11.x:  
When upgrading to a new version, it's crucial to consider potential breaking changes that may impact the application. Laravel strives to document all such changes, though only a few may directly affect applications, as some modifications occur in less commonly used parts of the framework. Additionally, Laravel categorizes these changes based on their impact—high, medium, or low. Let’s explore these changes based on Laravel's recommendations for a smooth transition.   

###### i) Significant Changes:

The following are the high impact changes that need while upgrading from version 11.x:

> ***Updating Dependencies:*** 
> We should update the following dependencies in the application's composer.json file while upgrading from version 11.x:      
> * laravel/framework to ^12.0.    
> * phpunit/phpunit to ^11.0.    
> * pestphp/pest to ^3.0.

> ***Updating Installer While Using CLI Tool:*** 
> If we want to create new Laravel application using Laravel installer CLI tool we should update the installer installation to be compatible with Laravel 12.x and the new Laravel starter kits while upgrading from version 11.x:      
> * updated installer via composer > `composer global update laravel/installer`    
> * updated installer via php.new (run as administrator) > `Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://php.new/install/windows/8.4'))`   
> * updated installer using [Laravel Herd's](https://herd.laravel.com/) > update Herd installation to the latest release.


###### ii) Medium Impact Changes:
***Models and UUIDv7:*** 

Laravel says, **Likelihood Of Impact: Medium** about **Models and UUIDv7**. Before that let's firstly try to undestand what is this actually!

Laravel supports multiple **UUID** versions, primarily, **UUIDv4** and **UUIDv7**. A **UUID** (Universally Unique Identifier) is a 128-bit identifier used to uniquely identify records in a database. **UUIDv7** was introduced to improve performance and ordering in databases by using timestamp-based sorting. Unlike auto-incrementing IDs, **UUIDs:**

🔹 Are globally unique (no duplicates even across different databases).  
🔹 Do not expose record count (for security).  
🔹 Work well in distributed systems (no risk of ID conflicts).  
🔹 **UUIDv4** → Fully random values.   
🔹 **UUIDv7** → Ordered, time-based values (better for database indexing).  


**Laravel 12.x Upgrade: What Changed with UUIDs?**     
> **Before Laravel 12.x (Laravel 11.x and Earlier):** 
> **HasUuids** → Used UUIDv4 (random UUIDs).  
> **HasVersion7Uuids** → Used UUIDv7 (ordered UUIDs).  

> **In Laravel 12.x:**
> **HasUuids** → Now defaults to UUIDv7 instead of UUIDv4.  
> **HasVersion7Uuids** → Removed (not needed anymore).  
> New **HasVersion4Uuids** trait → If you still want UUIDv4, use this instead.


**Example Before Laravel 12 (Using UUIDv4 by Default):** 
```php
    use Illuminate\Database\Eloquent\Concerns\HasUuids;
    
    class User extends Model {
        use HasUuids; // Previously, this used UUIDv4
    }
```

**Example in Laravel 12 (Now Uses UUIDv7 by Default):** 
```php
    use Illuminate\Database\Eloquent\Concerns\HasUuids;
    
    class User extends Model {
        use HasUuids; // Now this generates UUIDv7
    }
```

**If We Want to Keep Using UUIDv4 in Laravel 12:** 
```php
    use Illuminate\Database\Eloquent\Concerns\HasVersion4Uuids as HasUuids;
    
    class User extends Model {
        use HasUuids; // This keeps using UUIDv4 instead of UUIDv7
    }
```

###### iii) Minimal Impact Changes:

The following are the minimal impact changes that need while upgrading from version 11.x:

***(A) Updating Dependencies*** 

> **Carbon 3**
> All **Laravel 12** applications now require **Carbon 3.x**. Upgrading to **Carbon 3.x** in **Laravel 12** is straightforward. **Laravel 12** requires **Carbon 3.x** by default, so if you're using **Laravel 12**, it should already be installed. However, if you need to upgrade from **Carbon 2.x**, follow these steps.:<br /><br /> 
> **1. Check Your Current Carbon Version :** Run the following command in your Laravel project to see the installed version:   
> `composer show nesbot/carbon`         
> If you see Carbon 2.x, you'll need to upgrade.<br /><br />
> **2. Upgrade to Carbon 3.x :** Run the following command:      
> `composer require nesbot/carbon:^3.0 --with-all-dependencies`           
> This updates Carbon to version 3.x<br /><br />
> **3. Verify the Update :** Check again with:      
> `composer show nesbot/carbon`           
> You should see something like this: versions: `*3.x.x*`<br /><br />


***(B) SVGs Image Validation***     
Before **Laravel 12** image validation rule allowed **SVG** images by default. Now from **Laravel 12** to allow SVGs when using the image rule, we must explicitly allow them:  
```php
    use Illuminate\Validation\Rules\File;
    
    'photo' => 'required|image:allow_svg'
    
    // Or...
    'photo' => ['required', File::image(allowSvg: true)],
```

***(C) Nested Array Request Merging***     
Previously, in **Laravel 11** and earlier, calling `$request->mergeIfMissing()` with dot notation keys would not properly merge into a nested array. Instead, it would store the key as a string, rather than treating it as a nested array key.

**Example: Laravel 11 (Old Behavior):**
```php
    use Illuminate\Validation\Rules\File;
    
    'photo' => 'required|image:allow_svg'
    
    // Or...
    'photo' => ['required', File::image(allowSvg: true)],
```

**Expected Output in Laravel 11:**
`[
        'user.last_name' => 'Otwell', // Stored as a string key, not nested.
]`

**Problem:** Laravel treated `user.last_name` as a string key, not as a nested array.

**We had to manually structure the array** to avoid this issue:
```php
    $request->mergeIfMissing([
        'user' => ['last_name' => 'Otwell'],
    ]);
```

**Example: Laravel 12 (New Behavior):**
Now, Laravel 12 correctly merges dot notation keys into a nested array.

```php
    $request->mergeIfMissing([
        'user.last_name' => 'Otwell',
    ]);
```

**Expected Output in Laravel 12:**
`[
    'user' => [
        'last_name' => 'Otwell',
    ]
]`

***(D) Multi-Schema Support in Database Schema Inspection***<br />

** * Schema Inspection At a Glance:**

In **Laravel 12**, database schema inspection methods `(Schema::getTables(), Schema::getViews(), Schema::getTypes(), and Schema::getTableListing())` now return results from all database schemas by default, instead of only showing tables from the default schema.

> **Laravel 11 & Earlier (Old Behavior):**     
> * `Schema::getTables()` & similar methods only fetched tables from the default schema.    
> * If a database had multiple schemas (like in `PostgreSQL, MySQL, MariaDB`, and `SQL Server`), Laravel only returned tables from the default schema.    
> * Developers had to use custom queries to inspect tables in other schemas.

**Example in Laravel 11:**
```php
    $tables = Schema::getTables(); // Only returns tables from the default schema.
```
**Expected Output in Laravel 11:**
`['migrations', 'users', 'posts']`


> **Laravel 12 (New Behavior):** 
> Now, `Schema::getTables()`, `Schema::getViews()`, and `Schema::getTypes()` automatically return tables from all schemas.:      

**Example in Laravel 12:**
```php
    $tables = Schema::getTables();
```
**Expected Output in Laravel 12:**
`['main.migrations', 'main.users', 'blog.posts']`

Tables from all schemas are included by default!
  

