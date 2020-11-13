Here is the mapping of VMs to their private IPs:

VM Name	Host Name	IP Address
zookeeper1	vkc-zk1	10.30.3.2
zookeeper2	vkc-zk2	10.30.3.3
zookeeper3	vkc-zk3	10.30.3.4
broker1	vkc-br1	10.30.3.30
broker2	vkc-br2	10.30.3.20
broker3	vkc-br3	10.30.3.10
Hosts file entries:

10.30.3.2	vkc-zk1
10.30.3.3 	vkc-zk2
10.30.3.4 	vkc-zk3
10.30.3.30 	vkc-br1
10.30.3.20 	vkc-br2
10.30.3.10 	vkc-br3
Zookeeper servers bind to port 2181. Kafka brokers bind to port 9092.

Let's test it!
First test that all nodes are up vagrant status. The result should be similar to this:

Current machine states:

zookeeper1                running (virtualbox)
zookeeper2                running (virtualbox)
zookeeper3                running (virtualbox)
broker1                   running (virtualbox)
broker2                   running (virtualbox)
broker3                   running (virtualbox)


This environment represents multiple VMs. The VMs are all listed
above with their current state. For more information about a specific
VM, run 'vagrant status NAME''.
Login to any host with e.g., vagrant ssh broker1. Some scripts have been included for convenience:

Create a new topic /vagrant/scripts/create-topic.sh <topic name> (create as many as you see fit)

Note: If this step fails, exit the VM and run vagrant up --provision (if error persists, please file an issue)

Topics can be listed with /vagrant/scripts/list-topics.sh

Start a console producer /vagrant/scripts/producer.sh <topic name>. Type few messages and seperate them with new lines (ctl-C to exit).

/vagrant/scripts/consumer.sh <topic name>: this will create a console consumer, getting messages from the topic created before. It will read all the messages each time starting from the beginning.

Now anything you type in producer, it will show on the consumer.
