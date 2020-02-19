
# WebApplication.php

Code listing for `/src/WebApplication.php`. This class is the decision-making logic for the application to decide how to respond to the HTTP Request message received by the web application.

```php
    <?php
    namespace Tudublin;
    
    class WebApplication
    {
        private $mainController;
    
        public function __construct()
        {
            $this->mainController = new MainController();
        }
    
        public function run()
        {
            $action = filter_input(INPUT_GET, 'action');
    
            switch($action) {
                case 'jokes':
                    $this->mainController->jokes();
                    break;
    
                case 'index':
                default:
                    $this->mainController->index();
            }
        }
    }
```

    