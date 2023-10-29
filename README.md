PROJECT WITH HaProxy LB >> Three Apache Webservers hosted on AWS EC2 and DNS configured on GoDaddy.com  
VMs are prepared by Cloudformation  

#Haproxy is configured to run the movement on acl rules  
#frontend main  
#   bind *:80  
#   acl is_devopsproject hdr(host) -i devopsproject.pl www.devopsproject.pl  
#   use_backend http_backend if is_devopsproject  
#   acl issub_devopsproject hdr(host) -i sub.devopsproject.pl  
#   use_backend http_backend_sub if issub_devopsproject  
#backend http_backend  
#   balance     roundrobin  
#   server  18.209.22.173 18.209.22.173:80 check  
#   server  54.82.240.204 54.82.240.204:80 check  
#backend http_backend_sub  
#   balance     roundrobin  
#   server  18.208.219.219 18.208.219.219:80 check  


Domain name:devopsproject.pl

1.) Run Cloudformation script on AWS  
  -4 instances based on AMAZON AWS AMI  
  -Ports 80 and 22 opened  
  -install apache on 3 of them  
  -install HaProxy on one of them    
2.) Configure all of them based on .cfg files    
  - for apache create basic index.html files  
  - for haProxy make changes in cfg file(acl rules for 2 domains and 1 subdomain)  
3.) Add records on GoDaddy.com. Lets say our LB Public IP is >18.215.158.127  
- add RECORD     A    @         IP EC2apache1 #18.215.158.127  
- add RECORD     A    www       IP EC2apache2 #18.215.158.127  
- add RECORD     A    subdomain IP EC2apache2 #18.215.158.127  



