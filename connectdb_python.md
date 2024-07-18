Accessing a database through python programming language is through DB-API.


*** when an user writes a code through notebook or any IDE using python or R, and then to conncect to the database it is done ithrough DB-API. ***

# Benefits of using DB-API

- Easy to implement and understand
- encouragegs similarity between python modules used to access datbases.
- portable across databases
- achieves consistency
- broad reach of connectivity from python

## concepts of  python db-api

1. Connections Objejcts
   - Database connections
   - Manage transactions
2. Cursor objects
   - Database Queries
   - Scroll through results set
   - Retrieve results

# writing code using Db-api

from dbmodule import connect

#create connection objects

    Connection = connect('dbname','username','pswd')

#create a cursor object

    Cursor = Connection.cursor()

#run queries

    Cursor.execute('Select * from mytable')
    Results = cursor.fetchall()

#free resources

    Cursor.close()


