####l_rsc
```php
    /*!

    * \class       $1

    *

    * \author      ${3:`!v g:snips_author`}

    * \date        `!v strftime('%d-%m-%y')`

    */



    class ${1:`!v expand('%:t:r')`} extends ${2:BaseController} {

        function __construct() {

        }

        

        public function index() {

        }

        

        public function create() {

        }

        

        public function store() {

        }

        

        public function show($id) {

        }

        

        public function edit($id) {

        }

        

        public function update($id) {

        }

        

        public function destroy($id) {

        }

    }
```
####l_ssp
```php
    /*!

    * \namespace   $1

    * \class       $2

    *

    * \author      ${3:`!v g:snips_author`}

    * \date        `!v strftime('%d-%m-%y')`

    */



    namespace ${1:Services};



    use Illuminate\Support\ServiceProvider;



    class ${2:`!v expand('%:t:r')`} extends ServiceProvider {

        

        public function register() {

            $this->app->bind('${4}Service', function ($app) {

                return new ${5}(

                    $app->make('Repositories\\${6}Interface')

                );

            });

        }

    }
```
####l_rsp
```php
    /*!

    * \namespace   $2

    * \class       $3

    *

    * \author      ${4:`!v g:snips_author`}

    * \date        `!v strftime('%d-%m-%y')`

    */



    namespace ${2:Repositories\\${1:}};



    use Entities\\$1;

    use $2\\$1Repository;

    use Illuminate\Support\ServiceProvider;



    class ${3:`!v expand('%:t:r')`} extends ServiceProvider {

        /*!

        * \var     defer

        * \brief   Defer service

        */

        protected $defer = ${5:true};



        public function register() {

                $this->app->bind('$2\\$1Interface', function($app) {

                        return new $1Repository(new $1());

                });

        }



        /*!

        * \brief   If $defer == true need this fn

        */ 

        public function provides() {

                return ['$2\\$1Interface'];

        }

    }
```
####l_md
```php
    /*!

    * \namespace   $1

    * \class       $2

    *

    * \author      ${3:`!v g:snips_author`}

    * \date        `!v strftime('%d-%m-%y')`

    */



    namespace ${1:Entities};



    class ${2:`!v expand('%:t:r')`} extends \Eloquent {

        protected $table   = '${4:`!p snip.rv = t[2].lower()`}';



        public $timestamps = ${5:false};



        protected $hidden  = array(${6});



        protected $guarded = array(${7:'id'});

    }
```
####l_ar
```php
    /*!

    * \namespace   $1

    * \class       $2

    * \implements  $3

    *

    * \author      ${4:`!v g:snips_author`}

    * \date        `!v strftime('%d-%m-%y')`

    */



    namespace ${1:Repositories};



    use Illuminate\Database\Eloquent\Model;



    abstract class ${2:`!v expand('%:t:r')`} implements ${3:BaseRepositoryInterface} {

        protected $model;



        /*!

        * \fn      __construct

        *

        * \brief   Take the model

        */



        public function __construct(Model $model) {

                $this->model = $model;

        }



        /*!

        * \fn      all

        *

        * \return  Illuminate\Database\Eloquent\Collection

        */

        public function all($columns = array('*')) {

                return $this->model->all()->toArray();

        }



        /*!

        * \fn      create

        *

        * \return  Illuminate\Database\Eloquent\Model

        */

        public function create(array $attributes) {

                return $this->model->create($attributes);

        }



        /*!

        * \fn      destroy

        *

        * \return  int

        */

        public function destroy($ids) {

                return $this->model->destroy($ids);

        }



        /*!

        * \fn      find

        *

        * \return  mixed

        */

        public function find($id, $columns = array('*')) {

            return $this->model->find($id, $columns);

        }

    }


```
####l_r
```php
    /*!

    * \namespace   $1

    * \class       $3

    * \implements  $4

    *

    * \author      ${5:`!v g:snips_author`}

    * \date        `!v strftime('%d-%m-%y')`

    */



    namespace ${1:Repositories\\${2}};



    class ${3:`!v expand('%:t:r')`} extends \\${6} implements ${4:$3RepositoryInterface} {

        ${7}

    }
```
####l_s
```php
    /*!

    * \namespace $1

    * \class     $2

    *

    * \author    ${6:`!v g:snips_author`}

    * \date      `!v strftime('%d-%m-%y')`

    */



    namespace Services\\${1};



    use ${3:Repositories\\${4:Interface}};



    class ${2:`!v expand('%:t:r')`} {

        protected $${5:repo};



        /*!

        * \fn      __construct

        */

        public function __construct($4 $repo) {

            $this->$5 = $repo;

        }

    }
```