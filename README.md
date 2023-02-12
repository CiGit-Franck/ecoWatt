# ecoWatt
*Une interface simple sous Node-Red avec alerte par mail*
### Pré-requis
>- Disposer d'un compte [RTE](https://data.rte-france.com/#)
>- [Node-Red](https://nodered.org/docs/getting-started/local) (avec modules : node-red-dashboard, node-red-node-email, node-red-contrib-cron-plus)
### Partie Node-Red
>1-Import des flows (src/RTE.json & src/mail.json)

>![flow](/img/nodes.PNG)

>![dashboard](/img/dashboard.PNG)

>2-Configuration des nodes RTE & Mail
>- RTE : récuperer la *[key-64](https://data.rte-france.com/group/guest/apps/-/apps/984443/node-red-ECOWATT)*
>>![key-64](/img/key64.png)

>>![Token](/img/token.png)

>- __Token__
>>- url: https://digital.iservices.rte-france.com/token/oauth/
>>- method: __POST__
>>- headers:
>>>- __Authorization: Basic__ *key-64* obtenu sur le site RTE"
>>>- __Content-Type: application/x-www-form-urlencoded__

>- __Request__
>>- url: https://digital.iservices.rte-france.com/open_api/ecowatt/v4/signals
>>- method: __GET__
>>- headers:
>>>- __Authorization: Basic__ *"access_token"*
>>>- __Content-Type: application/x-www-form-urlencoded__

>- Mail : 
>>![Mail](/img/mail.png)

>3-Définir les crontab
>>2 fois par jour -> 0 15 14,2 * * *
