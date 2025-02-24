# Laravel 12.x New Features and Improvements
As Laravel follows [Semantic Versioning](https://semver.org/) and it has it's major framework releases come to light of version 12.x at 24th February. Let’s take a quick look at what this version offers and comes with new features and improvements. 

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
**Version 11**

	PHP support version (8.2 - 8.4)
	Laravel will fix bugs untill September 3rd, 2025
	Laravel will provide security fixes untill March 12th, 2026

**Version 12.x**

	PHP support version (8.2 - 8.4)
	Laravel will fix bugs untill August 13th, 2026
	Laravel will provide security fixes untill February 24th, 2027



