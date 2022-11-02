# airflow setup


1. Create a new sub-directory called airflow in your project dir (such as the one we're currently in)

2. Set the Airflow user:

  On Linux, the quick-start needs to know your host user-id and needs to have group id set to 0. Otherwise the files created in `dags`, `logs` and `plugins` will be created with root user. You have to make sure to configure them for the docker-compose:

          mkdir -p ./dags ./logs ./plugins
          echo -e "AIRFLOW_UID=$(id -u)" > .env
  
On Windows you will probably also need it. If you use MINGW/GitBash, execute the same command.

To get rid of the warning ("AIRFLOW_UID is not set"), you can create .env file with this content:

          AIRFLOW_UID=50000


3. Import the official docker setup file from the latest Airflow version:

          curl -LfO 'https://airflow.apache.org/docs/apache-airflow/stable/docker-compose.yaml'

4. It could be overwhelming to see a lot of services in here. But this is only a quick-start template, and as you proceed you'll figure out which unused services can be removed. Eg. Here's a no-frills version of that template.

5. Docker Build:

When you want to run Airflow locally, you might want to use an extended image, containing some additional dependencies - for example you might add new python packages, or upgrade airflow providers to a later version.

Create a `Dockerfile` pointing to Airflow version you've just downloaded, such as `apache/airflow:2.2.3`, as the base image,

