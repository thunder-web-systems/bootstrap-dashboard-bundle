This bundle is a basic implementation of 
https://getbootstrap.com/docs/4.1/examples/dashboard/ to symfony. 

To install the bundle:

    composer require uspdev/bootstrap-dashboard-bundle
   
Assets:

    php bin/console assets:install --symlink

Extends in your template:

    {% extends '@UspdevBootstrapDashboard/base.html.twig' %}

Blocks available to override:

 - title
 - system_name
 - search
 - user
 - sidebar
 - body
 - javascripts (it is a good idea to use: {{ parent() }})
 - stylesheets (it is a good idea to use: *{{ parent() }}*)
