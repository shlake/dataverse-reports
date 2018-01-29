# dataverse-reports
A python3-based tool to generate and email statistical reports from Dataverse (https://dataverse.org/) using the native API and database queries.

As with Miniverse, the reports require access to the Dataverse database.

Configuration
-----

```bash
$ cp config/application.yml.sample config/application.yml
```

Example
```
dataverse__api_host: ''
dataverse__api_key: ''
dataverse_db_host: ''
dataverse_db_username: ''
dataverse_db_password: ''
work_dir: '/tmp'
from_email: ''
admin_emails:
        - email1
        - email2
from_email: ''
accounts:
     account1:
          name: Account 1
          identifier: account1_identifier
          contacts:
               - email1
               - email2
     account2:
          name: Account 2
          identifier: account2_identifier
          contacts:
               - email1
```

Set parameters for API and database connections. Accounts list refers to top-level dataverses on which reports based at the institutional level will begin.

Virtual Environment Setup
-----
```bash
pip install virtualenv
virtualenv -p python3 venv
source venv/bin/activate
pip install -r requirements.txt
```

Usage
-----

All commands run inside the virtual environment.


Generate and email a report of all dataverses for super admin(s).
```bash
$ python run.py -c config/application.yml -r dataverse -g all
```

Generate and email reports of dataverses for each institution beginning at a top-level dataverse.
```bash
$ python run.py -c config/application.yml -r dataverse -g institutions
```

Generate and email a report of all datasets for super admin(s).
```bash
$ python run.py -c config/application.yml -r dataset -g all
```

Generate and email reports of datasets for each institution beginning at a top-level dataverse.
```bash
$ python run.py -c config/application.yml -r dataset -g institutions
```