# Laravel Lab

## Controllers & Requests
`app\Http\Controllers\`

`$ php artisan make:controller ControllerFolder\ControllerName`

### Basic global functions

    env(global variable);
    response()->json(['teste' => 'teste']);
    response()->download($pathToFile);
    response()->file($pathToFile);
	redirect('url');
	route('name of the route');
	dd('what'); // var_dump() & die()
### Requests
```
use  Illuminate\Http\Request;

public function test(Request $request){
	dd($request->all());
}
```
### Request validation
[Validation Rules](https://laravel.com/docs/8.x/validation#available-validation-rules)

    use  Illuminate\Http\Request;
    $validated = $request->validate([
    'email'  =>  'required|exists:user',    
    'password'  =>  'required'    
    ]);
    
    if (!Auth::attempt($validated)) {    
	    return  redirect('/register/error');    
    }   
    return  redirect('/register/success');
