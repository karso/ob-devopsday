
# ob Movies

This is a short guide on setting up the system and environment dependencies
required for ob's Movies database.

#### **Your Mission**

Greetings Earthling! You have been selected to test your skills among the Team Awesome,
**DevOps** :)

This challenge contains a directory - `ob-devopsday/obmovies` - with a Python project and a mongoDB dataset dump 
(available on the releases section of the repo). The package dependencies for Python are resolved using pip. The project 
was built using Flask framework. The application has some errors/omissions that are purposefully made. Once you have 
solved the connection issue run ``pytest`` to confirm 
connectivity.

#### **Challenges**
1. Solve the following tickets/TODOs in `db.py`: 
   1. Paging,
   1. Faceted Search and 
   1. User Management.
1. Containerize obmovies webapp and deploy into a Kubernetes solution/tool of your choice.
1. Use helm chart to deploy the webapp. 

##### **Brownie points:**
* Create a CICD pipeline to build the app and deploy to your cluster.
* Codify the creation of your cluster.

 Movies Application Structure
--

Everything you will implement is located in the ``obmovies/db.py`` file, which contains all database interfacing methods. 
The API will make calls to ``db.py`` to interact with a MongoDB. You have the option of using a local mongo server or 
sign up for a free tiered Mongo Atlas account.

The unit tests in ``tests`` will test these database access methods directly, without going through the API. The UI will 
run these methods in integration tests, and therefore requires the full application to be running.

The API layer is fully implemented, as is the UI. If you need to run on a port other than 5000, you can edit the 
``index.html`` file in the build directory to modify the value of **window.host**.

Please do not modify the API layer in any way, ``movies.py`` and ``user.py`` under the **obmovies/api** directory. Doing 
so will most likely result in the frontend application failing to validate some of the labs.


### Local Development Environment Configuration
#### MongoDB Atlas and Compass

Mongo Atlas offers a free tiered option that provides sample datasets. You will be using the ``mflix`` collection for 
this challenge. Optional: If you are interested in running a local mongoDB use the ``mongod-sampledata.gz`` available on the 
Releases tab in git

Sign up for a free-tiered Mongo Atlas account. Create a project and a cluster with a name of your choosing. During the 
creation of the cluster select "Load Sample Dataset". You will need to whitelist your IP address to gain access.


#### Virtualenv

Use ``virtualenv``, to define your Python 3 environment.
You are required to have a Python 3 installed in your workstation.

You can find the `virtualenv installation procedure`_ on the PyPA website.

Once you've installed Python 3 and ``virtualenv``, you will have to setup a
``virtualenv`` environment:
- Navigate to the obmovies python directory: `cd obmovies`
- Create the virtual environment for obmovies: `virtualenv -p YOUR_LOCAL_PYTHON3_PATH obmovies_venv`
- Activate the virtual environment: `source obmovies_venv/bin/activate`
- You can deactivate the virtual environment with the following command: `deactivate`

Documentation: [virtualenv installation](https://virtualenv.pypa.io/en/stable/installation/)

#### Python Library Dependencies

Once the Python 3 environment is activated, we need to install our python dependencies. Dependencies are defined in 
``requirements.txt``, and can be installed with  the following command: `pip install -r requirements.txt`


Running the Application
--

In the ``obmovies`` directory there are two files, called ``dotini_unix`` and ``dotini_win``.

Rename this file to ``.ini`` with the following command:
```
mv dotini_unix .ini  # on Unix
ren dotini_win .ini # on Windows
```

Once the file has been renamed, open it, and enter your Atlas or local mongo server connection string as directed in the 
comment. This is the information the driver will use to connect!

You can confirm connection to the database by running the unit test: `pytest -m connection`

To start the `obmovies` application, run the following command: `python run.py`


And then point your browser to: http://localhost:5000/


Running the Unit Tests
--

To run the unit tests for this challenge, you will use ``pytest``. The challenges solved contains a module of unit tests 
that you can call individually with a command like the following: `pytest -m LAB_UNIT_TEST_NAME`

Each ticket will contain the command to run that ticket's specific unit tests.


## When you are finished
- Please send your solution as a zipped package to Tech-challenge@orderbird.com
- Include documentation on how to run your the your application and the Kubernetes cluster solution/tool used.   
- also please don't fork this repo as other candidates could then start build on top of your solution ;-)
