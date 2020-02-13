## **ZiSoft Awareness HW Sizing**

**Overview**
ZiSoft Awareness is a flexible web-based application that is designed to accommodate both small-scale
implementation in a single department and large-scale application in organizations with thousands of users.
Large-scale execution, however, requires careful planning and an adequate setup to accommodate the
processing, bandwidth and storage needs of the system.

**General Environment Sizing Notes**
ZiSoft Awareness is a data intensive platform. As such, the majority of the workload is usually dependent on
the database environment. A properly tuned database environment is an absolute requirement for a
production environment in ZiSoft Awareness. Many of the sizings detailed will be focused on data storage.
ZiSoft Awareness is used in various enterprise environments with different use cases. The Best Practices
described below is not a one size fit all solution. Please take your use cases into account and use your best
judgement to determine the best architecture solution.

***Process Capability and Memory***

 1. Estimate the number of cases to be created per day. The number of
    processes created in a day has an effect on the performance of
    Zisoft Awareness, which is why its important to have an estimate
    before sizing the server. 
    
 2. Consider the total number of nominal users
    that are expected to be using Zisoft Awareness .
    
 3. Use a web application server tuned for medium CPU and memory capacity.
   
    
 4. Depending on the level of redundancy security the customer requires,
    the production web application server cluster should at LEAST
    support one server being unavailable. This means the other remaining
    servers should have surplus CPU/RAM capacity to handle the extra
    load if this occurs. 
		    
		    o For example, if there are two production
		      servers, ideally 50% of one server's capacity should handle 100% of
		    the volume at peak, at a minimum. Consider one CPU core (or
		    hyper-thread) to every 4 gigabytes of memory. 
		    
		    o For example, for a
		    web application server that has 64GB of memory, a 16 thread/core
		    processing environment is suggested. 
		    o Assume a maximum allowed size
		    per server to be 128GB of memory, with a minimum of 32 thread
		    processing. o Assume a minimum base frequency of 2.4GHz .*
   
    
 5. Consider dedicating 128MB for one active user at a time. o This value might
    change depending on memory requirements for certain processes, etc.
		    
		    o This value is based on the memory_limit in PHP's configuration
		      file and should also account for the overhead web server memory
		      requirements. 
		    o For the total amount of users, ensure that there is
                     a buffer that allows for 30% spikes at any time.*

**Network Speed**
• These servers should have gigabit network interfaces and should be local to the shared resources of
the load balancer and dependencies (file server, databases and caching). Ensure that your router and
Internet bandwidth supports your expected incoming and outgoing traffic.

# Error Percentage Table Per Instance
| Instance Type |  vCPU | Memory |  Network I/O | 20 Users | 40 Users | 60 Users| 80 Users | 100 Users|200 Users|300 Users| 400 Users|
|------|----|----|------|-----|----|------|----|----|------|-----|-----|
| t2.medium |  2| 4 |  1 G |  [2.02%](https://zisoft-jmeter.s3-us-west-2.amazonaws.com/Tests/t2.medium/20user/Report/index.html) | [5.22%](https://zisoft-jmeter.s3-us-west-2.amazonaws.com/Tests/t2.medium/40user/Report/index.html)| [10.64%](https://zisoft-jmeter.s3-us-west-2.amazonaws.com/Tests/t2.medium/60user/Report/index.html)| - - - | - - -|- - - |- - - | - - - |
| t2.xlarge |  4 | 16 |  1 G |  [2.02%](https://zisoft-jmeter.s3-us-west-2.amazonaws.com/Tests/t2.xlarge/20user/Report/index.html) | [4.19%](https://zisoft-jmeter.s3-us-west-2.amazonaws.com/Tests/t2.large/40user/Report/index.html)| [5.21%](https://zisoft-jmeter.s3-us-west-2.amazonaws.com/Tests/t2.large/60user/Report/index.html)|[23.15%](https://zisoft-jmeter.s3-us-west-2.amazonaws.com/Tests/t2.large/80user/Report/index.html) | - - -|- - - |- - - | - - - |
| m5d.2xlarge |  8 | 32|  10 G |  [2.02%](https://zisoft-jmeter.s3-us-west-2.amazonaws.com/Tests/m5d.2xlarge/20user/Report/index.html) | [4.19%](https://zisoft-jmeter.s3-us-west-2.amazonaws.com/Tests/m5d.2xlarge/40user/Report/index.html)| [5.21%](https://zisoft-jmeter.s3-us-west-2.amazonaws.com/Tests/m5d.2xlarge/60user/Report/index.html)|[8.57%](https://zisoft-jmeter.s3-us-west-2.amazonaws.com/Tests/m5d.2xlarge/80user/Report/index.html) | [11.17%](https://zisoft-jmeter.s3-us-west-2.amazonaws.com/Tests/m5d.2xlarge/100user/Report/index.html)|- - - |- - - | - - - |
| m5d.4xlarge |  16 | 64|  10 G |  [2.02%](https://zisoft-jmeter.s3-us-west-2.amazonaws.com/Tests/m5d.4xlarge/20user/Report/index.html) | [4.19%](https://zisoft-jmeter.s3-us-west-2.amazonaws.com/Tests/m5d.4xlarge/40user/Report/index.html)| [5.21%](https://zisoft-jmeter.s3-us-west-2.amazonaws.com/Tests/m5d.4xlarge/60user/Report/index.html)|[8.57%](https://zisoft-jmeter.s3-us-west-2.amazonaws.com/Tests/m5d.4xlarge/80user/Report/index.html) | [11.17%](https://zisoft-jmeter.s3-us-west-2.amazonaws.com/Tests/m5d.4xlarge/100user/Report/index.html)|[11.73%](https://zisoft-jmeter.s3-us-west-2.amazonaws.com/Tests/m5d.4xlarge/200user/Report/index.html) |[12.01%](https://zisoft-jmeter.s3-us-west-2.amazonaws.com/Tests/m5d.4xlarge/300user/Report/index.html) | [33.38%](https://zisoft-jmeter.s3-us-west-2.amazonaws.com/Tests/m5d.4xlarge/400user/Report/index.html) |
| m5d.8xlarge |  32 | 128|  10 G |  [2.02%](https://zisoft-jmeter.s3-us-west-2.amazonaws.com/Tests/m5d.8xlarge/20user/Report/index.html) | [4.19%](https://zisoft-jmeter.s3-us-west-2.amazonaws.com/Tests/m5d.8xlarge/40user/Report/index.html)| [5.21%](https://zisoft-jmeter.s3-us-west-2.amazonaws.com/Tests/m5d.8xlarge/60user/Report/index.html)|[8.57%](https://zisoft-jmeter.s3-us-west-2.amazonaws.com/Tests/m5d.8xlarge/80user/Report/index.html) | [11.17%](https://zisoft-jmeter.s3-us-west-2.amazonaws.com/Tests/m5d.8xlarge/100user/Report/index.html)|[11.73%](https://zisoft-jmeter.s3-us-west-2.amazonaws.com/Tests/m5d.8xlarge/200user/Report/index.html) |[12.01%](https://zisoft-jmeter.s3-us-west-2.amazonaws.com/Tests/m5d.8xlarge/300user/Report/index.html) | [35.38%](https://zisoft-jmeter.s3-us-west-2.amazonaws.com/Tests/m5d.8xlarge/400user/Report/index.html)|


#
# ZiSoft  Awareness Server Sizing

1.
  1. Overview
  2. General Environment Sizing Notes
  3. Zisoft Application Server Sizing
  4. Calculating Hardware Requirements

1.
  1.
    1.  Total Memory Required Calculation
    2. Total Minimum Servers Required Calculation
    3. Memory Per Server Calculation
    4. CPU Core/Thread Per Server Minimum
    5. Data Transfer

1.
  1. Estimate 5% Active Users Requirements



## Overview

ZiSoft Awareness is a flexible web-based application that is designed to accommodate both small-scale implementation in a single department and large-scale application in organizations with thousands of users. Large-scale execution, however, requires careful planning and an adequate setup to accommodate the processing, bandwidth and storage needs of the system.

## General Environment Sizing Notes

ZiSoft Awareness is a data intensive platform. As such, the majority of the workload is usually dependent on the database environment. A properly tuned database environment is an absolute requirement for a production environment in ZiSoft Awareness. Many of the sizings detailed will be focused on data storage.

ZiSoft Awareness is used in various enterprise environments with different use cases. The Best Practices described below is not a one size fit all solution. Please take your use cases into account and use your best judgement to determine the best architecture solution.







## ZiSoft Application Server  Sizing and Deployment

The key to any server sizing project is to determine and understand the guidelines and types of workloads involved when running on a large-scale. Read the following guidelines below to help accurately evaluate your system requirements:

**Process Capability and Memory**

- Estimate the number of cases to be created per day. The number of processes created in a day has an effect on the performance of Zisoft Awareness, which is why its important to have an estimate before sizing the server.
- Consider the total number of nominal users that are expected to be using Zisoft Awareness ( 250,000 users )
- Use a web application server tuned for medium CPU and memory capacity.
- Depending on the level of redundancy security the customer requires, the production web application server cluster should at LEAST support one server being unavailable. This means the other remaining servers should have surplus CPU/RAM capacity to handle the extra load if this occurs.
For example, if there are two production servers, ideally 50% of one server&#39;s capacity should handle 100% of the volume at peak, at a minimum.
- Consider one CPU core (or hyper-thread) to every 4 gigabytes of memory.
  - For example, for a web application server that has 64GB of memory, a 16 thread/core processing environment is suggested.
  - Assume a maximum allowed size per server to be 128GB of memory, with a minimum of 32 thread processing.
  - Assume a minimum base frequency of 2.4GHz
- Consider dedicating 64MB for one active user at a time.
  - This value might change depending on memory requirements for certain processes, etc.
  - This value is based on the memory\_limit in PHP&#39;s configuration file and should also account for the overhead web server memory requirements.
  - For the total amount of users, ensure that there is a buffer that allows for 30% spikes at any time.

**Network Speed**

- These servers should have gigabit network interfaces and should be local to the shared resources of the load balancer and dependencies (file server, databases and caching). Ensure that your router and Internet bandwidth supports your expected incoming and outgoing traffic.

## Calculating Hardware Requirements

The sections below provide guidance on how to calculate hardware requirements, taking various considerations into account.

### Total Memory Required Calculation

(pu \* mmpu \* 1.3) / 2048 = tm

Where:

- **pu:** Peak number of Active users.
- **mmpu:** Maximum amount of memory in megabytes per user.
- **1.3:** Allows for 30% growth/spikes at peak.
- **tm:** Total memory required for this environment.

### Total Minimum Servers Required Calculation

(tm \* rl) / 2 \* mps = sc \&gt; 2 (sc rounded up) or rl = ms

Where:

- **tm:** Total memory required.
- **rl:** The redundancy level specified (a minimum of 2). There is always a minimum level of redundancy required.
- **mps:** Maximum amount of memory per server the customer can acquire (a maximum of 128GB is recommended).
- **sc:** Total server count. Round up sc to ensure an adequate number of servers.
- **mw:** Minimum number of servers required.

### Memory Per Server Calculation

(tm \* rl) / (2 \* ms ) = (mmps rounded up to whole number divisible by 8) = mps

Where:

- **tm:** Total memory required.
- **rl:** Redundancy level required by customer.
- **ms:** Minimum number of servers required.
- **mmps:** Minimum amount of memory required per server.
- **mps:** The value of mmps rounded up to a whole number divisible by 8.

### CPU Core/Thread Per Server Minimum

(mps / 4) = cps

- **mps:** Memory per server.
- **cps:** Number of cores/threads per server.

### Data Transfer

(users \* adt / cput) = dt

- **Users :** Number of Active users
- **Adt**  = (high transfer session data  \* 0.33) +  (Avg transfer session data  \* 0.33) + (low transfer session data  \* 0.33) / 3 =  ( 100 MB \* 0.33) + ( 40 MB \* 0.33 )+ (1 MB \* 0.33 ) / 3 = 15.51 MB
- **cput:**  cpu  session tme out  = 30 s

Estimation HW Sizing

#### Estimate HW Sizing when Active users = 5%

Active users = Concurrent users who access the application at CPUT (server CPU Session time out 30s)

Active users = 250,000 \* 5 / 100 = 12500

Estimate 5%  has an estimated 12500 simultaneous users at their peak time. They&#39;ve stated they can only support servers with a max memory of 128 GB. They request that they have a redundancy level of 3 ( 30 % of their fleet could be down at any time). Memory per user will be 64MB).

| **Parameter Levels** | **Calculation** | **Result** |
| --- | --- | --- |---|---|---| 
| Memory Calculation: | (12500 \* 64 \* 1.3) / 2048 = **507.81 GB** | 512 GB |
| Server  ( VM ) Count Calculation: | (512\* 3) / 128 = 12 | 12 server (VM) |
| Minimum Memory per server: | (512 \* 3) / ( 2 \*12) = 64 rounded up to a whole number divisible by 8 = 64 **GB** | 64 GB per server. |
| CPU Cores per server: | 64/ 4 = 16 | 16 cores |
| **Total Data Transfer / sec** | 12500 \* 15.51 MB / CPUT ( 30 ) = 6463.5MB = 6.5 GB | 6.5 GB/s |
| **Data Transfer / server (VM)** | 6.5 GB  / 12 | 541 MB/s |

