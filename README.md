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
pig
```
_Result_
![image](https://user-images.githubusercontent.com/111234771/195464574-73ecfc25-9fc6-4cc0-80e4-fb89779f4dbe.png)


# Congratulation..... Hive Sucessfully Installed...#

# Uninstall PIG #
```
sudo rm -R ~/pi
```

### Remove the content from ~/.bashrc ###
```
sudo nano ~/.bashrc
```
```
export PIG_HOME=/home/hadoop/PIG
export PATH=$PATH:$PIG_HOME/bin
```
