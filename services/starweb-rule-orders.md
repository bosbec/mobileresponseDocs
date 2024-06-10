**Installation**

Följande nycklar behöver läggas in på account settings:

* starweb_shop_name
* starweb_client_id
* starweb_client_secret
* starweb_group_key
* rule_api_key

En channel behöver även skapas och väljas i triggers "Newsletter" och "order-created".

Säkerställ att schemaläggning av get categories sätts, förslagsvis en gång om dagen.

Kolla även att antal jobs workflowet får köra är tillräckligt.

För att hämta in historiska ordrar:

* Kolla datum i job_72. Standard är 30 dagar bakåt.
* Kör get orders.
