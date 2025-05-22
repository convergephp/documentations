---
title: Code Frame
description: An expandable code display component with syntax highlighting, filename headers, and collapsible functionality.
category: Components
author: Converge UI
---

# Code Frame

The Code Frame component provides an elegant way to display code snippets with syntax highlighting, filename headers, and expandable/collapsible functionality. Perfect for documentation, tutorials, and code examples.

## Overview

Ideal for:
- Documentation with code examples
- Tutorial content with expandable code blocks
- File previews with syntax highlighting
- Interactive code demonstrations

## Basic Usage

@blade
<x-converge::code.frame filename="welcome.blade.php" language="php">
```php
namespace App\Http\Controllers;

use Illuminate\Http\Request;

class WelcomeController extends Controller
{
    public function index()
    {
        return view('welcome', [
            'title' => 'Welcome to Converge UI',
            'message' => 'Build beautiful documentation with ease.'
        ]);
    }
}
```
</x-converge::code.frame>
@endblade

```php
@blade
<x-converge::code.frame filename="welcome.blade.php" language="php">
```php
namespace App\Http\Controllers;

    use Illuminate\Http\Request;

    class WelcomeController extends Controller
    {
        public function index()
        {
            return view('welcome', [
                'title' => 'Welcome to Converge UI',
                'message' => 'Build beautiful documentation with ease.'
            ]);
        }
    }```
</x-converge::code.frame>
@endblade
```

## Advanced Usage

@blade
<x-converge::code.frame
    filename="database/migrations/create_users_table.php"
    language="php"
    :expandable="true"
    initial-height="150px"
    min-expanded-height="400px">
```php
use Illuminate\Database\Migrations\Migration;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Support\Facades\Schema;

return new class extends Migration
{
    public function up(): void
    {
        Schema::create('users', function (Blueprint $table) {
            $table->id();
            $table->string('name');
            $table->string('email')->unique();
            $table->timestamp('email_verified_at')->nullable();
            $table->string('password');
            $table->rememberToken();
            $table->timestamps();
        });
    }

    public function down(): void
    {
        Schema::dropIfExists('users');
    }
};
```
</x-converge::code.frame>
@endblade

## Non-Expandable Code

@blade
<x-converge::code.frame
    filename="config/app.php"
    language="php"
    :expandable="false">
```php
return [
    'name' => env('APP_NAME', 'Laravel'),
    'env' => env('APP_ENV', 'production'),
    'debug' => (bool) env('APP_DEBUG', false),
    'url' => env('APP_URL', 'http://localhost'),
];
```
</x-converge::code.frame>
@endblade

## Props

| Name | Type | Default | Required | Description |
|------|------|---------|----------|-------------|
| `filename` | `string` | - | Yes | File name displayed in the header |
| `language` | `string` | `'php'` | No | Programming language for syntax highlighting |
| `expandable` | `boolean` | `true` | No | Whether the code frame can be expanded/collapsed |
| `initialHeight` | `string` | `'100px'` | No | Height when collapsed (expandable mode) |
| `minExpandedHeight` | `string` | `'300px'` | No | Minimum height when expanded |
