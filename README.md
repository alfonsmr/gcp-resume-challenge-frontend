# gcp-resume-challenge-frontend
Google Cloud Platform (GCP) Resume Challenge

https://acloudguru.com/blog/engineering/cloudguruchallenge-your-resume-on-gcp

Bibliografy:

https://cloud.google.com/storage/docs/hosting-static-website
https://github.com/jbub/ghostwriter
https://themes.gohugo.io/themes/ghostwriter/
https://qualityandinnovation.com/2020/12/23/pushing-your-hugo-site-to-a-gcs-bucket-part-3/




Process

Create Hugo site
make hugo

gsutil cp -r * gs://gcp-resume-challenge
gsutil web set -m index.html -e 404.html gs://gcp-resume-challenge

Load balancer with SSL certificate

Go to the Load balancing page in the Google Cloud Console. https://console.cloud.google.com/networking/loadbalancing/
Under HTTP(S) load balancing, click Start configuration.
Select From Internet to my VMs and click Continue.
Give your load balancer a Name, such as example-lb. (Enable Compute Egine API if asked)

Configuring the backend
Click Backend configuration.
In the Create or select backend services & backend buckets dropdown, go to the Backend buckets sub-menu, and click the Create a backend bucket option.
Choose a Name for the backend bucket, such as example-bucket.
Click Browse under Cloud Storage bucket.
Select the my-static-assets bucket and click Select.
If you want to use Cloud CDN, select the checkbox for Enable Cloud CDN. Leave the Cache mode selection as Cache static content. Note that Cloud CDN may incur additional costs.
Click Create.

Note: To redirect traffic from HTTP to HTTPS, you need to set up an additional HTTP load balancer with a redirect setting in the URL map. For instructions, see Setting up HTTP-to-HTTPS redirect for external HTTP(S) load balancers.
