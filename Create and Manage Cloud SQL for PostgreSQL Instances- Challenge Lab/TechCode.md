# 🌐 Create and Manage Cloud SQL for PostgreSQL Instances: Challenge Lab || GSP355 🚀 [![Open Lab](https://img.shields.io/badge/Open-Lab-blue?style=flat)](https://www.skills.google/course_templates/652/labs/564283)

## ⚠️ Disclaimer ⚠️

<blockquote style="background-color: #fffbea; border-left: 6px solid #f7c948; padding: 1em; font-size: 15px; line-height: 1.5;">
  <strong>Educational Purpose Only:</strong> This script and guide are provided for the educational purposes to help you understand the lab services and boost your career. Before using the script, please open and review it to familiarize yourself with Google Cloud services.
  <br><br>
  <strong>Terms Compliance:</strong> Always ensure compliance with Qwiklabs' terms of service and YouTube's community guidelines. The aim is to enhance your learning experience — not to circumvent it.
</blockquote>

---

<div style="padding: 15px; margin: 10px 0;">

## Enable the following Google APIs:
```bash
gcloud services enable datamigration.googleapis.com --quiet
gcloud services enable servicenetworking.googleapis.com --quiet
```
---

## Compute Engine > VM instances > Connect the SSH of postgresql-vm

- **install the pglogical database extension and jquery**
```
sudo apt install postgresql-14-pglogical
```

- **Download and apply some additions to the PostgreSQL configuration files (to enable pglogical extension)**
```
sudo su - postgres -c "gsutil cp gs://cloud-training/gsp918/pg_hba_append.conf ."
sudo su - postgres -c "gsutil cp gs://cloud-training/gsp918/postgresql_append.conf ."
sudo su - postgres -c "cat pg_hba_append.conf >> /etc/postgresql/14/main/pg_hba.conf"
sudo su - postgres -c "cat postgresql_append.conf >> /etc/postgresql/14/main/postgresql.conf"
sudo systemctl restart postgresql@14-main
```

- **Apply required privileges to postgres and orders databases**

```
sudo su - postgres
```

```
psql
```
Run above command 2 times
```
\c postgres;
```

```
CREATE EXTENSION pglogical;
```
Run above command 2 times
```
\c orders;
```

```
CREATE EXTENSION pglogical;
```
---

### Open the below website

- **[Online word replacer](https://textcompare.io/word-replacer)**

```
CREATE USER migration_admin PASSWORD 'DMS_1s_cool!';
ALTER DATABASE orders OWNER TO migration_admin;
ALTER ROLE migration_admin WITH REPLICATION;


\c orders;


SELECT column_name FROM information_schema.columns WHERE table_name = 'inventory_items' AND column_name = 'id';
ALTER TABLE inventory_items ADD PRIMARY KEY (id);


GRANT USAGE ON SCHEMA pglogical TO migration_admin;
GRANT ALL ON SCHEMA pglogical TO migration_admin;
GRANT SELECT ON pglogical.tables TO migration_admin;
GRANT SELECT ON pglogical.depend TO migration_admin;
GRANT SELECT ON pglogical.local_node TO migration_admin;
GRANT SELECT ON pglogical.local_sync_status TO migration_admin;
GRANT SELECT ON pglogical.node TO migration_admin;
GRANT SELECT ON pglogical.node_interface TO migration_admin;
GRANT SELECT ON pglogical.queue TO migration_admin;
GRANT SELECT ON pglogical.replication_set TO migration_admin;
GRANT SELECT ON pglogical.replication_set_seq TO migration_admin;
GRANT SELECT ON pglogical.replication_set_table TO migration_admin;
GRANT SELECT ON pglogical.sequence_state TO migration_admin;
GRANT SELECT ON pglogical.subscription TO migration_admin;



GRANT USAGE ON SCHEMA public TO migration_admin;
GRANT ALL ON SCHEMA public TO migration_admin;
GRANT SELECT ON public.distribution_centers TO migration_admin;
GRANT SELECT ON public.inventory_items TO migration_admin;
GRANT SELECT ON public.order_items TO migration_admin;
GRANT SELECT ON public.products TO migration_admin;
GRANT SELECT ON public.users TO migration_admin;



ALTER TABLE public.distribution_centers OWNER TO migration_admin;
ALTER TABLE public.inventory_items OWNER TO migration_admin;
ALTER TABLE public.order_items OWNER TO migration_admin;
ALTER TABLE public.products OWNER TO migration_admin;
ALTER TABLE public.users OWNER TO migration_admin;



\c postgres;


GRANT USAGE ON SCHEMA pglogical TO migration_admin;
GRANT ALL ON SCHEMA pglogical TO migration_admin;
GRANT SELECT ON pglogical.tables TO migration_admin;
GRANT SELECT ON pglogical.depend TO migration_admin;
GRANT SELECT ON pglogical.local_node TO migration_admin;
GRANT SELECT ON pglogical.local_sync_status TO migration_admin;
GRANT SELECT ON pglogical.node TO migration_admin;
GRANT SELECT ON pglogical.node_interface TO migration_admin;
GRANT SELECT ON pglogical.queue TO migration_admin;
GRANT SELECT ON pglogical.replication_set TO migration_admin;
GRANT SELECT ON pglogical.replication_set_seq TO migration_admin;
GRANT SELECT ON pglogical.replication_set_table TO migration_admin;
GRANT SELECT ON pglogical.sequence_state TO migration_admin;
GRANT SELECT ON pglogical.subscription TO migration_admin;
```

## Create Connection Profile:

## For Database Migration: Click [Here](https://console.cloud.google.com/dbmigration/migrations?)
```bash
curl -LO raw.githubusercontent.com/DrVelu/Arcade-Google-Cloud-Labs/refs/heads/main/Create%20and%20Manage%20Cloud%20SQL%20for%20PostgreSQL%20Instances%3A%20Challenge%20Lab/DrVelu.sh
sudo chmod +x DrVelu.sh 
./DrVelu.sh
```

---

### Task 3. Implement Cloud SQL for PostgreSQL IAM database authentication

- **Asking For a password enter**

```
supersecret!
```
> Copy and paste the password and the password will not visible to you

```
\c orders
```

- **Asking For a password enter**
```
supersecret!
```
> Copy and paste the password and the password will not visible to you

---

- ⚠️ **Change the TABLE_NAME and USER_NAME by given lab instructions**
```
GRANT ALL PRIVILEGES ON TABLE [TABLE_NAME] TO "USER_NAME";

\q
```

---

### Task 4. Configure and test point-in-time recovery

```
date --rfc-3339=seconds
```
> Copy the given output and Save this

- **Asking For a password enter**
```
supersecret!
```
> Copy and paste the password and the password will not visible to you


```
\c orders
```

- **Asking For a password enter**
```
supersecret!
```
> Copy and paste the password and the password will not visible to you

```
insert into distribution_centers values(-80.1918,25.7617,'Miami FL',11);
\q
```

```
gcloud auth login --quiet

gcloud projects get-iam-policy $DEVSHELL_PROJECT_ID
```

```
gcloud sql instances clone [CLOUDSQL_INSTANCE] [NEW_INSTANCE_NAME] \
 --point-in-time "[TIME_STAMP]"
```


</div>

---

## 🎉 **Congratulations! Lab Completed Successfully!** 🏆  

<div style="text-align:center; padding: 10px 0; max-width: 640px; margin: 0 auto;">
  <h3 style="font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; margin-bottom: 14px;">📱 Join the DrVelu Community</h3>

  <a href="#" style="margin: 0 6px; display: inline-block;">
    <img src="#" alt="YouTube Channel">
  </a>

  <a href="#" style="margin: 0 6px; display: inline-block;">
    <img src="#" alt="LinkedIn Profile">
  </a>

  <a href="#" style="margin: 0 6px; display: inline-block;">
    <img src="#" alt="Telegram Channel">
  </a>

  <a href="#" style="margin: 0 6px; display: inline-block;">
    <img src="#" alt="Instagram Profile">
  </a>
</div>

---

<div align="center">
  <p style="font-size: 12px; color: #586069;">
    <em>This guide is provided for educational purposes. Always follow Qwiklabs terms of service and YouTube's community guidelines.</em>
  </p>
  <p style="font-size: 12px; color: #586069;">
    <em>Last updated: November 2025</em>
  </p>
</div>
