<h1>Route Definitions
</h1>

<h1>Bacis rotute</h1>
<pre>



// routes/web.php
Route::get('/', function () {
return 'Hello, World!';
});

</pre>
<h1>Sample website route here</h1>
<pre>
    Route::get('/', function () {
        return view('welcome');
        });
        Route::get('about', function () {
        return view('about');
        });
        Route::get('products', function () {
        return view('products');
        });
        Route::get('services', function () {
        return view('services');
        });
</pre>
<h1>Type of route here / rotuer verbs</h1>
<pre>


    Route::get('/', function () {
        return 'Hello, World!';
        });
        Route::post('/', function () {});
        Route::put('/', function () {});
        Route::delete('/', function () {});
        Route::any('/', function () {});
        Route::match(['get', 'post'], '/', function () {});
    
</pre>
<h1>ROute Handling Routes or calling controller methods</h1>


<pre>
    Route::get('/', 'WelcomeController@index');
 
</pre>

<h1>Route paremanters</h1>

<pre>
    Route::get('users/{id}/friends', function ($id) {
        //
        });


        Route::get('users/{userId}/comments/{commentId}', function (
        $thisIsActuallyTheRouteId,
        $thisisReallyTheCommentId
        ) {
        //
        });
        
</pre>

<h1>Regular expression route constraints
</h1>

<pre>
    Route::get('users/{id}', function ($id) {
        //
        })->where('id', '[0-9]+');
        Route::get('users/{username}', function ($username) {
        //
        })->where('username', '[A-Za-z]+');
        Route::get('posts/{id}/{slug}', function ($id, $slug) {
        //
        })->where(['id' => '[0-9]+', 'slug' => '[A-Za-z]+']);
</pre>

<h1>Route Names</h1>
<pre>// Defining a route with name in routes/web.php:
    Route::get('members/{id}', 'MembersController@show')->name('members.show');
    // Link the route in a view using the route() helper
    <a href="<?php echo route('members.show', ['id' => 14]); ?>">
    </pre>

<h5>Rul helper</h5>
<pre>
    <a href="<?php echo url('/'); ?>">
        // outputs <a href="http://myapp.com/">
</pre>

<h1>Router Name conventions</h1>

<pre>
    Photos.index
    photots.creare
    photos.store
    photos.show 
    photos.edit 
    photos.update 
    photos.update 
    
</pre>

<!-- 2nd day -->
<h1>PASSING ROUTE PAR AMETER S TO THE ROUTE() HELPER</h1>

<p>When your route has parameters (e.g., users/{id}), you need to define those parameters when you’re using the route() helper to generate a link to the route. There are a few different ways to pass these parameters. Let’s imagine a route defined as users/{userId}/comments/{commentId}.
    If the user ID is 1 and the comment ID is 2, let’s look at a few options we have available to us:</p>

<pre>Option 1:
    route('users.comments.show', [1, 2])
    // http://myapp.com/users/1/comments/2
    Option 2:
    route('users.comments.show', ['userId' => 1, 'commentId' => 2])
    // http://myapp.com/users/1/comments/2
    Option 3:
    route('users.comments.show', ['commentId' => 2, 'userId' => 1])
    // http://myapp.com/users/1/comments/2
    Option 4:
    route('users.comments.show', ['userId' => 1, 'comme</pre>

<h1>Route group</h1>
<h3>Defining a route group</h3>
<pre>
    Route::group([], function () {
        Route::get('hello', function () {
        return 'Hello';
        });
        Route::get('world', function () {
        return 'World';
        });
        });
        
        
    </pre>
<h1>APPLYING MIDDLEWARE IN CONTROLLERS
</h1>
<h6>
    <pre>class DashboardController extends Controller
        {
        public function __construct()
        {
        $this->middleware('auth');
        $this->middleware('admin-auth')
        ->only('admin');
        $this->middleware('team-member')
        ->except('admin');
        }
        }
        </pre>
</h6>

<h1>Path Prefixes</h1>
<p>If you have a group of routes that share a segment of their path — for example, if your site’s API is prefixed with /api — you can use route groups to simplify this structure</p>
<h6>
    <pre>Route::group(['prefix' => 'api'], function () {
        Route::get('/', function () {
        // Handles the path /api
        });
        Route::get('users', function () {
        // Handles the path /api/users
        });
        });
        </pre>
</h6>

<h1>Subdomain Routing</h1>
<p>Subdomain routing is the same as route prefixing, but it’s scoped by subdomain instead of route prefix. There are two primary uses for this. First, you may want to present different sections of the application (or entirely different applications) to different
    subdomains. Example 3-13 shows how you can achieve this.
</p>
<h6>
    <pre>
        Route::group(['domain' => 'api.myapp.com'], function () {
            Route::get('/', function () {
            //
            });
            });
    </pre>
</h6>
<h2> Parameterized subdomain routing</h2>


<h6>
    <pre>
        Route::group(['domain' => '{account}.myapp.com'], function () {
            Route::get('/', function ($account) {
            //
            });
            Route::get('users/{id}', function ($account, $id) {
            //
            });
            });
    </pre>
</h6>
<h1>Route group name prefixes
</h1>

<h6>
    <pre>
        Route::group(['as' => 'users.', 'prefix' => 'users'], function () {
            Route::group(['as' => 'comments.', 'prefix' => 'comments'], function () {
            // Route name will be users.comments.show
            Route::get('{id}', function () {
            //
            })->name('show');
            });
            });
    </pre>
</h6>

<h1 class="text-center "> Chapter -4 Views</h1>
<h1>Load views</h1>
<h1>THREE WAYS TO LOAD A VIEW()</h1>
<h2>Simple view() usage</h2>
<h6>
    <pre>Route::get('/', function () {
        return view('home');
        });</pre>
</h6>
<h1> Passing variables to views</h1>
<h6>
    <pre>
        Route::get('tasks', function () {
            return view('tasks.index')
            ->with('tasks', Task::all());
            });
            
    </pre>
</h6>
<h1>Using View Composers to Share Variables with Every View

</h1>
<h6>
    <pre>
        view()->share('variableName', 'variableValue');
    </pre>
</h6>

<h1>contorollers</h1>
<img src="https://i.stack.imgur.com/4qglC.png" alt="">
