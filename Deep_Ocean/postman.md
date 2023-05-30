# The introduction of Postman
## Agenda
- Overview (5 mins)
- The basic features we could use it (10 mins)
- Quick Demo (10 mins)
- Q&A ( 5 mins)
## Overview
![image](https://github.com/LenChang/Tech_Sharing/assets/9037287/d3e7ad80-f7a9-414b-9af6-393121ae2b5a)
![image](https://github.com/LenChang/Tech_Sharing/assets/9037287/933b59e6-a5a5-4165-8957-942035c2bff0)
### API tool comparison
![image](https://github.com/LenChang/Tech_Sharing/assets/9037287/49ec326a-1352-4aef-bf96-1534811dc4cd)
- https://www.postman.com/
- https://insomnia.rest/
- https://www.knowi.com/
#### Conclusion
If you are a developer looking for an API tool with many features, choose Postman. Postman supports integration with a number of apps but you can request them to build an integration for a specific app. The tool requires you to write code to accomplish most of the tasks.
- https://www.postman.com/product/integrations/

Insomnia on the other hand is an API tool with few features. It creates integrations using plugins and you can create your own plugins for specific use cases. It also requires you to write code to accomplish some tasks.

If you are looking for a full-fledged BI solution on top of API-based data and other sources, choose Knowi.
## The basic features we could use it
### Create and test your API
![image](https://github.com/LenChang/Tech_Sharing/assets/9037287/b8a646d1-fbb3-427f-9c22-66dcdde16eb9)
### Group your API  with same setting or configuration
![image](https://github.com/LenChang/Tech_Sharing/assets/9037287/6b185150-551c-44cb-9a03-e48fcb959f71)
### Keep samples of your API
![image](https://github.com/LenChang/Tech_Sharing/assets/9037287/9d5c2875-ba6a-4416-b756-a6328d8834f2)
### Write tests to protect your API result (JavaScript)
![image](https://github.com/LenChang/Tech_Sharing/assets/9037287/7d936c35-9689-4648-8a73-4e691720058b)
### Monitor your API healthy
![image](https://github.com/LenChang/Tech_Sharing/assets/9037287/dd9fe87f-f8c7-4c88-b095-aa7831cae62f)
### Share your configuration
![image](https://github.com/LenChang/Tech_Sharing/assets/9037287/ba65ae32-08ae-41ed-908e-06f2abe60080)

## Quick Demo
### Topic: Copy this api to Postman and implement all features as above
- https://10.8.2.105:8000/atadc/docs#/V2/get_image_with_label_v2_view_lot_image_with_label_get
### Steps
1. Create a collection for your project
1. Find the API address, query parameters and authorization key and put those on the right way
1. Get the result and save the result as a sample
1. Make the general string to be the config environment
1. Write tests to protect your API
1. Create a monitor to monitor your API healthy

# Reference
- https://medium.com/geekculture/postman-vs-insomnia-vs-knowi-4ed2e9c6d1b5#28cc
- https://www.elastic.co/guide/en/observability/current/apm.html
