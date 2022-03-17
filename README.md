## Phonebook Backend Api

### Run Program

Get a copy of the program:

```bash
  git clone https://github.com/ivandi1980/Phonebook-Backend-Api.git
```

Go to the project directory:

```bash
  cd Phonebook_Backend_REST-API_using_Golang_and_PostgreSQL
```

Build image and start the Backend app and PostgreSQL database:

```bash
  docker-compose up -d --build --force-recreate
```

Check if they are running properly:

```bash
  docker-compose ps
```

The output should be like this:

```bash
        Name                    Command            State            Ports
----------------------------------------------------------------------------------
phonebook_backend_api   ./Phonebook_Backend_REST   Up      0.0.0.0:8000->8000/tcp,
                        -A ...                             :::8000->8000/tcp
phonebookdb             docker-entrypoint.sh       Up      0.0.0.0:5432->5432/tcp,
                        postgres                           :::5432->5432/tcp

```

### Connect to database and add a table

Go inside of the container:

```bash
  docker exec -it phonebookdb /bin/sh
```

Then connect to PostgreSQL database:

```bash
  psql -U postgres
```

Now, add a table:

```bash
CREATE TABLE contacts (
  id SERIAL,
  PhoneNumber VARCHAR(250) NOT NULL,
  FullName VARCHAR(250) NOT NULL,
  Address VARCHAR(250) NOT NULL,
  Email VARCHAR(250) NOT NULL,
  PRIMARY KEY (id)
);
```

And add some data into the table:

```bash

INSERT INTO contacts (
  PhoneNumber,
  FullName,
  Address,
  Email
)
VALUES
    ('01234567890', 'Ivandjoh','Indonesia','ivan@ivan.com'),
    ('09876543210', 'Juna','Indonesia','juna@juna.com');

```

At the end, check if the data has been added successfully:

```bash
  SELECT * FROM contacts;
```

The output should be like this:

```bash
 id |  phonenumber   |      fullname      |                                   address                                    |         email
----+----------------+--------------------+------------------------------------------------------------------------------+-----------------------
  1 | 01234567890 | Ivandjoh | Indonesia| ivan@ivan.com
  2 | 09876543210  | Juna  | Indonesia | juna@juna.com
(2 rows)
```
