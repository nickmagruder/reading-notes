# Welcome to Nick's CodeFellows Page
## CodeFellows Reading Notes

Table of Contents
* [Home](https://nickmagruder.github.io/reading-notes/)



# Code 401 Notes

# Reading 16 - AWS: Cloud Servers

## Review, Research, and Discussion
1. What’s the difference between a FIFO and a standard queue?
    - Amazon SQS FIFO queues are nearly identical to normal queues, but support "exactly-once" processing and prevent unintentional duplicates
2. How can the server be assured a message was properly received?
    - By added "received" message functionality using queues such that messages are only deleted from the queue once receipt is confirmed
3. What classic design pattern is best represented by event driven programming?
    -   Observer pattern
4. How do you test an event driven system?
    -   Implement effective logging, use a tracing collector, unit tests require a lot more work; ideally an automation process can be built. An entire messages infrascture has to be built before proper testing can be implemented.

## Terms
- Server: A hub through which all messages/events pass
- Pub/Sub: Publisher/Subscriber messaging
- WRRC - Web Response/Request cycle

<br/><br/><br/><br/>






# Reading 17

## Review, Research, and Discussion

## Terms


<br/><br/><br/><br/>






# Reading 18

## Review, Research, and Discussion

## Terms


<br/><br/><br/><br/>






# Reading 19

## Review, Research, and Discussion

## Terms


<br/><br/><br/><br/>






# Reading 20

## Review, Research, and Discussion

## Terms





<br/><br/><br/><br/><br/><br/><br/><br/>


# Lecture Notes

# Monday 3/8

## Reading/Lab/Challenge Notes:
[What is a virtual machine](https://www.youtube.com/watch?v=yIVXjl4SwVo)
- Virtual Machine Manager or hypervisor
    - ALlows running different OS with an OS
[Virtualization](https://www.youtube.com/watch?v=l0DfHUWMjsU)
- Virtualization and the cloud
    - Hypervisor allowed creating virtual machinesjjj
[Amazon EC2](https://aws.amazon.com/ec2/?ec2-whats-new.sort-by=item.additionalFields.postDateTime&ec2-whats-new.sort-order=desc)
- Elastic Compute Cloud
- "Amazon EC2 is a web service that provides secure, resizable compute capacity in the cloud."
[EC2 for Humans](https://www.youtube.com/watch?v=lZMkgOMYYIg)
### Elastic Beanstalk
- Different Remote Computer Options:
    - M=Multipurpose
    - C=Compute Optomized
    - T="Burst" for spikey applications
- Auto-assign Public IP: Enable to make web-accessible
- IAM role: what capabalities it has
- EBS: Elastic Block Storage
- Security Group
    - Type: SSH: Protocol: TCP: Port Range: 22 Source: My IP
    - IP Range might be needed using "cider"
    - Other Security Group Notes:
        - Inbound: managing what can access your instance, should be as strict as possible
- Review Launch instance
    - Key Pair: required for logging in, must be saved securely and NEVER LOSE I
### Connecting to the new Instance
- Use terminal
- ssh -i <path-to-paypair.pem> <username@publicdns>
- Cannot connect if key-pair .peb file is not protected - file must protected
- Run command:
    - chmod 400 <path-to-paypair.pem>


## Lecture Notes
- 


<br/><br/><br/><br/>





# Tuesday

## 

<br/><br/><br/><br/>





# Wednesday 

## 

<br/><br/><br/><br/>






## Thursday

##

<br/><br/><br/><br/>





# Friday

## 



