# **NBA Data Lake**
This project automates the setup of a **data lake** for **NBA analytics** using AWS services, including **Amazon S3, AWS Glue, and Amazon Athena**. It fetches **NBA player data** from an external API, stores it in **S3**, organizes it with **AWS Glue**, and enables querying via **Amazon Athena**.

---

## **Project Overview**
This project includes a Python script, `setup_nba_data_lake.py`, which does the following:
- ✅ Creates an **S3 bucket** to store raw NBA data.
- ✅ Fetches and uploads **NBA player data** to **Amazon S3**.
- ✅ Sets up an **AWS Glue** database and table.
- ✅ Configures **Amazon Athena** for querying structured NBA data.

---

## **Prerequisites**
Before running the script, ensure you have:

### **1. API Access from SportsData.io**
- **Sign up** at [SportsData.io](https://sportsdata.io).
- Navigate to **"Developers" → "API Resources" → "Introduction & Testing"**.
- Select **NBA** and sign up for a **free trial**.
- **Retrieve your API Key** from the **"Standings"** section.

### **2. AWS IAM Role/Permissions**
Ensure the user or role running the script has the following permissions:
- **S3**: `s3:CreateBucket`, `s3:PutObject`, `s3:DeleteBucket`, `s3:ListBucket`
- **Glue**: `glue:CreateDatabase`, `glue:CreateTable`, `glue:DeleteDatabase`, `glue:DeleteTable`
- **Athena**: `athena:StartQueryExecution`, `athena:GetQueryResults`

---

## **Installation & Setup**

### **Step 1: Open AWS CloudShell**
1. Go to [AWS Console](https://aws.amazon.com) and sign in.
2. Click the **CloudShell icon** (`>_`) next to the search bar.

### **Step 2: Create the `setup_nba_data_lake.py` File**
1. In the CloudShell CLI, type:
   ```bash
   nano setup_nba_data_lake.py


# Step 3: Create the setup_nba_data_lake.py file
1. In the CLI (Command Line Interface), type
```bash
nano setup_nba_data_lake.py
```
2. Open this GitHub repository: [NBA Data Lake](https://github.com/cleo469/NBA-Data-Lake-Day-3)

3. Copy the contents of `setup_nba_data_lake.py` and paste it into CloudShell.
2.Paste the following line of code into your file, ensuring you swap out with your API key:

```bash
SPORTS_DATA_API_KEY=your_sportsdata_api_key
NBA_ENDPOINT=https://api.sportsdata.io/v3/nba/scores/json/Players
```

Press ^X to exit, press Y to save the file, then press Enter to confirm the file name.

# Step 4: Run the Script
1. In the CLI, type:
```bash
python3 setup_nba_data_lake.py
```
You should see messages indicating:

2.  The resources were successfully created.
3.  The sample data was uploaded successfully.
4.  The Data Lake Setup Completed.

# Step 5: Manually Check for the Resources
1.In the AWS Console, search for **S3** and click on the **S3 service**.

You should see two General Purpose Buckets named "Sports-analytics-data-lake"

* Click the bucket name to view its contents.
* Click on the raw-data folder.

2.You should see a file named
```bash
nba_player_data.json.
```
3.Click the file name, and at the top, select Open File.

4.You will see a JSON-formatted string containing NBA player data.

# Step 6: Query Data in Amazon Athena
1.Navigate to Amazon Athena in the AWS Console.

Paste the following SQL query:
```bash
SELECT FirstName, LastName, Position, Team
FROM nba_players
WHERE Position = 'PG';
```
2.Click Run.

The query results should display NBA players who play as Point Guards (PG).

# What I Learned

*Securing AWS services with least privilege IAM policies.

*Automating AWS resource creation with a Python script.

*Integrating external APIs into cloud-based workflows.

# Future Enhancements

*Automate data ingestion with AWS Lambda.

*Implement a data transformation layer with AWS Glue ETL.

*Add advanced analytics & visualizations using AWS QuickSight.

