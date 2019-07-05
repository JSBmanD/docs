### Tracking Link Parameters

Branch Tracking links allow tracking many parameters about the performance of your ad campaigns and individual ads. Additional parameters for advanced analysis may be added to the link after the '?' or '&' character, to trace extra information.

!!! tip "Example Tracking Link with Additional Parameters"
    Example Branch link including additional parameters to pass Agency and Sub Publisher information:`https://tracking.app.link?%243p=a_partner&~agency=myAgency&~secondary_publisher=best_publisher`

The following parameters are available to use within the pre-generated tracking link:

#### Campaign Information

Branch Parameter | Description
--- | ---
~agency | Agency name
~secondary_publisher | Sub Publisher
~campaign | Campaign name
~campaign_id | Campaign ID
~channel | Channel
~feature | Feature
~stage | Stage
~tags | Tags
~creative_name | Creative name
~creative_id | Creative ID
~ad_set_name | Ad set name
~ad_set_id | Ad set ID
~ad_name | Ad unit name
~ad_id | Ad unit ID
~banner_dimensions | Banner Dimension
~placement | Placement
~keyword_id | Keyword ID
~keyword_text | Keyword Text

#### Device Information

Branch Parameter | Description
--- | ---
%24aaid | Google AAID
%24idfa | Apple IDFA

#### Spend Calculation

!!! info "Cost Data Availability"
    Cost data passed via these macros is available in exports but is not visible in the Branch dashboard.

Branch Parameter | Description
--- | ---
~cost_model | Cost Model; e.g. CPI, eCPC
~cost_value | Cost Value; e.g. 10.00
~cost_currency | Cost Currency; e.g. USD
