
Need to override method `registerErrorViewPaths` in your `App\Exceptions\Handler` class.
```php
    protected function registerErrorViewPaths()
    {
        $paths = collect(config('view.paths'));

        View::addNamespace('errors', $paths->map(function ($path) {
            return "{$path}/errors";
        })->push(dirname((new \ReflectionClass(\Illuminate\Foundation\Exceptions\Handler::class))->getFileName()).'/views')->all());
    }
```
