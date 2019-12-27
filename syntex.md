<h3>Route Definitions
</h3>

<h4>Bacis rotute</h4>
<pre>



// routes/web.php
Route::get('/', function () {
return 'Hello, World!';
});

</pre>
<h4>Sample website route here</h4>
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
<h4>Type of route here / rotuer verbs</h4>
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
<h4>ROute Handling Routes or calling controller methods</h4>


<pre>
    Route::get('/', 'WelcomeController@index');
 
</pre>

<h4>Route paremanters</h4>

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

<h4>Regular expression route constraints
</h4>

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

<h4>Route Names</h4>
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

<h3>Router Name conventions</h3>

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
<h4>PASSING ROUTE PAR AMETER S TO THE ROUTE() HELPER</h4>

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