# Laravel 12.x New Features and Improvements
As Laravel follows [Semantic Versioning](https://semver.org/) and it has it's major framework releases come to light of version 12.x at 24th February. Let’s take a quick look at what this version offers and comes with new features and improvements. 

#### A) Caution! When Using Named Arguments in Laravel:
Laravel's backward compatibility guidelines do not cover named arguments. This means the Laravel team may rename function arguments in future updates to improve the codebase. Therefore, when using named arguments in Laravel, you should be cautious and understand that parameter names may change in future versions.

###### Example:
    Laravel may change function argument names in future releases.  
    in Laravel 12, the `response()->json()` function may look like this:
    ```php
          public function json(array $data, int $status = 200)

