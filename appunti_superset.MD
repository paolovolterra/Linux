# [Apache SUPERSET](https://superset.apache.org/)
![logo](https://superset.apache.org/img/superset-logo-horiz-apache.svg)

su
pip install Pillow==2.2.2
pip install virtualenv
apt install python3.8-venv
. venv/bin/activate
pip install --upgrade setuptools pip
## Install superset
pip install apache-superset

## Initialize the database
superset db upgrade

## Create an admin user (you will be prompted to set a username, first and last name before setting a password)
export FLASK_APP=superset
superset fab create-admin
pip3 install Pillow
superset init  # Create default roles and permissions

## lanciare il server
superset run -p 8088 --with-threads --reload --debugger  # To start a development web server on port 8088, use -p to bind to another port

## collegarsi a mysql
pip install pymysql
mysql+pymysql://pvolterr:8422@127.0.0.1/aida


## collegarsi a Clickhouse
spegnere i 2 server
pip install clickhouse-driver==0.2.0 && pip install clickhouse-sqlalchemy==0.1.6

### URI
clickhouse+native://default:8422@localhost/aida


## sul browser all'indirizzo http://127.0.0.1:8088/ si entra con la solita papo ecc.

## [collegare il server clickhouse](https://altinity.com/blog/visualizing-clickhouse-data-with-apache-superset-part-1-installation)
pip install clickhouse-sqlalchemy  

![](https://altinity.com/wp-content/uploads/2021/04/add-database-1024x534.png)

clickhouse+native://localhost/default

# ERRORI

## launchpadlib 1.10.13 requires testresources

sudo apt install python3-testresources


## Fix to below error: ' error: command 'x86_64-linux-gnu-gcc' failed with exit status 1
. supersetdata/bin/activate  
superset init  
superset run -p 8088 --with-threads --reload --debugger  

## come risolvere l'errore   "bash: venv/bin/activate: No such file or directory"	
pip install --upgrade virtualenv
virtualenv -p python3 venv	

## cannot import name 'soft_unicode' from 'markupsafe'
pip install markupsafe==2.0.1

## No PIL installation found
python3 -m pip install Pillow

## apache-superset 1.4.1 requires sqlalchemy!=1.3.21,<1.4,>=1.3.16, but you have sqlalchemy 1.4.32 which is incompatible
pip install SQLAlchemy==1.3.24



# [INSTALL](https://docs.altinity.com/integrations/clickhouse-and-superset/install-superset/)

## Direct Installation Prerequisites

Before installing Superset on Ubuntu 20.04, the following packages must be installed, and will require administrative access on the machine.

Note that Superset requires Python, specifically Python 3.7.9 and above as of this document. These instructions are modified from the original to include installing python3-venv as part of the other prerequisites.

	sudo apt-get install build-essential libssl-dev libffi-dev python3-dev python3-pip libsasl2-dev libldap2-dev python3-venv

## Direct Installation Instructions

To install Superset directly into the Ubuntu 20.04 operating system:
A virtual environment is highly recommended to keep all of the Superset python requirements contained. Use the following commands to create your Superset virtual environment, activate it, then upgrade pip:

    python3 -m venv clickhouse-sqlalchemy
    . clickhouse-sqlalchemy/bin/activate
    pip install --upgrade pip

Install Superset with the following in your virtual environment. 
The command superset fab create-admin sets the admin user password, which will be used to login and update administrative level Superset settings:

	export FLASK_APP=superset
	pip install apache-superset
	superset db upgrade
	superset fab create-admin
	superset load_examples
	superset init 

Install the ClickHouse SQLAlchemy - this allows Superset to communicate with ClickHouse. There are two drivers currently in development. As of this time, we recommend the clickhouse-sqlalchemy driver. To install clickhouse-sqlalchemy, use the pip command:

	pip install clickhouse-sqlalchemy

For those who want to enable TLS communications with services like Altinity.Cloud, verify the versions:

    The clickhouse-driver version should be greater than 0.2.0.

    The clickhouse-sqlalchemy driver should be 0.1.6 or greater.

    pip freeze | grep clickhouse
    clickhouse-driver==0.2.0
    clickhouse-sqlalchemy==0.1.6

## Starting Superset From Direct Install

Once Superset is installed, start it with the following command:

	superset run -p 8088 --with-threads --reload --debugger

Access the Superset web interface with a browser at the host name, port 8088. For example: http://localhost:8088. The default administrative account will be admin, with the password set from the command superset fab create-admin as listed above.

## Installation References

    Installing Superset from Scratch

