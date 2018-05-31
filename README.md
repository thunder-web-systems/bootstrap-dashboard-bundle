This bundle is a basic implementation of 
https://getbootstrap.com/docs/4.1/examples/dashboard/ to symfony. 

To install the bundle:

    composer require uspdev/bootstrap-dashboard-bundle
   
Assets:

    php bin/console assets:install --symlink

Use in you template, override the block body from base:

    {% extends '@UspdevBootstrapDashboard/base.html.twig' %}

