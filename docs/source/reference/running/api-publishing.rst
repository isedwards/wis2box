.. _api-publishing:

API publishing
==============

When wis2box starts, the API provisioning environment is initialized.  At this stage,
the following steps are required:

- station metadata has been configured
- discovery metadata has been created
- data pipelines are configured and running

Let's dive into publishing the data and metadata:

wis2box provides an API supporting the `OGC API`_ suite of standards using `pygeoapi`_.

Station metadata API publishing
-------------------------------

The first step is to publish our station metadata to the API. The command below
will generate local station collection GeoJSON for API publication.

.. code-block:: bash

   wis2box metadata station publish-collection


.. note:: This command also runs automatically at startup and thereafter every 10 minutes
          to keep your stations up to date.

.. seealso:: :ref:`station-metadata`


Discovery metadata API publishing
---------------------------------

This step will publish dataset discovery metadata to the API.

.. code-block:: bash

   wis2box metadata discovery publish /path/to/discovery-metadata.yml


Dataset collection API publishing
---------------------------------

The below command will add the dataset collection to pygeoapi from the
discovery metadata MCF created as described in the :ref:`discovery-metadata` section.

.. code-block:: bash

   wis2box data add-collection $WIS2BOX_DATADIR/data/config/foo/bar/baz/discovery-metadata.yml


Deleting a dataset
------------------

To delete a dataset from the API backend and configuration:

.. code-block:: bash

   wis2box data delete-collection dataset-id


.. note::

   Changes to the API configuration are reflected and updated automatically.


Summary
-------

At this point, you have successfully published the required data and metadata collections to the API.


.. _`OGC API`: https://ogcapi.ogc.org
.. _`pygeoapi`: https://pygeoapi.io
