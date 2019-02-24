

//Cross-Site
header('Access-Control-Allow-Origin: *'); 
header("Access-Control-Allow-Credentials: true");
header('Access-Control-Allow-Methods: GET, PUT, POST, DELETE');
header('Access-Control-Max-Age: 1000');
header('Access-Control-Allow-Headers: Origin, Content-Type, X-Auth-Token , Authorization');



//configuration
$config = [
    'settings' => [
        'displayErrorDetails' => true,
        'database' => [
            'dbname'   => 'databasename',
            'hostname' => 'localhost',
            'password' => '',
            'username' => 'root'
        ],
    ],
];



//dependence
$container = $app->getContainer();
$container['db'] = function($c){
    $x = $c->get('settings')['database'];
    $pdo = new PDO("mysql:host={$x['hostname']};dbname={$x['dbname']}", "{$x['username']}", "{$x['password']}");
return $pdo;
};
