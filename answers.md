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

Created custom checks with metric named (my_metrics) in the range 0 to 1000 and it's default interval time is 30sec. Then it has been changed to 45sec.

![005](https://user-images.githubusercontent.com/33669341/53704096-5c96c500-3e19-11e9-9fca-2ad3a00b3929.PNG)

The created custom check can be viewed in the 'datadog-agent status' as below,

![dtdg-check](https://user-images.githubusercontent.com/33669341/53704173-974d2d00-3e1a-11e9-89a5-fe17def7a647.PNG)

Initila interval time 05sec for testing.

![custom_metrics](https://user-images.githubusercontent.com/33669341/53704131-f1012780-3e19-11e9-883c-3b7023021a63.PNG)

Then interval changed from 05sec to 45sec to have a clear view.

![collection interval from 5 to 45](https://user-images.githubusercontent.com/33669341/53704144-13934080-3e1a-11e9-8a16-a2bf71155a18.png)

### VISUALIZING DATA

### MONITORING DATA
