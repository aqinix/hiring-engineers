### ENVIRONMENT SETUP

Used Ubuntu 16.04 linux VM via Vagran.

![002](https://user-images.githubusercontent.com/33669341/53703513-2fdfaf00-3e13-11e9-964c-7546da8440c6.PNG)

The datadog-agent status after installing agent in the host ubuntu-xenial.

![001](https://user-images.githubusercontent.com/33669341/53703664-d1b3cb80-3e14-11e9-9a92-3b05a1d6f33f.PNG)

### COLLECTING METRICS

Edit the agent config file and added the tag (first_tag).

![004](https://user-images.githubusercontent.com/33669341/53703973-d62db380-3e17-11e9-8097-268a970eff68.png)

Host Map with added tag.

![img001](https://user-images.githubusercontent.com/33669341/53703892-180a2a00-3e17-11e9-931f-35832252c3af.PNG)

Created custom checks with metric named (my_metrics) in the range 0 to 1000 and it's default interval time is 30 sec. Then it has been changed to 45 sec.

![005](https://user-images.githubusercontent.com/33669341/53704096-5c96c500-3e19-11e9-9fca-2ad3a00b3929.PNG)

The created custom check can be viewed in the 'datadog-agent status' as below,

![dtdg-check](https://user-images.githubusercontent.com/33669341/53704173-974d2d00-3e1a-11e9-89a5-fe17def7a647.PNG)

Initila interval time 5 sec for testing.

![custom_metrics](https://user-images.githubusercontent.com/33669341/53704131-f1012780-3e19-11e9-883c-3b7023021a63.PNG)

Then interval changed from 5 sec to 45 sec to have a clear view.

![collection interval from 5 to 45](https://user-images.githubusercontent.com/33669341/53704144-13934080-3e1a-11e9-8a16-a2bf71155a18.png)

### VISUALIZING DATA

The created custom metrics and integrated mysql metrics in the hostmap.

![008](https://user-images.githubusercontent.com/33669341/53704495-5c98c400-3e1d-11e9-8fcd-bf4fc28cd234.PNG)

![009](https://user-images.githubusercontent.com/33669341/53704498-5efb1e00-3e1d-11e9-878c-937641649208.PNG)

The integrated sql in datadog agent status

![010](https://user-images.githubusercontent.com/33669341/53704502-60c4e180-3e1d-11e9-8a46-d787b055327b.PNG)

Created timeboard by using datadog API. 

                import requests, json, os, datetime, time
                from datadog import initialize
                from datadog import api as dog

                options = {
                        'api_key' : '<<API_KEY>>',
                        'app_key' : '<<APP_KEY>>'
                        }

                initialize(**options)

                def create_timeboard():
                    title = "MY TEST DASHBOARDx"
                    description = "created timeboard via api"
                    graph = {
                        "title": "Custom metric",
                        "definition":
                        {
                            "requests": [{"q": "customCheck.my_metric{host:ubuntu-xenial}"}],
                            "viz": "timeseries",
                        }
                    }
                    graph2 = {
                        "title": "Custom metric with roll up for past 1h",
                        "definition":
                        {
                            "requests": [{"q": "customCheck.my_metric{host:ubuntu-xenial}.rollup(sum, 3600)"}],
                            "viz": "timeseries",
                        }
                    }
                    x = dog.Timeboard.create(title=title, description=description, graphs=[graph, graph2])
                    return x


                create_timeboard()

Below is the JSON response of created timeboard using datadof api

![016](https://user-images.githubusercontent.com/33669341/53705231-23635280-3e23-11e9-8b13-3c3ad3ddcf9f.PNG)

Dashboard list : custom created dashboard and mysql dashboard

![011](https://user-images.githubusercontent.com/33669341/53704824-2f014a00-3e20-11e9-8ca9-65df714327f8.PNG)

Created custom metrics timeboard with and without rollup function for past 1 hour

![012](https://user-images.githubusercontent.com/33669341/53704818-2e68b380-3e20-11e9-8855-ba102423ead8.PNG)

Selected past 5 mins in the timeboard

![013](https://user-images.githubusercontent.com/33669341/53704819-2e68b380-3e20-11e9-98cd-1faca7e1b01f.PNG)

snapshot with selected last 5 mins data

![015](https://user-images.githubusercontent.com/33669341/53704821-2f014a00-3e20-11e9-8c4c-0b0be965af13.PNG)

Dashboard : Mysql timeboard

![014](https://user-images.githubusercontent.com/33669341/53704820-2e68b380-3e20-11e9-898a-7902be016116.PNG)






### MONITORING DATA
