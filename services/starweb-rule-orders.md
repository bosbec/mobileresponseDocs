**Requirements**

The following keys need to be entered in Account Settings:

* `starweb_shop_name`
* `starweb_client_id`
* `starweb_client_secret`
* `starweb_group_key`
* `rule_api_key`

A channel also needs to be created and selected in the triggers "Newsletter" and "order-created."

Ensure that the "get categories" trigger scheduling is set, preferably once a day.

Also, check that the number of jobs the workflow can run is high enough.

To fetch historical orders:

* Check the date in job_72. The default is 30 days back.
* Run the "get orders" trigger.

If you have any questions, don't hesitate to contact support.
