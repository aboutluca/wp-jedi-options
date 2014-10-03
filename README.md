wp-jedi-options
===============

wpJediOptions is a php class that permit to create an options page in wordpress with multiple type of input by passing an array.

What you have to do to make it works is include it in functions.php in your theme and then add some code in the same file.


Utilization
==

        <?php        
        $options = new wpJediOptions(
        
                Array(
                
                    "page_title" => "Opzioni jedi",
                    "page_menu_title" => "Opzioni",
                    "page_note" => "Note that the fields must be compiled for each language",
                    "page_slug" => 'jedi-setting',
                    "options_name" => 'jedi_option',
                    "options_group" => 'jedi_option_group',
                    "options" =>  Array(
                    
                        "field_1" => Array(
                            "label" => "Title 1",
                            "name" => "title_1",
                            "type" => "text",
                            "description" => "Insert the title",
                            "language" =>ICL_LANGUAGE_CODE,
                        ),
                        
                        "field_2" => Array(
                            "label" => "Select trough multiple value",
                            "name" => "multiple_value",
                            "type" => "select",
                            "description" => "Select between options",
                            "options" => Array(
                                "1" => "Value 1",
                                "2" => "Value 2",
                                "3" => "Value 3"
                            )
                        ),
                        
                        "field_3" => Array(
                            "label" => "Example of rich text field",
                            "name" => "richtext_1",
                            "type" => "richtext",
                            "description" => "Insert the richtext",
                        ),
                        
                        "field_4" => Array(
                            "label" => "Example of image field",
                            "name" => "image_1",
                            "type" => "image",
                            "description" => "Choose image to upload"
                        ),
                        
                        "field_5" => Array(
                            "label" => "Position 1",
                            "name" => "mappa1",
                            "type" => "map",
                            "description" => "Search the zone by the geocode or drag the marker where you want"
                        ),
                        
                        "field_6" => Array(
                            "label" => "Checkbox 1",
                            "name" => "checkbox_example",
                            "type" => "checkbox",
                            "description" => "Check or not check"
                        )
                        
                        "field_6" => Array(
                            "label" => "Colorpicker 1",
                            "name" => "colorpicker_example",
                            "type" => "colorpicker",
                            "description" => "Choose you preferite color"
                        )
                        
                    )
                )
        
        );
        
        /* Retrive one multilanguage option: */
        $option_title = JediOptions::get_option('jedi_option', 'title_1'.strtolower(ICL_LANGUAGE_CODE));
        
        /* Retrive an image ID (when you add image field automatically the library save ID for you): */
        $option_image = JediOptions::get_option('jedi_option', 'image_1_id');
        
        /* Retrive one normal option: */
        $option_richtext = JediOptions::get_option('jedi_option', 'richtext_1');
        
        ?>

Constructior Params
==

"page_title" => Set the title for the admin Page created (string)

"page_menu_title" => Set the title for the page in the admin menu (string)

"page_note" => Set the page description under the title in the page, helpful to explain to user (string)

"page_slug" => Set the slug in the url for the page only _ and - are accepted as special char (string)

"options_name" => The name for your options (string)

"options_group" => The name for your optionsgroup (string)

"options" => The array of options you would create (array)

Options Params
==

"label" => The label of the input (string)

"name" => The input name (special char only - or _ ) (string)

"description" => The description helpful for the user (string)

"type" => The option type (text/richtext/select/map/image/checkbox/colorpicker) (string)

"language" => Optional, if you pass a variable you can have a multiple language field (string)

"options" => Optional, if you use a "select" type you can pass an array of value. The key of the array is the value, the value is the label

"sanitize" => TODO





        
