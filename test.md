## **ZiSoft Awareness HW Sizing**

ZiSoft Awareness is a flexible web-based application that is designed to accommodate both small-scale implementation in a single department and large-scale application in organizations with thousands of users. Large-scale execution, however, requires careful planning and an adequate setup to accommodate the processing, bandwidth and storage needs of the system.

*** General Environment Sizing Notes ***

ZiSoft Awareness is a data intensive platform. As such, the majority of the workload is usually dependent on the database environment. A properly tuned database environment is an absolute requirement for a production environment in ZiSoft Awareness. Many of the sizings detailed will be focused on data storage.

ZiSoft Awareness is used in various enterprise environments with different use cases. The Best Practices described below is not a one size fit all solution. Please take your use cases into account and use your best judgement to determine the best architecture solution.


***ZiSoft Application Server  Sizing and Deployment***

The key to any server sizing project is to determine and understand the guidelines and types of workloads involved when running on a large-scale. Read the following guidelines below to help accurately evaluate your system requirements:

***Process Capability and Memory***

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

***Network Speed***

- These servers should have gigabit network interfaces and should be local to the shared resources of the load balancer and dependencies (file server, databases and caching). Ensure that your router and Internet bandwidth supports your expected incoming and outgoing traffic.

***Calculating Hardware Requirements***

The sections below provide guidance on how to calculate hardware requirements, taking various considerations into account.

*** Total Memory Required Calculation***

(pu \* mmpu \* 1.3) / 2048 = tm

Where:

- **pu:** Peak number of Active users.
- **mmpu:** Maximum amount of memory in megabytes per user.
- **1.3:** Allows for 30% growth/spikes at peak.
- **tm:** Total memory required for this environment.

***Total Minimum Servers Required Calculation***

(tm \* rl) / 2 \* mps = sc \&gt; 2 (sc rounded up) or rl = ms

Where:

- **tm:** Total memory required.
- **rl:** The redundancy level specified (a minimum of 2). There is always a minimum level of redundancy required.
- **mps:** Maximum amount of memory per server the customer can acquire (a maximum of 128GB is recommended).
- **sc:** Total server count. Round up sc to ensure an adequate number of servers.
- **mw:** Minimum number of servers required.

***Memory Per Server Calculation***

(tm \* rl) / (2 \* ms ) = (mmps rounded up to whole number divisible by 8) = mps

Where:

- **tm:** Total memory required.
- **rl:** Redundancy level required by customer.
- **ms:** Minimum number of servers required.
- **mmps:** Minimum amount of memory required per server.
- **mps:** The value of mmps rounded up to a whole number divisible by 8.

*** CPU Core/Thread Per Server Minimum***

(mps / 4) = cps

- **mps:** Memory per server.
- **cps:** Number of cores/threads per server.

*** Data Transfer***

(users \* adt / cput) = dt

- **Users :** Number of Active users
- **Adt**  = (high transfer session data  \* 0.33) +  (Avg transfer session data  \* 0.33) + (low transfer session data  \* 0.33) / 3 =  ( 100 MB \* 0.33) + ( 40 MB \* 0.33 )+ (1 MB \* 0.33 ) / 3 = 15.51 MB
- **cput:**  cpu  session tme out  = 30 s

Estimation HW Sizing

 Estimate HW Sizing when Active users = 5%

Active users = Concurrent users who access the application at CPUT (server CPU Session time out 30s)

Active users = Total number of users \* 5 / 100 = N

Estimate 5%  has an estimated n simultaneous users at their peak time. They&#39;ve stated they can only support servers with a max memory of 128 GB. They request that they have a redundancy level of 3 ( 30 % of their fleet could be down at any time). Memory per user will be 64MB).


