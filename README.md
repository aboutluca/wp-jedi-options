wp-jedi-options
===============

wpJediOptions is a **php class for wordpress** that permit to create an options page with multiple type of input by passing an array. The library require Wordpress 3.5 or later. The inputs types are pre built using wordpress's api. They are:
* Richtext editor
* Simple Text
* Select input
* Image upload
* Add a marker on a map using google map api. (Geocode search and draggable marker)
* Simple checkbox
* Colorpicker

#### Tutorial
[Read the tutorial!](http://www.aboutluca.com/2014/11/13/create-theme-options-page-for-wordpress/)

#### Installation
What you have to do to make it works is:
* Copy the WpJediOptions.php in your theme directory
* Include it in your functions.php
* Build the options as you want.

#### Full example

        <?php    
        
        require_once( get_template_directory() . '/wpJediOptions.php' );
        
        $page_options = new wpJediOptions(

            Array(

                "page_title" => "Jedi options",
                "page_menu_title" => "Options",
                "page_note" => "Note that the fields must be compiled for each language",
                "page_slug" => "jedi-setting",
                "options_name" => "jedi_option",
                "options_group" => "jedi_option_group",
                "options_parent_slug" => "",
                "options" =>  Array(
                    
                    "field_1" => Array(
                        "label" => "Title 1",
                        "name" => "title_1",
                        "type" => "text",
                        "description" => "Insert the title",
                        "language" =>ICL_LANGUAGE_CODE
                    ),
                    
                    "field_2" => Array(
                        "label" => "Example of rich text field",
                        "description" => "Insert the richtext",
                        "type" => "richtext",
                        "name" => "richtext_1",
                        "language" => ICL_LANGUAGE_CODE
                    ),
                    
                    "field_3" => Array(
                        "label" => "Select trough multiple value",
                        "name" => "multiple_value",
                        "type" => "select",
                        "description" => "Select between options",
                        "language" =>ICL_LANGUAGE_CODE,
                        "options" => Array(
                          "1" => "Value 1",
                          "2" => "Value 2",
                          "3" => "Value 3")
                    ),
                    
                    "field_4" => Array(
                        "label" => "Example of image field",
                        "name" => "image_1",
                        "type" => "image",
                        "description" => "Choose image to upload"
                    ),
                    
                    "field_5" => Array(
                        "label" => "Colorpicker 1",
                        "name" => "colorpicker_example",
                        "type" => "colorpicker",
                        "description" => "Choose you preferite color"
                    ),
                    
                    "field_6" => Array(
                        "label" => "Checkbox 1",
                        "name" => "checkbox_example",
                        "type" => "checkbox",
                        "description" => "Check or not check"
                    ),
                    
                    "field_7" => Array(
                        "label" => "Colorpicker 1",
                        "name" => "colorpicker_example",
                        "type" => "colorpicker",
                        "description" => "Choose you preferite color"
                    )       
                )
            )
        );
        
        $sub_page_maintenance = new wpJediOptions(

                Array(

                    "page_title" => "Maintenance",
                    "page_menu_title" => "Maintenance",
                    "page_note" => "Note that this is a sub page of page Options",
                    "page_slug" => "jedi-maintenance-setting",
                    "options_name" => "jedi_option_maintenance",
                    "options_group" => "jedi_option_maintenance_group",
                    "options_parent_slug" => "jedi-setting",
                    "options" =>  Array(
                        //TODO
                    )
                )

        );
        
        /* Retrive one multilanguage option: */
        $option_title = wpJediOptions::get_option('jedi_option', 'title_1'.strtolower(ICL_LANGUAGE_CODE));
        
        /* Retrive an image ID (when you add image field automatically the library save ID for you): */
        $option_image = wpJediOptions::get_option('jedi_option', 'image_1_id');

        /* Retrive one normal option: */
        $option_richtext = wpJediOptions::get_option('jedi_option', 'richtext_1');
        
        ?>


Documentation
-------------

#### Constructor Params

"page_title" => Set the title for the admin Page created (string)

"page_menu_title" => Set the title for the page in the admin menu (string)

"page_note" => Set the page description under the title in the page, helpful to explain to user (string)

"page_slug" => Set the slug in the url for the page only _ and - are accepted as special char (string)

"options_name" => The name for your options (string)

"options_group" => The name for your optionsgroup (string)

"options" => The array of options you would create (array)

"options_parent_slug" => The slug of the parent page (optional)

#### Options Params

"label" => The label of the input (string)

"name" => The input name (special char only - or _ ) (string)

"description" => The description helpful for the user (string)

"type" => The option type (text/richtext/select/map/image/checkbox/colorpicker) (string)

"language" => Optional, if you pass a variable you can have a multiple language field (string)

"options" => Optional, if you use a "select" type you can pass an array of value. The key of the array is the value, the value is the label

"sanitize" => TODO

#### Retrive options


To retrive an option you have to use this code:

    wpJediOptions::get_option('options_name', 'single_opt_name')
    
where options_name is the name specified in the contructor and single_opt_name is "name" in options param.
If you want to retrive by language with WPML add the code below:

    wpJediOptions::get_option('options_name', 'single_opt_name'.strtolower(ICL_LANGUAGE_CODE))
    
    
If you want to retrive the image ID add "_id" to the name of you image option

    wpJediOptions::get_option('options_name', 'single_opt_name_id')



        
