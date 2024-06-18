# Partial solution for part 1

This repo contains working `main.py`, `test.py` and `requirements.txt` files. Copy the files over to $HOME/cnd24-exercise, and then install the dependencies in requirements.txt.

If you didn't manage to populate the database using the `data_model.py` and `db_init.py`, now it may be a good moment to do it:

Copy the solution files:

```bash
cp test.py main.py requirements.txt $HOME/cnd24-exercise
```

ONLY DO THIS IF NOT ALREADY DONE: Create the instace, the database, and the user, and get the connection name for the instance:

```bash
gcloud sql instances create postgres --database-version=POSTGRES_15 --region=europe-west1 --cpu=2 --memory=8GB
gcloud sql databases create product_details --instance=postgres
gcloud sql users create evolution --instance=postgres --password=evolution
export INSTANCE_CONNECTION_NAME="$(gcloud sql instances describe postgres --format="value(connectionName)")"
```

ONLY DO THIS IF NOT ALREADY DONE: Create and activate 

```bash
python -m venv .venv
source .venv/bin/activate
```

Install the required packages:

```bash
pip install -r requirements.txt
```

ONLY DO THIS IF NOT ALREADY DONE IN PART 1: create the tables and the data in the database:

```bash
export DB_USER=evolution
export DB_PASS=evolution
export DB_NAME=product_details
python data_model.py
python db_init.py
```

Finally, test your application

```bash
python main.py
```

You should now be in a good place to continue with part 2.
