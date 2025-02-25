As Laravel follows [Semantic Versioning](https://semver.org/) and it has it's major framework releases come to light of version 12.x at 24th February. Let’s take a quick look at what this version offers and come with new features and improvements. 

#### A) Caution! When Using Named Arguments in Laravel:
Laravel's backward compatibility guidelines do not cover **named arguments**. This means the Laravel team may rename function arguments in future updates to improve the codebase. Therefore, when using named arguments in Laravel, you should be cautious and understand that parameter names may change in future versions.

**Example:**  

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
> **Version 11**
> PHP support version (8.2 - 8.4)    
> Laravel will fix bugs untill September 3rd, 2025    
> Laravel will provide security fixes untill March 12th, 2026    

**Version 12.x**

PHP support version (8.2 - 8.4) 
Laravel will fix bugs untill August 13th, 2026 
Laravel will provide security fixes untill February 24th, 2027 

#### C) WorkOS AuthKit:
Laravel included [WorkOS AuthKit](https://authkit.com/) for user authentication which offers social authentication, passkeys, and SSO support to it's new releases starter kits for React, Vue, and Livewire. 

Many, including myself, may find it surprising that why has 'WorkOS AuthKit' been added in Laravel 12.x despite the presence of 'Socialite'? Well, Let's take a look at the key differences between these two, which will probably help us understand the reasons why Laravel included this feature in 12.x version. 

**i) WorkOS AuthKit vs Laravel Socialite: Key Differences:**

**Laravel Socialite** and **WorkOS AuthKit** both provide authentication solutions, but they are designed for different use cases. Here's a breakdown of what they are and how they differ:


**WorkOS AuthKit**

WorkOS AuthKit is a new authentication solution introduced in Laravel 12's starter kits (React, Vue, Livewire). It provides:
✔ Enterprise authentication out of the box.
✔ Social login (Google, Microsoft, etc.).
✔ Passkeys (passwordless authentication).
✔ Single Sign-On (SSO) for corporate users.

It’s integrated into Laravel’s starter kits, making it easier to implement authentication without additional setup.

    
**Laravel Socialite**

Socialite is Laravel’s existing package for OAuth-based authentication. It allows authentication via:
✔ Google
✔ Facebook
✔ GitHub
✔ Twitter
✔ Other OAuth providers

It’s developer-friendly but requires manual setup, including registering OAuth credentials, handling callbacks, and storing user data.


**ii) When to Use Which?**

Use WorkOS AuthKit if you're building an app with Laravel 12 starter kits (React, Vue, Livewire) and need enterprise authentication, SSO, or passkeys.  
Use Laravel Socialite if you need OAuth-based login (Google, Facebook, GitHub, etc.) but don't require SSO or passkeys. 

Laravel **Socialite** is great for basic social logins, while **WorkOS AuthKit** is a more advanced authentication solution with enterprise features. Laravel 12 does not replace Socialite but provides WorkOS AuthKit as an alternative for applications needing SSO, passkeys, or enterprise authentication. 

