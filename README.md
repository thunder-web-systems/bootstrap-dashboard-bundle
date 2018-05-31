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

An example that can be inserted in your base.html.twig:

    {% extends '@UspdevBootstrapDashboard/base.html.twig' %}

    {% block title %} Sistema{% endblock %}
    {% block system_name %} Sistema {% endblock %}

    {% block user %}
        {% if is_granted('ROLE_USER') %}
            <a class="btn btn-danger" href=" {{ path('logout') }}">logout</a>
        {% else %}
            <a class="btn btn-success" href=" {{ path('login') }}">login</a>
        {% endif %}
    {% endblock %}

    {% block sidebar %} 
    <ul class="nav flex-column">
        <li class="nav-item">
            <a class="nav-link active" href="/users">
                <span data-feather="home"></span>
                Manage users 
                <span class="sr-only">(current)</span>
            </a>
        </li>
        <li class="nav-item">
            <a class="nav-link" href="/reports">
                <span data-feather="file"></span>
                Reports
            </a>
        </li>
    </ul>
    {% endblock %}

    {% block body %}
        {% for msg in app.session.flashBag.get('success') %}
            <div class="alert alert-success">
                {{ msg }}
            </div>   
        {% endfor %}

        {% for msg in app.session.flashBag.get('danger') %}
            <div class="alert alert-danger">
                {{ msg }}
            </div>   
        {% endfor %}

        {{ parent() }}
    {% endblock %}
