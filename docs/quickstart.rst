.. _project-setup-guide:

=================
Quick start guide
=================

Build dependencies
------------------

The following software is required to build geojs from source:

* `Git <https://git-scm.com/>`_
* `Node.js <https://nodejs.org/>`_

For testing and development, the following additional software is required:

* `Python 3 <https://www.python.org/>`_

In addition, the following python modules are recommended for development
and testing of geojs.

* `Girder Client <https://girder.readthedocs.io>`_
* `Pillow <https://pillow.readthedocs.io>`_
* `Requests <http://docs.python-requests.org/en/latest/>`_

For testing WebGL in a headless environment, the additional packages are needed:

* `mesa-utils <https://www.mesa3d.org/>`_ and `libosmesa6 <https://www.mesa3d.org/>`_
* `xvfb <https://www.x.org/archive/X11R7.6/doc/man/man1/Xvfb.1.xhtml>`_
* `Firefox <https://www.mozilla.org/firefox>`_

For an example on how to install all packages for a specific OS, see
:ref:`Ubuntu Provisioning <ubuntu-development>`.

Getting the source code
-----------------------

Get the latest geojs source code from our `GitHub repository`_
by issue this command in your terminal. ::

    git clone https://github.com/OpenGeoscience/geojs.git

This will put all of the source code in a new directory called
``geojs``. 

.. _GitHub repository: https://github.com/OpenGeoscience/geojs

Building the source
-------------------

Inside the new ``geojs`` directory, you can simply run the following commands to
install all dependent javascript libraries and bundle together everything that
is needed. ::

    npm install
    npm run build

The compiled javascript libraries will be named ``geo.min.js`` and ``geo.lean.min.js`` in ``dist/built``.
The first file contains geojs including all optional dependencies. The second file is a version of
geojs without any of the third party dependencies such as d3 and Hammer; if you want to use the lean
bundle but need any of these dependencies, you must include them first in your page and expose them in
global scope under their standard names. The bundled libraries are minified, but source maps are provided.

.. _quick-start-guide:

Using the library
-----------------

The following html gives an example of including all of the necessary files
and creating a basic full map using the `osmLayer` class.

.. code-block:: html

    <head>
        <script src="/built/geo.min.js"></script>

        <style>
            html, body, #map {
                margin: 0;
                width: 100%;
                height: 100%;
                overflow: hidden;
            }
        </style>

        <script>
        $(function () {
            geo.map({'node': '#map'}).createLayer('osm');
        });
        </script>
    </head>
    <body>
        <div id="map"></div>
    </body>

You can save this page into a new file at ``dist/mymap.html``.  To view your new creation,
start up a web server with the command ::

    npm run examples

Now, if you open up `<http://localhost:8082/mymap.html>`_ in your favorite webgl enabled
browser, you should see a map like the following:

.. image:: images/osmmap.png
    :align: center

Additionally, you will be able to see all of the built-in examples at
`<http://localhost:8082/examples>`_ with the example server running.
