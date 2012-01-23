Installation
============

1. Add this plugin to your project as Git submodules:

       $ git submodule add git@github.com:Icepique/sfGravatarPlugin.git plugins/sfGravatarPlugin


2. Add this plugin to your ProjectConfiguration file:

       // config/ProjectConfiguration.class.php
       public function setup()
       {
         $this->enablePlugins(array(
           // ...
           'sfGravatarPlugin',
           // ...
         ));
       }
          
3. Enable the helper in your settings.yml file

       // apps/frontend/config/settings.yml
       all:
         .settings:
           # ...
           standard_helpers:  [ ... , Gravatar]

4. Create a directory named ``g_cache`` in ``web/uploads`` and add full rights to it (note: you can change the directory's name but don't forget to change it in config file).


Usage
=====

All you have to do is use the helper like this example:

    echo gravatar_image_tag('name@domain.com');

With parameters:

    echo gravatar_image_tag('name@domain.com', 140, 'G', 'Picture avatar');

Or :
    <img src="<?php echo gravatar_image('name@domain.com', 140, 'G'); ?>" />
    
You can check if an email has a gravatar (warning, slow due to curl function)

    <?php if(gravatar_has_image('name@domain.com')): ?>  
      <!-- -->
    <?php endif;?>

Available options:
    - size : the size of the avatar (default to 80px)
    - rating : is the type of content in the image (default to G)
    - default_image: the default image (default to null)

You can set some default option that are common for all of your gravatars in your app.yml:

    all:
      gravatar:
        default_size:   80
        default_rating: G
        default_image:  gravatar_default.png
        cache_dir_name: g_cache
        cache_expiration: 3 days # refer to strtotime()

The gravatars will be saved in cache under Symfony's upload dir, according to the setting of your Symfony's setup.

For more information, check the gravatar page: http://en.gravatar.com/site/implement/images/

The plugin is being developed by Mickael Kurmann (mickael.kurmann <<at>> gmail.com) and [Xavier Lacot](http://lacot.org/) (xavier@lacot.org)