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


