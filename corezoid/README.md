[![N|Corezoid](https://api.corezoid.com/logo/logo_big_small.png)](https://corezoid.com/)  

Corezoid Docs - https://doc.corezoid.com/  

Corezoid change log - https://doc.corezoid.com/docs/release-notes  

## Installation notes:  

- Just clone repo end ``` cd corezoid ``` edit values.yaml and ```helm install corezoid-public -n public .```  

## Upgrading notes:
```helm upgrade corezoid-public -n public .```  

#### Enabling SAML encryption:  
Go to google mobile application https://admin.google.com/u/1/ac/apps/unified and click «add SAML application»  
Fill name and choose icon --next-->  
skip next step with metadata --next-->  
Fill URL ACS: https://{{ .Values.global.subdomain}}.{{ .Values.global.domain }}/auth2/saml/google_saml_1/return  
Object ID: google_saml_1.{{ .Values.global.subdomain}}.{{ .Values.global.domain }}  
Select Title identifier format: X509_Subj --next-->  
Attributes->add  
firstname  -> first_name  
lastname  - > last_name --Done-->  

On mobile page click download metadata  
And move downloaded file to ./templates folder with name GoogleIDPMetadata.xml for first auth method or GoogleIDPMetadataSupport.xml for second «hidden» auth method, for hidden auth  - use link https://{{ .Values.global.subdomain}}.{{ .Values.global.domain }}/support  
Don’t forget to enable service (mobileapp) on User access menu - enable status service: enable for all  


#### Enabling Enigma encryption:  
- See [ENIGMA.md](ENIGMA.md)  

#### Dependencies:  
#####Testing on Kubernetes version 1.22 and helm v3  
#####Supported stateful versions:  
- Postgresql 13.3  
- Redis 3.2  
- Elasticsearch 7.17.5  
- RabbitMQ 3.9  
---

