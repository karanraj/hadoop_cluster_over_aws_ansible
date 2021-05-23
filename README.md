# Software Required #

* [JDK](https://drive.google.com/file/d/17UWQNVdBdGlyualwWX4Cc96KyZhD-lxz/view?usp=sharing)
* [Hadoop](https://drive.google.com/file/d/1541gbFeGZZJ5k9Qx65D04lpeNBw87rM5/view?usp=sharing)
* [Apache-Hive](https://drive.google.com/file/d/1hym2U10gEWtq1MCdLo9PgO9KrDS6JWpB/view?usp=sharing)

# This repo contains 4 files/directory #

1. **hosts** This directory which is a dynamic inventory for anisble playbook fetches hosts from aws which is launched by **Instance Role**.
2. **roles** This directory contains all the 6 roles used in the project.
3. **ansible.cfg** This file is a configuration file for ansible. *You only have to update your public key path which will be used to login to the instances*.
4. **playbook.yml** This file contains all the play required for setup.

# Roles Used #

Here I have created 6 role in total kept in roles directory...

1. **Instance** for launching aws 9 instances. 1 *Namenode*, 3 *DataNode*, 1 *JobTracker*, 3 *TaskTracker*, 1 *Client*
   Update the varibale in roles/Instances/vars/main.yml
   access_key: "Your AWS Access key"
   secret_key: "Your AWS Secret Key"
   ami_id: "AMI-Id"
   sg_group_id: "SecurityGroup-Id"
   ins_type: "Instamce Type"
   key_name: "Key Name"
   subnet_id: "Subnet-Id"
2. **NameNode** *for Configuring Namenode*
     * Put the above downloaded JDK software in /root/sowtware/ directory
     * Put the above downloaded Hadoop software in /root/sowtware/ directory
     * You can update roles/NameNode/vars/main.yml with your own values otherwise leave it...
       * namenode_port_no: "9001"
       * namenode_dir: "/name"
3. **DataNode** *For Configuring Datanodes*
     * Put the above downloaded JDK software in /root/sowtware/ directory.
     * Put the above downloaded Hadoop software in /root/sowtware/ directory.
     * You can update roles/DataNode/vars/main.yml with your own values otherwise leave it
       * namenode_port_no: "9001"*It must be same as that of namenode*
       * datanode_dir: "/data"
4. **JobTracker** *For Configuring JobTracker*
    * Put the above downloaded JDK software in /root/sowtware/ directory.
    * Put the above downloaded Hadoop software in /root/sowtware/ directory.
    * You can update roles/JobTracker/vars/main.yml with your own values otherwise leave it...
       * namenode_port_no: "9001"*same as that of namenode*
       * jobtracker_port_no: "9002"
5. **TaskTracker** *For Configuring TaskTracker*
    * Put the above downloaded JDK software in /root/sowtware/ directory.
    * Put the above downloaded Hadoop software in /root/sowtware/ directory.
    * You can update roles/TaskTracker/vars/main.yml with your own values otherwise leave it...
       * jobtracker_port_no: "9002"*same as that of JobTracker*
6. **Client** *For Configuring Client:*
     * Put the above downloaded JDK software in /root/sowtware/ directory.
     * Put the above downloaded Hadoop software in /root/sowtware/ directory.
     * Put the above downloaded Apache-Hive in /apache-hive directory.
     * You can update roles/TaskTracker/vars/main.yml with your own values otherwise leave it...
       * namenode_port_no: "9001"*same as that of NameNode*
       * jobtracker_port_no: "9002"*same as that Of jobtracker*

# Finally Run The Playbook #

With command *ansible-playbook playbbok.yml* run the playbook and your setup will be configured successfully.

