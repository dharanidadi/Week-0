# header
### Nodes
One of the primary purposes of ROS is to facilitate communication between the ROS nodes. Every program in ROS is called a **node**. Every independent task can be separated into nodes which communicate with each other through channels. These channels are also known as **topics**.

For example, one node can capture the images from a camera and send the images to another node for processing. After processing the image, the second node can send a control signal to a third node for controlling a robotic manipulator in response to the camera view.

The main mechanism used by ROS nodes to communicate is by sending and receiving **messages**. The **messages** are organized into specific categories called **topics**. Nodes may **publish** messages on a particular topic or **subscribe** to a topic to receive information.

Common ROS tools:

`roscore`:The Main program to initiate ros. It sets up the basic architecture for the channels, allowing nodes to communicate.

`rosrun` is used to run a single ros program  (node).

`roslaunch` is used to automate launching multiple nodes at once.

There are tools like `rostopic` and `rqt_graph` which can be used to visualize the nodes’ communication in the current channels and their message transactions.

### Topics
You use a topic when you need to send a data stream. The data stream is unidirectional. Some nodes can publish on the topic, some nodes can subscribe to the topic. There is no response from a subscriber to a publisher, the data is only going one way.

A topic has a message type. All publishers and subscribers on this topic must use the message type associated with the topic.

You can create a publisher or subscriber in any ROS supported language you want, directly inside ROS nodes.

When a node wants to publish something, it will inform the ROS master. When another node wants to subscribe to a topic, it will ask the ROS master form where it can get the data.
(The rosmaster package implements the ROS Master. Most programs will not need to interact with this package directly. The rosmaster is run automatically whenever `roscore` is run and all communication with the Master happens over XMLRPC APIs.)

Finally, a node can contain many publishers and subscribers for many different topics.

### Services

A ROS service is a client/server system

Services are another way to pass data between nodes in ROS. Services are just synchronous remote procedure calls, they allow one node to call a function that executes in another node. Service calls are well suited to things that you only need to do occasionally and that take a bounded amount of time to complete.

A service is defined by a name, and a pair of messages. One message is the request, one message is the response. You must respect the format of the data on both side of the communication.

You can directly create service clients and servers inside ROS nodes, using for example, the roscpp library for c++ and the rospy library for Python.

Finally, a service server can only exist once, but can have many clients. And basically, the service will be created when you create the server.

(Topics will be used for unidirectional data streams, and services will be used when you need a client/server architecture.)





