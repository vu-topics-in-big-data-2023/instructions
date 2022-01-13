# Create MongoDB in AWS EC2

## Step 1. Create the EC2 Instance

![Screen Shot 2021-01-18 at 9.19.49 PM](/Users/zhuangweikang/Desktop/Screen Shot 2021-01-18 at 9.19.49 PM.png)

![Screen Shot 2021-01-18 at 9.20.05 PM](/Users/zhuangweikang/Desktop/Screen Shot 2021-01-18 at 9.20.05 PM.png)

![Screen Shot 2021-01-18 at 9.20.14 PM](/Users/zhuangweikang/Desktop/Screen Shot 2021-01-18 at 9.20.14 PM.png)

![Screen Shot 2021-01-18 at 9.20.24 PM](/Users/zhuangweikang/Desktop/Screen Shot 2021-01-18 at 9.20.24 PM.png)

![Screen Shot 2021-01-18 at 9.20.35 PM](/Users/zhuangweikang/Desktop/Screen Shot 2021-01-18 at 9.20.35 PM.png)

![Screen Shot 2021-01-18 at 9.20.42 PM](/Users/zhuangweikang/Desktop/Screen Shot 2021-01-18 at 9.20.42 PM.png)

## Step 2. Connect to the AWS EC2 instance and Install MongoDB

![Screen Shot 2021-01-18 at 9.20.54 PM](/Users/zhuangweikang/Desktop/Screen Shot 2021-01-18 at 9.20.54 PM.png)

### Install MongoDB

```shell
# 2.1 Install the MongoDb packages
# Login to your EC2 then type the commands:
# Import the public key used for accessing package management system
wget -qO - https://www.mongodb.org/static/pgp/server-4.2.asc | sudo apt-key add -

# 2.2 Create a list file for mongoDB
echo "deb [ arch=amd64 ] https://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/4.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.2.list

# 2.3 Install mongodb using apt
sudo apt-get update && sudo apt-get install -y mongodb-org

# 2.4 Start mongodb server and check its status
sudo service mongod start
sudo service mongod status
```

## Step 3. Configure MongoDB to enable remote connection.

```shell
# 3.1. Create an admin user that has administrations to access all databases and grant limited authorization to normal users.
# Get into the mongodb console and perform the following operations.Note you may change the username and password to whatever you like.
sudo mongo

> use admin
> db.createUser({ user: "admin", pwd: "adminpassword", roles: [{ role: "userAdminAnyDatabase", db: "admin" }] })
> db.auth("admin", "adminpassword")
> exit

# 2.6. Now, we are now going to enable authentication on the MongoDB instance, by modifying the mongod.conf file. Once this is done, you'll be required to provide username and password to connect to databases.
sudo nano /etc/mongod.conf

# Use nano to open the config file then add these lines at the bottom of the YAML config file:
security:
    authorization: enabled

# Then hit ctl+w to search "bindip", you should see:
net:
    bindIp: 0.0.0.0

# Make sure the bindIp is 0.0.0.0, which ensures the mongodb server listen connection requests from everywhere.

# Hit ctl+x, then 'y' to save the update.

# 2.7 Now restart the mongod service (Ubuntu syntax) for the changes to take effect
sudo service mongod restart 
sudo service mongod status

# 2.8 To create a external user login to mongo db account such as 'ubuntu'- Now login to mongo shell and select admin db and authenticate
sudo mongo

> use admin
> db.auth("admin", "adminpassword")
# create a database
> use <the database you want to create>
# create remote user name - 'ubuntu' and a passowrd who can use the db you created (this is generally a good idea. You restrict access for people)
> db.createUser({ user: "ubuntu", pwd: "yourpassword", roles: [{ role: "dbOwner", db: "<your db name>" }] })

#Check that everything went fine by trying to authenticate, with the db.auth(user, pwd) function.
>db.auth("ubuntu", "yourpassword")
```

**Note: keep your username and password private. Very important. This is what you will use to connect to the database.**

**Refer** to the link if you get stuck: https://medium.com/@matteocontrini/how-to-setup-auth-in-mongodb-3-0-properly-86b60aeef7e8

## Step 4. Import Lahman baseball dataset into mongodb

```shell
# download the dataset
wget http://www.seanlahman.com/files/database/lahman2012-csv.zip

# unzip it
tar xzf lahman2012-csv.zip && rm lahman2012-csv.zip

# import all csv files in the lahman2012-csv folder into Mongodb using the mongoimport command
mongoimport -d <dbname> -c <collection_name> --type csv --file <input.csv> --headerline --username "your db username" --password "your password"

# alternatively, you can write a shell script to automate the process
echo "for file in ls *.csv
do 
mongoimport -d lahman -c $(basename $file .csv) --type csv $file --headerline --username <your db username> --password <your db password>
done" >> importer.sh

# then,
sh importer.sh
```

## Step 5.  Check connection using MongoDB compass:

Download the mongoDB compass https://www.mongodb.com/try/download/compass, which is a tool for visualizing MongoDB data in a convenient way.

And test the connection and basic queries.

![Screen Shot 2021-01-18 at 9.21.13 PM](/Users/zhuangweikang/Desktop/Screen Shot 2021-01-18 at 9.21.13 PM.png)