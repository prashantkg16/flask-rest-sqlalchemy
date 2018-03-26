Flask Rest Application 

	Features:
		- Exposed the Rest Services
		- Using existing Mysql database 
		- Using SQLALCHEMY as ORM
		- Support the large application

	Directory Structure:
		- app(directory)
			- __init__.py
			- mod_rest(directory)
				- __init__.py
				- controllers.py
				- models.py
			- templates(directory)
				- 404.html
		- config.py
		- run.py
		- readonly.cfg
		
This application exposed the rest base web services with using the Pre existing database. For database queries, It is using the SQLALCHEMY ORM.

As per directory structure, application is initialized from app directory

In GIT- config.py, Through configparser, we get the database credential from config file
config = configparser.ConfigParser()  
### Database credential stored on read only 
config.read('readonly.cfg')

SQLALCHEMY_DATABASE_URI = 'mysql://' + config.get('DB', 'user') + ':' + config.get('DB', 'password') + '@' + config.get('DB', 'host') + '/' + config.get('DB', 'db')
SQLALCHEMY_TRACK_MODIFICATIONS = True


In GIT - app/__init__.py, This is the initialization file
from flask_sqlalchemy import SQLAlchemy
app = Flask(__name__)
### Configurations
app.config.from_object('config')
# database object
mysqldb = SQLAlchemy(app)
### 


In GIT - there is a app mod_rest. Three file in  
	__init__.py		
	controllers.py	### logical section
	models.py	### Initialized all the model



