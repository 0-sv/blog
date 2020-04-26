---
title: "My Crossover Interview"
date: 2020-04-22T11:18:25+07:00
draft: false
toc: false
images:
tags: 
  - career
  - cv
  - experience
---
I applied to CrossOver last month. They have an automated interview process, where you have to pass a list of tests like basic cognitive aptitude and language skills.

It seemed like I passed all of the tests, however, after submitting my final test I heard that my score wasn't sufficient to become a Product Knowledge Curator to earn that sweet American salary of $100K a year.

![alt let-me-in](https://i.redd.it/tbdw89vj27j31.png)

My final test consisted of creating three product knowledge articles based on customer inquiries. I hope they can be treated as a good sample for anyone. Any feedback is welcome as well, as I have no experience with this sort of work, nor could I found any proper resources on the internet.

# Article #1
Issue {#h.k8yr88jtekzq .c7}
-----

After installing Cloudflare, the usage of an IP address outside a
whitelisted range of IP addresses is unavailable. This happens, for
instance, in the case of downloading a data feed from the website of the
customer.

Root cause {#h.keazvfit2kqd .c7}
----------

The customer opened this ticket by announcing the installation of
Cloudflare. The Cloudflare product is known as a “Content Delivery
Network” (CDN). It’s main usage is serving static content, however,
customers also rely on it for [enhanced security, performance and
reliability](https://www.google.com/url?q=https://support.cloudflare.com/hc/en-us/articles/205177068&sa=D&ust=1587533068987000).

Cloudflare stops malicious traffic before it reaches the origin web
server; first, the origin IP address is “masked” (a DNS lookup returns a
Cloudflare IP address). The second step -- our main concern -- is
Cloudflare's’ analysis of the resources requested. If a visitor requests
a high volume of resources over a short period of time, then that
visitor can be marked as malicious traffic.

You can imagine that downloading a data feed in any interval might be
considered as suspicious and, subsequently, malicious traffic.
Whitelisting a range of IP addresses with server-defined firewall rules
marks traffic as unsuspicious. This is opposed to blacklisting a range
of IP addresses, in which case the server has a range of IP addresses
that are marked suspicious already and are therefore challenged or
blocked. In the Cloudflare configuration, both are known as [configuring
IP access
rules](https://www.google.com/url?q=https://support.cloudflare.com/hc/en-us/articles/217074967-Configuring-IP-Access-Rules&sa=D&ust=1587533068987000).
In IP access rules, visitors that are whitelisted have precedence over
blacklists.

We’ve agreed with the customer to download a data feed from their
website. Since it’s their website that’s using Cloudflare, they are
“privileged” (as in: having the rights of access) to configure
Cloudflare. Moreover, our role is to download their data feed, so we are
responsible for outbound traffic to their Cloudflare IP address. This
means that we have to supply our customer with a range of IP addresses
that they can use in their Cloudflare configuration.

We can supply this range of IP addresses by browsing to endpoint
https://api.crossover.com/12345678. An API request to this endpoint
should return the IP addresses that should be whitelisted for use of
Cloudflare. This endpoint is secured with basic authentication. The
customer should have an application available for monitoring changes to
this file.

Resolution {#h.glhs6ahcgeb8 .c7}
----------

### Create a HTTP request to the endpoint {#h.9nh7dhmru0rk .c14}

Copy the following code (or browse to
/shared-drive/data/cloudflare-ip.js):

    var data = ["192.168.0.0", "192.168.0.1"];                               
                                                                        
    var xhr = new XMLHttpRequest();                                          
                                                                            
    xhr.withCredentials = true;                                              
                                                                            
    xhr.addEventListener("readystatechange", function () {                   
                                                                            
     if (this.readyState === this.DONE) {                                    
                                                                            
       console.log(this.responseText);                                       
                                                                            
     }                                                                       
                                                                            
    });                                                                      
                                                                            
    xhr.open("GET", "https://api.crossover.com/12345678");                   
                                                                            
    xhr.setRequestHeader("cloudflare-ip", "1");                              
                                                                            
    xhr.setRequestHeader("authorization", "Basic dXNlcjoxMjM0");             
                                                                            
    xhr.send(data);   

### Share the IP addresses with the customer {#h.9oe861vd1qb .c14}

You can either show the customer how to make a HTTP request to this
endpoint, or supply them with the range by making the request yourself
and copying over the IP addresses.

Multiple choice quiz {#h.vgz59dblomqs .c7}
--------------------

### Q1: For which of the following reasons would you use a CDN? (2 points) {#h.3zt35tjcja1w .c14}

1.  Serving static content
2.  Performance
3.  Security
4.  All of the above

### Q2: What happens when you lookup the DNS configuration for a Cloudflare server? (3 points) {#h.glzqh7asrjuo .c14}

1.  The Cloudflare server returns the IP address of the origin server
2.  The Cloudflare server returns the IP address of the Cloudflare
    server
3.  The Cloudflare server returns the FQDN of the origin server
4.  The Cloudflare server returns the FQDN of the Cloudflare server

### Q3: Who is responsible for whitelisting IP addresses in the Cloudflare configuration? (4 points) {#h.o4p39ts22gmw .c14}

1.  The administrator of the Cloudflare server
2.  The administrator of the origin web server
3.  The administrator of the web client
4.  All of the above 

### Q4: Where do we find the endpoint for the whitelisted IP addresses? (1 point) {#h.23fx3xg0h7ph .c14}

1.  [https://crossover.com/api/12345678](https://www.google.com/url?q=https://crossover.com/api/12345678&sa=D&ust=1587533068994000)
2.  [https://crossover.com/whitelisted-ip-addresses](https://www.google.com/url?q=https://crossover.com/whitelisted-ip-addresses&sa=D&ust=1587533068994000)
3.  [https://api.crossover.com/12345678](https://www.google.com/url?q=https://api.crossover.com/12345678&sa=D&ust=1587533068994000)
4.  [https://api.crossover.com/whitelisted-ip-addresses](https://www.google.com/url?q=https://api.crossover.com/whitelisted-ip-addresses&sa=D&ust=1587533068994000) 

# Article #2
Issue {#h.k8yr88jtekzq .c11}
-----

The index for the fakesite.com fails. The customer is unable to update
the product catalog -- one beneficiary of the index -- which includes
pricing.

Root cause {#h.keazvfit2kqd .c11}
----------

Indexing is a common technique to decrease query time for a database. An
index is applied to rows with [specific columns to increase search
performance](https://www.google.com/url?q=https://dev.mysql.com/doc/refman/8.0/en/mysql-indexes.html&sa=D&ust=1587533093395000).
If there’s no index available, then the database engine has to start a
query from the first row until it reaches the row that matches the
query. A query can also start the search from the index, decreasing the
query time to logarithmic time complexity (O(log(t)n)).

Fakesite.com has invested in a custom index by SLI
(com.sli.searchbuilder), a Java application. This index fails because it
“expects single but array was returned”. Specifically, there’s one entry
that has duplicated \<review\> information. In other words, there’s one
item number “24140-206” that has two entry keys: “826” and “1987”. We
can reproduce the error by returning an array [“826”, “1987”].

It’s possible to specify two keys because there’s an issue with the
translation module. This module is called by the previously mentioned
SearchBuilder module. The first function in the call stack is the
setVariables function by the TranslationFunction module. Let’s assume
that this function takes the database entry (row) as input, and returns
a Java data structure. It throws an error, then, because the variable
for product reviews keys should be a single and not an array.

Furthermore, as documented in the original troubleshooting article,
there’s not enough information about the location of the Select One From
Array Module. This module could handle an array as input by selecting
one value in that array instead of the array itself. We can’t locate
this module because it’s “Use If” has multiple connections. It has
multiple connections because the original software engineer has chosen
for this implementation for various reasons that are outside of the
scope of this article.

We could resolve the solution permanently by modifying this function and
wrap the present logic in a conditional logic block. We might be able to
check the parameters for the presence of an array of keys instead. In a
quick patch, we could take the first item in the array by default; this
might be the first product review written.

In a rewrite, which should take longer and have customer approval, we
should either build the application to support multiple product reviews
or deny any attempt at entering multiple product reviews. This will
prevent the issue mentioned in this article to happen again.

Resolution {#h.glhs6ahcgeb8 .c11}
----------

### Troubleshooting steps {#h.ebtfn16dtn5f .c13}

1.  Browse to
    [https://sb1.sli-systems.com/fakesiteType=PRODUCTION](https://www.google.com/url?q=https://sb1.sli-systems.com/fakesiteType%3DPRODUCTION&sa=D&ust=1587533093397000)
2.  Click on the translation module.
3.  Click on the “Run From” button.
4.  Open the log; you can find this link in the right menu on the SB
    screen.
5.  You will see the error reproduced: “Expected Single but Array was
    returned at field Value with id:123456789.
6.  This id is important: copy it, and visit the Translation module on
    the translation page.
7.  Click on the Find button (top of the screen), paste the id from the
    error. You will see that the module is highlighted with the issue.
8.  Check the module, it should be “num\_reviews”. Check the source it’s
    pulling data from.
9.  Click on the “view output” button from the consolidation module
    wired before the translation module.
10. Search using these filters: review/Reviewcount has “Minimum matches
    per Entry”: 2.
11. The resulting product has two reviews.
12. Inform the customer to delete this product.

Multiple choice quiz {#h.vgz59dblomqs .c11}
--------------------

### Q1: What is NOT a purpose of a database index? (1 point) {#h.kahwhg2r02jj .c13}

1.  Increase performance of a database engine
2.  Decrease query time for a database engine
3.  Decrease the time complexity for a database engine
4.  Decrease the space complexity for a database engine

### Q2: Why does the index fail for the slibuilder application? (2 points) {#h.y0ouj9umo70y .c13}

1.  The translation module returns one product review but expects two
2.  The translation module returns two product reviews but expects one
3.  The translation module returns one array of product reviews but
    expects two arrays
4.  The translation module returns two arrays of product reviews but
    expects one array

### Q3: What is a quick way to troubleshoot this problem? (2 points) {#h.apr8lkulmsia .c13}

1.  Find and remove one product review
2.  Find and remove two product reviews
3.  Find and remove product reviews until there’s only one left
4.  Find and remove all product reviews

### Q4: What is not a possible long-term solution for this problem? (3 points) {#h.ecjrrdlg1f3b .c13}

1.  Rewrite the logic to support two product reviews
2.  Rewrite the Select One From Array Module
3.  Wrap the logic in a conditional logic block
4.  Apply the quick way to troubleshoot this problem

# Article #3

Issue {#h.k8yr88jtekzq .c8}
-----

The customer has reported a high memory footprint on the LGP server.

Root cause {#h.keazvfit2kqd .c8}
----------

A customer has opened a ticket as a follow-up to a previous request
(\#1117416 -- “Memory up to 98 percent on LGP server”). The previous
request has not been adequately satisfied, ie. there’s still no
temporary or permanent resolution for the memory usage on the LGP
server.

There’s not enough information to conclude that the problem resolved
itself automatically previous time, and hence no intervention by the L1
or L2 was necessary. However, it seems likely that the problem has
resolved itself by nature of memory. That’s because with 98%+ usage, the
process might have been OOM-killed. There is only data available from
day-by-day, so we don’t know the actual memory usage on a given day.
This is obviously a report run by the sar command, so next time it might
be more useful to report on real-time metrics.

Let’s not assume that understanding one metric, memory usage, is key to
diagnosing the problem. One distinction we can’t infer from this table
is the respective virtual and physical memory. Moreover, we have no
information about what application is responsible for which part of the
memory. If this is a case of virtual memory over-allocation, we could
tune that behavior. Another matter is the difference between active and
inactive memory.

Furthermore, there’s no indication that there is actually problem. It
looks like there’s efficient use of memory if we don’t know the
respective resident memory and cache sizes. There has not been any
report of system failure. It might be a good idea to do some further
reporting to assess whether there’s an issue, and if so, what we might
provide as resolution for the customer request.

Resolution {#h.glhs6ahcgeb8 .c8}
----------

### In-depth reporting {#h.2epbdqtnj7hp .c15}

Please run:

-   free
-   cat /proc/meminfo
-   vmstat 1 3 5
-   top
-   ps -eo pid,user,comm,size,vsize,rss
-   sar -r 1 3 5
-   sar -S 1 3 5
-   smem

And report the results, so we can get more information about this issue.
We should also keep the customer up-to-date on this issue.

Multiple choice quiz {#h.vgz59dblomqs .c8}
--------------------

### Q1: High memory is always a problem {#h.t260tjp4kig9 .c15}

1.  True
2.  False

### Q2: There’s enough information to solve this problem {#h.nnar68hgqxcc .c15}

1.  True
2.  False

### Q3: The LGP server has experienced failures since the high memory usage was observed {#h.unio2xv8fu9w .c15}

1.  True
2.  False

### Q4: What command generated this report? {#h.esywz97jh0ud .c15}

1.  cat /proc/meminfo
2.  top
3.  sar
4.  smem