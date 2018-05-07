=========================
How to launch the project
=========================

Navigate to OUAP-4314/Evaluation/Projet and start the containers:

.. code-block:: bash

    docker-compose up

You can also start the containers in detached mode and check their logs in real time:

.. code-block:: bash

    docker-compose up -d
    docker-compose logs -f

Check if the containers are up:

.. code-block:: bash

    docker-compose ps

Gracefully shut the containers down:

.. code-block:: bash

    docker-compose down

Deploy the project on a Raspberry Pi:

.. code-block:: bash

    docker-compose -f rpi_docker-compose.yml up

Deploy the project on macOS:

.. code-block:: bash

    docker-compose -f mac_docker-compose.yml up

N.B.: the deployment is optimized for docker-compose. If you wish to launch each container separately,
add the --link parameter to the run command for both Scrapy and Flask containers:

.. code-block:: bash

    docker run -it --name scrapy_container --link mongo_container scrapy_image
    docker run -d --name flask_container --link mongo_container -p 1000:1000 flask_image

N.B. 2: the spider as it is only retrieves 20 authors for each letter of the alphabet (+ special character).
If you wish to extract more data, feel free to modify or remove the slice at line 32 in the authors.py spider `script <https://github.com/nicolasvo95/OUAP-4314/blob/master/Evaluation/Projet/scrapy_bdgest/bdgest/spiders/authors.py>`_
