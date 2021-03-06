# SPA(Single Page Application) With React js and Wordpress REST API

Single Page Application to create todo list using Wordpress REST API and React.

## Create Posts for todo lists in Wordpress
I have created custom post type named todo list and also created new template file. In this template file, I created custom form to display it in Wordpress front end for data insertion. You can add your task name and it's description there. I am using default twentynineteen theme provided by wordpress you can also use your custom theme.
![Screenshot from 2019-12-30 10-01-23](https://user-images.githubusercontent.com/46484569/71568241-b9234900-2aeb-11ea-83a0-abf98490f21b.png)



## Create custom endpoint in REST API
You need to create custom endpoint for your custom post type to access your posts data. So, open your functions.php file and add below code in it.
``` 
function  sections_endpoint( $request_data ) {
    $args = array(
        'post_type' => 'todo-list',
        'posts_per_page'=>-1, 
        'numberposts'=>-1
    );
    $posts = get_posts($args);
    foreach ($posts as $key => $post) {
        $posts[$key]->post_title;
        $posts[$key]->post_content;
    }
    return  $posts;
}
add_action( 'rest_api_init', function () {
    register_rest_route( 'sections/v1', '/todo-list/', array(
        'methods' => 'GET',
        'callback' => 'sections_endpoint'
    ));
});
 ```

Now open your newly created custom endpoint (like 'http://localhost/wordpress/wp-json/sections/v1/todo-list') in browser and you can see your all the custom posts data there. You need to fetch all of these posts in your react application. Let's move on react.

## Create React Applicatipon
Now, create react app with following command.<br>
``` npx create-react-app your-project-name ```<br>
or<br>
``` npm create-react-app your-project-name ```<br>
After running above command, new folder will be created in your system with your selected name. You also need to install one another important package named axios. To install it, run command ``` npm install axios ```. You can get more information [here](https://www.npmjs.com/package/axios)

## It's time to unlock the power of React
After installing react app, open app.js file in your favourite code editor. you can also create your own js file and import it in your index.js file. open your js file and add code for accessing the todo lists that you have created using wordpress. You can check code in my app.js file.

Now, open http://localhost:3000 in any browser to view your todo list.

![Screenshot from 2019-12-30 10-05-45](https://user-images.githubusercontent.com/46484569/71568333-71e98800-2aec-11ea-87c5-ac202a59559a.png)

## Usefull Blog
[Single Page Web Application](https://medium.com/@brijeshdhanani/how-to-create-a-single-page-application-spa-with-react-js-and-wordpress-rest-api-9a53a9698579)

********Please Follow Me on Github********

Thanks!!!!
