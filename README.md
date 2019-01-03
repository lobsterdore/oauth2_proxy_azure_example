# oauth2_proxy Azure AD example

End to end example using Azure AD with oauth2 proxy to provide 
authentication via Nginx.

## How to use

Create an AD application in Azure, giving the following URL as the redirect:

```
http://localhost:8080/oauth2/callback
```

Make a note of your Client ID and Tenant ID, now generate a new 
client secret and note down it's value.

Create a file called vars.yml with the following contents:

```YAML
---
# vars.yml

oauth2_proxy_azure_tenant: "[YOUR AD TENANT ID]"
oauth2_proxy_client_id: "[YOUR AD CLIENT ID]"
oauth2_proxy_client_secret: "[YOUR AD CLIENT SECRET]"
oauth2_proxy_cookie_secret: "[A RANDOM STRING]"
oauth2_proxy_email_domain: "[EMAIL ADDRESS DOMAIN TO ALLOW ACCESS FOR]"
```

Now you can bring up the instance using vagrant, note that you
must have Ansible 2.6+ installed.

Once up you should be able to hit http://localhost:8080 on your 
host machine, this should redirect you to the AD login page. Once
you have logged in you should see the default Nginx welcome page.