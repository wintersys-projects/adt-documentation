MULTI REGION DEPLOYMENTS

If you want to deploy using multiple regions you will need to set

>     MULTI_REGION="1"

in your template(s) for each region.

You will also need to set a primary region by having one of the regions you are deploying to set

>     PRIMARY_REGION="1"

and all the additional regions set 


>     PRIMARY_REGION="0"


When making a multi region deployment you will need to provide the public DBaaS endpoint to all regions which are not the primary domain. The primary region should be set such that the region for your webservers of your primary region is the same region/VPC/provider as the webservers in your primary region. 

Every region will need to provision its own reverse proxy machines because multi-region deployments are only possible when each individual region uses reverse proxies to forward traffic to the fleet of webservers for that region. 
