Dutu 
====

Dutu Dependency Injection (DI) container is a small PHP container 
for PHP 5.3 developed as part of Dutu Core (core libraries for the
upcoming Dutu framework). Dutu (DI) or simply Dutu (not to be 
confused with the Dutu framework on which it is meant for), 
influenced by Fabien Pontencier's Pimple_, was designed to be
intuitive, scalable and flexible.

.. _Dutu: http://www.dutu.com/

.. _Pimple: https://github.com/fabpot/Pimple

To use Dutu download_ it and require it in your code::

    require_once '/path/to/Dutu.php';

.. _download: https://github.com/tafadzwagonera/dutu

and then create the container by instantiating the ``Dutu`` class::

    $dutu = new Dutu();

Defining Parameters
___________________

It is as easy as abc. This is how we do it::

    $dutu->cookie_name = 'SESSION_ID';

Defining Services
_________________

There are two ways to define services in dutu. The first method involves
passing an associative array to Dutu's ``__construct`` method during
instantiation::

    //a list of database services
    $parameters = array(
        'pdoImpl' => 'PDOImpl',
        'mysqliImpl' => 'mysqliImpl'
    );

Then passing the array to the container::

    $dutu = Dutu($parameters);

    //instantiates your database class
    $dutu->pdoImpl;

The second method involves passing an associative array of services to Dutu's
``registerComponents`` method::

    $dutu->registerComponents($components);

or we can register components with their dependencies too::

   //only works if all the components in the array
   //have a common dependency
   $dutu->registerComponents($components, $dutu->config);


