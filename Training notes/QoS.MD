## What is QoS?
QOS = Quality of Service
This is a way to help alleviate congestion management. 

this is the default for traffic best effort or First in first out (FIFO).

## Characteristics of network traffic
There are four characteristics of network traffic.
- Bandwidth
  - Speed of link.
- Delay
  - is the time it takes for a packet to get from the source to the destination, this is called the one-way delay
  - round-trip delay is the time it takes to get from source to destination and back
- Jitter
  - This is the time between packets. This is what will make someone sound like a robot. 
  - This there is too much of a variation of jitter, Voice traffic will suffer.
- Loss
  - The amount of traffic lost. Generally shown as a percentage. 

### QoS Tools
The actual tools of QoS
- Classification and marking
  - This is for identifying and marking the traffic
  - One way to accomplish this is to use an access list
  - NBAR (Network Based Application Recognition ) is a application running on the router that will be able to identify traffic
- Queuing - Congestion Management
  - Instead one big queue like FIFO, we create multiple queues
    - A few different queuing options
      - Round-Robin scheduling
        - This one will send the a packet from one queue, then move to the next queue. 
        - This option doesnt really fix anything, its still FIFO but slightly broken up.
      - Weighted round robin
        - Here you will be able to set higher weight to a queue.
        - If you have 3 queues, you may send 10 packets from queue 1, 5 from queue 2, and 1 packet from queue 3. then start over at the begining.
        - This is better but maybe you really, REALLY care about queue 1 and you dont want to waste bandwidth on queue 3. This only kind of solves this issue. sure maybe you crank up queue 1 to 1000 Packets in the queue, but if the link is not congested you will always think queue 3 is slow. 
      - CBWFQ ( Class based weighted fair queuing)
        - This is generally the recommended way to perform queueing for cisco routers.
        - You can guarantee a minimum bandwidth to each class when there is congestion.
      - Low latency queuing (LLQ)
        - With LLQ you would allow traffic from one queue to be forwarded immediately. If the router sees this traffic, the router will now wait. The router will send the traffic immediately. 
        - IMPORTANT DETAIL - You must set a limit on this queue, otherwise the other queues may never send. when queues are full traffic is dropped.      
- Shaping and Policing
  - These two tools are used to limit traffic
  - Policing
    - Often used by ISP who must limit the bitrate to their customers
    - You may set a limit here and never allow more bandwidth out a link then you approve.
    - You may see a spike of data go above the allowed bandwidth. if this happens long enough is when the policer start to drop traffic.
    - You will see a traffic pattern here that will go up very high, get cut off and drop down. If you burst up to a 10 meg link up to 100 meg traffic will start to drop at the 10 meg link.

  - Shaping
    - This will level out the traffic. 
    - if you burst up to 100 megs from 10 megs traffic will do its best to hover at 10 megs and not drop as much traffic.
- Congestion Avoidance
  - These tools are used to manage loss and to reduce congestion