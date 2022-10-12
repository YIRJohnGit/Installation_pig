# Pig Installation on Hadoop [Ubuntu 22] #

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
wget --continue https://dlcdn.apache.org/pig/pig-0.17.0/pig-0.17.0-src.tar.gz

```
_Result: Successfull Downloads_


_**Note:** Incase of Error while downloading and you wanted to continue from where download is left, run the bewlow command_


**_Extract and Move the usr folder_**
```
ls -l pig-0.17.0-src.tar.gz
tar -xvzf pig-0.17.0-src.tar.gz
```
```
mv pig-0.17.0-src.tar.gz ../pig
```

_Result_


### Step-4 - Add Environment Variables ###
```
sudo nano ~/.bashrc
```
**_Add the below Change to the ~/.bashrc File and Save_**
```
#Pig Folder Path Settings
export PIG_HOME=/home/hadoop/pig
export PATH=$PATH:$PIG_HOME/bin
```
_Result_


**_Initiate the default changes_**
```
source ~/.bashrc
```

### Step-5 - Start the PIG ###
**Note:** _Start a New Terminal_
```
pig
```
_Result_

# Congratulation..... pig Sucessfully Installed...#

# Uninstall Hive #
```
sudo rm -R ~/pig
```

### Remove the content from ~/.bashrc ###
```
sudo nano ~/.bashrc
```
```
#Pig Folder Path Settings
export PIG_HOME=/home/hadoop/pig
export PATH=$PATH:$PIG_HOME/bin
```


