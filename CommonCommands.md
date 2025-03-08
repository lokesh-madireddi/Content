# File Size Increase

1. Command used to check the file size in a VM/EC2
``` df -h ```

2. Now by using this command you can see the available space in other disks of instance
``` lsblk ```

3. To allocate the free space to your drive you need to have few installables 
``` sudo apt install cloud-guest-utils ```

4. Now after installaling, you need to allocate the space to thepartition of same roote (/) with below command 
```sudo growpart /dev/xvda 1 ```

5. now run step 2 and check whether the partition is allocated with maximun space
  
6. Finally run the below to allocate the space to our actual file system 
```sudo resize2fs /dev/xdva1```

This is how you can allocate the space to your file system in realtime.
Before doing all these you should increase the size of instance in portal


# Content
```sudo apt install unzip -y```  To install unzip.
