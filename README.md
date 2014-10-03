wp-jedi-options
===============

wpJediOptions is a Php class that permit to create an options page in wordpress with multiple type of input by passing an array.


Here a full example explains what you can do with this library:


        
        
        $options = new wpJediOptions(
        
                Array(
                
                    /* Wordpress admin Page title */
                    "page_title" => "Opzioni jedi",
                    /* Wordpress page title on the admin menu */
                    "page_menu_title" => "Opzioni",
                    /* Page description under the title */
                    "page_note" => "Note that the fields must be compiled for each language",
                    /* Page slug on the url */
                    "page_slug" => 'jedi-setting',
                    /* Options name for retrive them */
                    "options_name" => 'jedi_option',
                    /* Options name for retrive / save them */
                    "options_group" => 'jedi_option_group',
                    
                
                    /* Here the array to pass */
                    "options" =>  Array(
                    
                        /* Example of simple text */
                        "field_1" => Array(
                            /* Options label for user interface */
                            "label" => "Title 1",
                            /* Options name for retrive / save them */
                            "name" => "title_1",
                            /* Type: you can choose trough text/richtext/select/map/image/checkbox */
                            "type" => "text",
                            /* Description help the user */
                            "description" => "Insert the title",
                            /* Language: multilang ready, if you use wpml can pass ICL_LANGUAGE_CODE or a variable in other case */
                            "language" =>ICL_LANGUAGE_CODE,
                        ),
                        
                        /* Example of multiple value */
                        "field_2" => Array(
                            "label" => "Select trough multiple value",
                            "name" => "multiple_value",
                            "type" => "select",
                            "description" => "Select between options",
                            "language" =>ICL_LANGUAGE_CODE,
                            "options" => Array(
                                /* Array: The key as the value; The value as the label */
                                "1" => "Value 1",
                                "2" => "Value 2",
                                "3" => "Value 3"
                            )
                        ),
                        
                        /* Example of richtext */
                        "field_3" => Array(
                            "label" => "Example of rich text field",
                            "name" => "richtext_1",
                            "type" => "richtext",
                            "description" => "Insert the richtext",
                            "language" =>'',
                        ),
                        
                        /* Example of image */
                        "field_4" => Array(
                            "label" => "Example of image field",
                            "name" => "image_1",
                            "type" => "image",
                            "description" => "Choose image to upload",
                            "sanitize" => ""
                        ),
                        
                        /* Example of map */
                        "field_5" => Array(
                            "label" => "Position 1",
                            "name" => "mappa1",
                            "type" => "map",
                            "description" => "Search the zone by the geocode or drag the marker where you want",
                            "sanitize" => ""
                        ),
                        
                        /* Example of checkbox */
                        "field_6" => Array(
                            "label" => "Checkbox 1",
                            "name" => "checkbox_example",
                            "type" => "checkbox",
                            "description" => "Check or not check",
                            "sanitize" => ""
                        )
                        
                    )
                )
        
        );
