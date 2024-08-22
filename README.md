# Cloudflare Minio Docker
I am making this repository for people like me who spent way too much time troubleshooting using Minio running on docker through Cloudflare. 

## Cloudflare blocks port 9000/9001 through cloudflare's proxy
Cloudflare blocks any port that isn't an http or https port. Yes that means things like 22, and in Minio's case 9000 and 9001. 

## Can I just change the ports?? 
While yes, you can change the ports for Minio to HTTPS ports (I used 2087 and 2053, getting it to work) it is not allowed in section 2.8 in Terms of Service for free plans.  

## What if I just point 80 then internal 9000 or 9001?
This seems to only work for the API (9000) or console (9001) directly but not both at the same time, as connecting to 9000 via browser will throw you to 9001. I wasn't able to get haproxy to do it either, though it _might_ be possible. But this is techinically not allowed in Cloudflare's TOS for free plans. 
  


## Ok...then what can I do??? 
You can route it through Cloudflare without Cloudflare proxy on (the cloud grayed out). This will allow connections not on http or https ports. HOWEVER, this will expose your ip...so generally not good for homelab setups. It also means you can't use Cloudflare certs on your minio setup. 
