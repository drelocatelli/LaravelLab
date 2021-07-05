# Laravel Lab

## Route, Views & Wildcards
`routes \ web.php`
### Basic Router

    Route::get('/', function(){
	    return view( 'welcome' );
    });
### Route with params

    Route::get('/user/{username}', function($username){
	    return view( 'users', [ 'username'=> $username ] );
    });
### Route with params & where clause

    Route::get('/user/{username}', function($username){
	    return view( 'users', [ 'username'=> $username ] );
    })->where('username', '[A-za-Z]');
### Route compact
This will create key-value variable.

     Route::get('/user/{username}', function($username){
	    return view( 'users', compact($username) );
    })->where('username', '[A-za-Z]');
### Route methods
     Route::match(['get','post'],'/', function(){
    	    return view( 'welcome' );
        });
### Route prefix group & controllers
    Route::group(['prefix' => 'user'], function(){
	    $controller = UserController::class;
	    Route::match(['get','post'],'/', [$controller, 'index']);
	    Route::get('/edit', [$controller, 'edit.user']);
	});
### Route form

    Route::post('/form', [$controller, 'form'])->name('form-handle');
    
    <form method="{{  route('form-handle')  }}">
    @csrf
