<p align="center">
  <a href="https://dev.to/vumdao">
    <img alt="How To Change RDS postgresql configurations" src="https://dev-to-uploads.s3.amazonaws.com/i/afr8ecips4oaffbxkypn.png" width="500" />
  </a>
</p>
<h1 align="center">
  <div><b>How To Change RDS postgresql configurations</b></div>
</h1>


## - With RDS you don't edit config files directly. Instead edit the parameters through the RDS console, or via the API.
## - As of now, RDS does allow changing configurations. So you can
> + See the list of configurations that your RDS is using.
> + You can change these parameters. You can change those that are listed in the RDS reference page.
## - This post give an example of change wal_level from replica to logical

## What’s In This Document 
- [General RDS configruation](#-General-RDS-configruation)
- [Change RDS configruation](#-Change-RDS-configruation)
- [Check wal_level](#-Check-wal_level)

### 🚀 **[General RDS configruation](#-General-RDS-configruation)**
![Alt Text](https://dev-to-uploads.s3.amazonaws.com/i/mlgl3vajz72oxa3gkeax.png)

- The RDS use Parameter group default.postgres10. A parameter group acts as a container for engine configuration values that are applied to one or more DB instances.

- It's not able to change parameters in the default parameter groups
![Alt Text](https://dev-to-uploads.s3.amazonaws.com/i/djnfp40hpajt4xun4pxi.png)


### 🚀 **[Change RDS configruation](#-Change-RDS-configruation)**
#### **1. Create new parameter group**
![Alt Text](https://dev-to-uploads.s3.amazonaws.com/i/74phe30hoepl9gztqt2a.png)

#### **2. Set wal_level from replica to logical**
![Alt Text](https://dev-to-uploads.s3.amazonaws.com/i/38fx2hx4jlx2w12raxbd.png)

#### **3. Modify db instance to apply new parameter group**
![Alt Text](https://dev-to-uploads.s3.amazonaws.com/i/b865fmhtnw5icise1edg.png)

- The config require reboot

![Alt Text](https://dev-to-uploads.s3.amazonaws.com/i/ym9gprcs6mocb45lmjyv.png)

### 🚀 **[Check wal_level](#-Check-wal_level)**
```
ubuntu@root:~$ psql -h mydb -p 5432 -U dbadmin_user -d mydatabase 
Password for user dbadmin_user: 
psql (11.5 (Ubuntu 11.5-3.pgdg18.04+1), server 10.4)
SSL connection (protocol: TLSv1.2, cipher: ECDHE-RSA-AES256-GCM-SHA384, bits: 256, compression: off)
Type "help" for help.

mydatabase=> show wal_level;
 wal_level 
-----------
 logical
(1 row)
```

### **Visit wwww.cloudopz.co to get more**


<h3 align="center">
  <a href="https://dev.to/vumdao">:stars: Blog</a>
  <span> · </span>
  <a href="https://vumdao.hashnode.dev/">Web</a>
  <span> · </span>
  <a href="https://www.linkedin.com/in/vu-dao-9280ab43/">Linkedin</a>
  <span> · </span>
  <a href="https://www.linkedin.com/groups/12488649/">Group</a>
  <span> · </span>
  <a href="https://www.facebook.com/CloudOpz-104917804863956">Page</a>
  <span> · </span>
  <a href="https://twitter.com/VuDao81124667">Twitter :stars:</a>
</h3>