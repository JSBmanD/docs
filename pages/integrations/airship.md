---
title: Airship
---
## Overview

![Airship](https://cdn.branch.io/branch-assets/ad-partner-manager//urban_airship-1568181974178.png)

This guide will walk you through how to send your Branch data to **[Airship](https://www.urbanairship.com/)** using Branch Data Integration.



## Setup

{! ingredients/data-integrations/integrate-branch-sdk.md !}

{! ingredients/data-integrations/enable-partner.md !}

{! ingredients/data-integrations/add-credentials.md !}

Please refer to [Airship's documentation](https://docs.airship.com/) if you need instructions on how to find the values required to enable the integration.

### What Branch sends to Airship

!!! warning "IMPORTANT"
	To be able to match events with your users - you must send a client's email as the `User Identity` to Branch:

	**iOS**: https://docs.branch.io/apps/ios/#track-users

	**Android**: https://docs.branch.io/apps/android/#track-users

* Commerce Events
* Custom Events

## Advanced

{! ingredients/data-integrations/reset-di-settings.md !}
