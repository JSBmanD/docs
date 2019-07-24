## Overview

![Campaign-Monitor](/_assets/img/pages/email/campaign-monitor/campaign-monitor.png)

This guide will walk you through how to setup your email campaigns with **[Campaign Monitor](https://www.campaignmonitor.com/){:target="\_blank"}** using Branch Universal Email to automatically convert your email links into **multi-platform deep links**

{! ingredients/email/overview-steps.md !}

## Setup

{! ingredients/email/prerequisites.md !}

## Configure your ESP

### Setup a custom click tracking domain

1. Add and verify a custom click tracking domain in the **[Set up a custom domain name for your account](http://email-campmon.branch.rocks/account/customize/customdomain/manage){:target="\_blank"}** section of your Campaign Monitor account:

    ![image](/_assets/img/pages/email/campaign-monitor/create-domain.png)

For more information on how to set up your domain, please visit Campaign Monitor's [documentation](https://help.campaignmonitor.com/custom-domain-names#set-up-a-custom-domain){:target="\_blank"}.

!!! tip "Adding a custom click-tracking domain"
    If you need help with setting up a custom click-tracking domain - please ask your account manager or request support at Campaign Monitor.

{! ingredients/email/cname.md !}

## Activate integration

### Choose your email service provider

Navigate to the [Universal Email](https://dashboard.branch.io/email){:target="\_blank"} section of the Branch dashboard. Select **Campaign Monitor** and click **Enable**.

{! ingredients/email/link-setup.md !}

### Tell us your click tracking domain

You can retrieve your click tracking domain from the **[Set up a custom domain name for your account](http://email-campmon.branch.rocks/account/customize/customdomain/manage){:target="\_blank"}** section of your Campaign Monitor account.

If you have not added a custom click tracking domain yet, follow the instructions [here](#setup-a-custom-click-tracking-domain).

![image](/_assets/img/pages/email/campaign-monitor/setup-config.png)

{! ingredients/email/technical-setup.md !}

{! ingredients/email/validate-test.md !}

{! ingredients/email/usage-auto.md !}

## Configure your mobile app

{! ingredients/email/technical-setup-app.md !}

{! ingredients/email/associated-domains.md !}

{! ingredients/email/bounce-web.md !}

## Using Universal email

{! ingredients/email/usage.md !}

{! ingredients/email/usage-auto-bounce-deep.md !}

{! ingredients/email/usage-auto-bounce-web.md !}

## Support

{! ingredients/email/support.md !}
