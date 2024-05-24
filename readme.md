TODO with TEMPLATE

```sh
    $ cp .env-sample .env
    $ npm i
    $ npm i ejs
```

* Talk about Templates & EJS Template.

* app.js
    ```js
    // TEMPLATE:
    // npm i ejs
    // https://ejs.co/
    // https://www.npmjs.com/package/ejs
    // https://github.com/mde/ejs/wiki/Using-EJS-with-Express
    app.set('view engine', 'ejs')
    // Default folder: './views'
    app.set('views', './public')
    ```
    ```js
    // Router:
    app.all('/', (req, res) => {

        // call ejs file in ./views/
        // res.render('index.ejs')
        res.render('index')

    })

    app.use('/view', require('./app/routes/todoTemplate'))
    app.use('/api', require('./app/routes/todo'))
    ```

* copy "router/todo" and rename "todoTemplate"
* copy "controller/todo" and rename "todoTemplate"

* app/routes/todoTemplate.js
    ```js
    const todoTemplate = require('../controllers/todoTemplate')

    router.route('/')
        .get(todoTemplate.list) // LIST
        .post(todoTemplate.create) // CREATE

    router.route('/:id')
        .get(todoTemplate.read) // READ
        .put(todoTemplate.update) // UPDATE
        .delete(todoTemplate.delete) // DELETE
    ```

* todoTemplate -> Controller & Router:
    * list
        * router
        * controller
            * res.render to ejs with data
    * read
        * like "list"
    * delete
        * send record to delete without template.
    * create 
        * router -> get & post
        * controller
        * Dont Forget -> app.js:
            ```js
            // Accept form-data & convert to object:
            // app.use(express.urlencoded())
            app.use(express.urlencoded({ extended: true })) // Allow array-form-elements
            ```
    * update
        * like "create"

* send error to template for errorHandler 
    * errorHandler
    * public/error.ejs