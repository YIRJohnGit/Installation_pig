# Pig Installation [Ubuntu 22] #

## Prerequitist and Installation ##
current Logged User Name: **_hadoop_**
host: **_localhost_**
```
sudo hostnamectl set-hostname localhost
exec bash
```
_Result_
![image](https://user-images.githubusercontent.com/111234771/195283872-ad5b1a98-5f9d-4356-934a-b6ec31935701.png)

### Step-1 - Initial Setup and System Updates ###
```
sudo apt update
```
```
java -version
readlink -f $(which java) # Verify Java Location

sudo apt remove openjdk-11*
sudo apt remove icedtea*
```

### Step-2 - Java Installation ###
```
sudo apt install -y openjdk-8-jdk openjdk-8-jre
```

### Step-3 - Download hive from the below link ###
```
cd ~/Downloads
```

_**Note:** Run the command for the first time and complete 100% Downloads_
```
wget --continue https://dlcdn.apache.org/pig/pig-0.17.0/pig-0.17.0.tar.gz

```
_Result: Successfull Downloads_
![image](https://user-images.githubusercontent.com/111234771/195462709-d60cdf85-6061-4ae1-89a7-430c57917b6e.png)

**_Extract and Move the usr folder_**
```
tar -xzvf pig-0.17.0.tar.gz
ll -lsht
```
_Result_
![image](https://user-images.githubusercontent.com/111234771/195463093-68b7067a-ddd6-4787-be6c-1dba565df4c0.png) 

```
ls -lhsrt
mv pig-0.17.0/ ../pig/
```

_Result_
![image](https://user-images.githubusercontent.com/111234771/195463333-fff8330b-d052-4bce-9924-02cb68ef8b4c.png)

### Step-4 - Add Environment Variables ###
```
sudo nano ~/.bashrc
```
**_Add the below Change to the ~/.bashrc File and Save_**
```
#PIG Folder Path Settings
export PIG_HOME=/home/hadoop/PIG
export PATH=$PATH:$PIG_HOME/bin
```
_Result_
![image](https://user-images.githubusercontent.com/111234771/195463572-4e53eadd-5161-44ee-963b-8010ed8e0a58.png)

**_Initiate the default changes_**
```
source ~/.bashrc
```


**Note:** _Start a New Terminal_
```
cd $HIVE_HOME
bin/beeline -n hadoop -u jdbc:hive2://localhost:10000
```
_Result_
![image](https://user-images.githubusercontent.com/111234771/195278928-709db835-214f-4def-88ef-41a44201f4b3.png)

```
show databases;
```
_Result_
![image](https://user-images.githubusercontent.com/111234771/195280370-b049018f-1957-4b36-8850-b15ca3b53b20.png)


**Note:** _Start a New Terminal_
```
hive
```
_Result_
![image](https://user-images.githubusercontent.com/111234771/195281072-ab2eb396-e416-4340-a8aa-23900f950fcb.png)


# Congratulation..... Hive Sucessfully Installed...#

# Uninstall Hive #
```
sudo rm -R /usr/local/apache-hive-3.1.3-bin
```

### Remove the content from ~/.bashrc ###
```
sudo nano ~/.bashrc
```
```
export HIVE_HOME=/usr/local/apache-hive-3.1.3-bin
export PATH=$PATH:$HIVE_HOME/bin
```

### Remove the Directories ###
```
hdfs dfs -rm -R /tmp
hdfs dfs -rm -R /user/hive/warehouse
```


# Troubleshooting #
### TS-001 - SLF4J: Class path contains multiple SLF4J bindings ###

![image](https://user-images.githubusercontent.com/111234771/195240546-9ed7fc72-cd1e-47c6-9a64-8ec1c8deae46.png)

**Problem Statement:** _Same kind of Class Function are available in Two difference places with difference versions_

**Solution:** _We are going delete one file from New locaition and copy ands replace the other file from old location to new location, that means we will have same file in both places_

### Locate the Files ###
```
ls $HIVE_HOME/lib/guava*
ls $HADOOP_HOME/share/hadoop/hdfs/lib/guava*
```
_Result_
 ![image](https://user-images.githubusercontent.com/111234771/195242097-0af7ded1-bec2-47e3-b94b-6366061585c7.png) 

### Remove and Replace the file ###
```
sudo rm -f $HIVE_HOME/lib/guava-27.0-jre.jar
```
```
sudo cp $HADOOP_HOME/share/hadoop/hdfs/lib/guava-27.0-jre.jar $HIVE_HOME/lib/
```


## Continue from Step-7 - Initiate Derby Database ##

