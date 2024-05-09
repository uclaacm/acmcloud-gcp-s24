# Google Cloud SQL MySQL Instance Quickstart

## Prerequisites
A Google Cloud account.
Google Cloud SDK installed, or access to the Google Cloud Console.

## Creating a Cloud SQL Instance

### Using Google Cloud Console
1. Navigate to the Cloud SQL Instances page in the Google Cloud console. [Go to Cloud SQL Instances](https://console.cloud.google.com/sql/instances)
2. Click **Create Instance**.
3. Select **MySQL** and click **Choose MySQL**.
4. Enter `myinstance` for the Instance ID.
5. Set a password for the root user.
6. Click **Create**.
7. Once created, you can click on the instance in the instance list to view its details. Note that it won't be available for other operations until it initializes and starts.

## Connecting to Your Instance

### Using Cloud Shell
1. In the Google Cloud console, click the Cloud Shell icon in the upper right corner.
2. Once Cloud Shell initializes, you'll see a welcome message indicating your current project, such as:
```
Welcome to Cloud Shell! Type "help" to get started.
Your Cloud Platform project in this session is set to sample-project.
Use "gcloud config set project [PROJECT_ID]" to change to a different project.
username@sample-project:~ (sample-project)$
```
3. Connect to your Cloud SQL instance with the following command (replace myinstance if your instance name is different):
```shell
gcloud sql connect myinstance --user=root
```
4. Click **Authorize** in the message box to allow Cloud Shell to make API calls.
5. When prompted, enter the root password.

## Database Operations

### Create a Database and Populate Data
1. Once connected, create a new database:
```sql
CREATE DATABASE guestbook;
```
2. Use the new database:
```sql
USE guestbook;
```
3. Create a table and insert sample data:
```sql
CREATE TABLE entries (guestName VARCHAR(255), content VARCHAR(255), entryID INT NOT NULL AUTO_INCREMENT, PRIMARY KEY(entryID));
INSERT INTO entries (guestName, content) values ("first guest", "I got here!");
INSERT INTO entries (guestName, content) values ("second guest", "Me too!");
```
4. Retrieve and view the data:
```sql
SELECT * FROM entries;
```
Expected output:
```
+--------------+-------------------+---------+
| guestName    | content           | entryID |
+--------------+-------------------+---------+
| first guest  | I got here!       |       1 |
| second guest | Me too!           |       2 |
+--------------+-------------------+---------+
2 rows in set (0.00 sec)
```
   
## Notes
These instructions assume the use of a public IP address; Cloud Shell does not work with private IP addresses.