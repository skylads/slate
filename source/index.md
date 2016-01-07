---
title: API Reference

language_tabs:
  - java

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='http://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Skott Gateway API Documentation! You can use our API to access Skott Gateway API endpoints, which can act on your campaigns on your advertising systems (like the Demand-Side Platform MediaMath).

We have language bindings in Java. You can view code examples in the dark area to the right.

This example API documentation page was created with [Slate](http://github.com/tripit/slate).

# Authentication

> To establish the connection to MediaMath's server, use this code:

```java
ConnectService myMMConnection = new ConnectService();
myMMConnection.verbose=true;
myMMConnection.login();
```

> You can give the name you want to this ConnectService object instead of 'myMMConnection'.

The Skott Gateway API allows you to manipulate objects such as SkottAdvertiser, SkottCampaign, SkottStrategy, etc (you find the full list of available entities in the [Entities](#entities) section). These objects are mapped with the MediaMath T1 entities advertiser, campaign, strategy, etc.

To be able to push your Skott objects to MediaMath and create new entities in your T1 account or update existing entities in your T1 account, you'll need first to establish the connection to MediaMath's servers. To do so, you need to instantiate a **ConnectService** object. Please get a look at the sample code on the right panel for more details.

<aside class="success">
Once the connection is established, you can use this ConnectService instance for several requests. Check each entity section to see when you need to use the ConnectService instance.
</aside>

# Entities

## SkottAdvertiser

> This sample code shows how to create a new advertiser in MediaMath T1 using SkottAdvertiser's newBuilder method:

```java
SkottAdvertiser skottAdvertiser = 
	SkottAdvertiser.newBuilder()
		.setName("Test Advertiser")
		.setAgencyId(112233)
		.setAdServerId(2)
		.setDomain("http://www.skylads.com")
		.setVerticalId(1)
		.build();
		
skottAdvertiser.create(myMMConnection);
```

> This second sample code shows how to update an existing advertiser in MediaMath T1 using SkottAdvertiser's buildUpon method:

```java
SkottAdvertiser updatedAdvertiser = 
	SkottAdvertiser.buildUpon(new SkottAdvertiser(12345))
		.setAdServerId(9)
		.setDomain("http://www.skott.io")
		.setVerticalId(3)
		.build();
		
updatedAdvertiser.update(myMMConnection);
```

> Please note that in both cases you need to use an instance of a ConnectService object as an argument for the create method, if you want the changes to be done on your MediaMath T1 entity.

SkottAdvertiser is a java object of our SkottGateway API that maps the *advertiser* entity of MediaMath T1.

### Creating or updating an advertiser on MediaMath's T1 using SkottAdvertiser

You can either create a new object entirely on MediaMath T1 using SkottAdvertiser's **newBuilder** method (see code examples on the right panel for more details), or update an existing advertiser from MediaMath T1 using SkottAdvertiser's **buildUpon** method (see code examples on the right panel for more details).

In both cases you can then use a number of methods to affect desired values to the fields of this new or updated object. The table below lists all available methods to use with the builders. We use java's builder pattern to make these changes. You can find a lot more information about the builder pattern on the internet, here is just one example: [wikipedia.org/wiki/Builder_pattern](https://en.wikipedia.org/wiki/Builder_pattern). You can also check the code examples on the right panel for more details on how to use those methods with the newBuilder and buildUpon methods.

Please note that to actually create or update your object on MediaMath T1, you need an active connection to their server (the *myMMconnection* object in the code examples on the right panel). For more details on how to establish the connection, please read through our [Authentication](#authentication) section.


### Variables of SkottAdvertiser

Name | Required? | Description | Allowed values | Default
----- | ---- | ------ | --------- | ----
name | yes | Name for the Advertiser | string; maximum 64 characters | -
agencyId | yes | T1 Agency ID to which an advertiser belongs | integer | -
adServerId | yes | Enter ID for third-party adserver - refer to the "Ad Servers" page | integer | -
domain | yes | The URL domain of the advertiser—for example, http://www.advertiser.com | string; maximum 255 characters | -
verticalId | yes | Enter id for the Advertiser's Vertical - see Advertiser Vertical table below | integer; '1'-'34' | -

<aside class="notice">
For more information on advertisers and their fields on MediaMath, you can also refer to MediaMath's documentation at [developer.mediamath.com](developer.mediamath.com).
</aside>

### List of MediaMath's T1 Vertical IDs

For easy reference, the table below lists vertical_id for each vertical available in MediaMath T1.

Advertiser Verticals | vertical_id
-------------------- | -----------
Adult | 31
Air Travel | 1
Alcohol | 30
Autos | 2
Business Services | 3
Clothing & Accessories | 5
Computer (Hardware & Software) | 6
Consumer Goods | 28
Credit Cards | 7
Dating | 8
Education | 11
Electronics | 4
Employment | 9
Entertainment | 12
Food & Beverages | 13
Gambling | 27
Government | 29
Home & Garden | 16
Hotels | 24
Insurance | 17
Internet Services | 18
Media | 25
Non-Profit | 26
Personal Care | 19
Personal Finance | 20
Pets | 14
Pharmaceuticals (Rx & OTC) | 10
Real Estate | 21
Religion and Spirituality | 33
Sporting Goods | 22
Telecommunications | 23
Tobacco | 32
Toys | 15
Weight Loss | 34

<aside class="warning">
The Vertical IDs listed above are for reference but are subject to change without without notification from MediaMath. Therefore, we recommend that you regularly verify that the Vertical IDs remain consistent with desired Vertical.
</aside>

## SkottAgency

> This sample code shows how to create a new advertiser in MediaMath T1 using SkottAdvertiser's newBuilder method:

```java
SkottAgency skottAgency = 
	SkottAgency.newBuilder()
		.setName("Test Agency")
		.setOrganizationId(321)
		.build();

skottAgency.create(myMMConnection);
```

> This second sample code shows how to update an existing advertiser in MediaMath T1 using SkottAdvertiser's buildUpon method:

```java
SkottAgency updatedAgency = 
	SkottAgency.buildUpon(new SkottAgency(112233))
		.setName("Agency v2")
		.build();
updatedAgency.update(myMMConnection);
```

> Please note that in both cases you need to use an instance of a ConnectService object as an argument for the create method, if you want the changes to be done on your MediaMath T1 entity.

SkottAdvertiser is a java object of our SkottGateway API that maps the *advertiser* entity of MediaMath T1.

### Creating or updating an advertiser on MediaMath's T1 using SkottAdvertiser

You can either create a new object entirely on MediaMath T1 using SkottAdvertiser's **newBuilder** method (see code examples on the right panel for more details), or update an existing advertiser from MediaMath T1 using SkottAdvertiser's **buildUpon** method (see code examples on the right panel for more details).

In both cases you can then use a number of methods to affect desired values to the fields of this new or updated object. The table below lists all available methods to use with the builders. We use java's builder pattern to make these changes. You can find a lot more information about the builder pattern on the internet, here is just one example: [wikipedia.org/wiki/Builder_pattern](https://en.wikipedia.org/wiki/Builder_pattern). You can also check the code examples on the right panel for more details on how to use those methods with the newBuilder and buildUpon methods.

Please note that to actually create or update your object on MediaMath T1, you need an active connection to their server (the *myMMconnection* object in the code examples on the right panel). For more details on how to establish the connection, please read through our [Authentication](#authentication) section.


### Variables of SkottAgency

Name | Required? | Description | Allowed values | Default
----- | ---- | ------ | --------- | ----
organizationId | yes | ID of T1 Organization ID to which agency belongs | integer | -
name | yes | Name for the Advertiser | string; maximum 64 characters | -
status | no | Status of concept | Status enum object; possible values: 'ON', 'OFF' | 'OFF'

<aside class="notice">
For more information on advertisers and their fields on MediaMath, you can also refer to MediaMath's documentation at [developer.mediamath.com](developer.mediamath.com).
</aside>

## SkottCampaign

> This sample code shows how to create a new campaign in MediaMath T1 using SkottCampaign's newBuilder method:

```java
SkottCampaign skottCampaign = 
	SkottCampaign.newBuilder()
		.setName("Test Campaign")
		.setAdvertiserId(12345)
		.setAdServerId(2)
		.setStartDate(new Date())
		.setEndDate(new SimpleDateFormat("yyyy-MM-dd'T'HH:mm:ss").parse("2016-01-30T00:00:00"))
		.setGoalType(GoalType.REACH)
		.setGoalValue(2.5)
		.setServiceType(ServiceType.SELF)
		.setTotalBudget(10.2)
		.build();
		
skottCampaign.create(myMMConnection);
```

> This second sample code shows how to update an existing advertiser in MediaMath T1 using SkottCampaign's buildUpon method:

```java
SkottCampaign updatedCampaign = 
	SkottCampaign.buildUpon(new SkottCampaign(123456))
		.setName("Campaign v2")
		.setAdServerId(2)
		.setEndDate(new SimpleDateFormat("yyyy-MM-dd'T'HH:mm:ss").parse("2016-01-16T00:00:00"))
		.setGoalValue(3.3)
		.setTotalBudget(12.4)
		.build();
		
updatedCampaign.update(myMMConnection);
```

> Please note that in both cases you need to use an instance of a ConnectService object as an argument for the create method, if you want the changes to be done on your MediaMath T1 entity.


SkottCampaign is a java object of our SkottGateway API that maps the *campaign* entity of MediaMath T1.

### Creating or updating a campaign on MediaMath's T1 using SkottCampaign

You can either create a new object entirely on MediaMath T1 using SkottCampaign **newBuilder** method (see code examples on the right panel for more details), or update an existing advertiser from MediaMath T1 using SkottCampaign's **buildUpon** method (see code examples on the right panel for more details).

In both cases you can then use a number of methods to affect desired values to the fields of this new or updated object. The table below lists all available methods to use with the builders. We use java's builder pattern to make these changes. You can find a lot more information about the builder pattern on the internet, here is just one example: [wikipedia.org/wiki/Builder_pattern](https://en.wikipedia.org/wiki/Builder_pattern). You can also check the code examples on the right panel for more details on how to use those methods with the newBuilder and buildUpon methods.

Please note that to actually create or update your object on MediaMath T1, you need an active connection to their server (the *myMMconnection* object in the code examples on the right panel). For more details on how to establish the connection, please read through our [Authentication](#authentication) section.


### Variables of SkottCampaign

Name | Required? | Description | Allowed values | Default
----- | ---- | ------ | --------- | ----
name | yes | Descriptive name of the campaign | string; maximum 256 characters | -
advertiserId | yes | T1 Advertiser ID to which a campaign belongs | integer; valid T1 advertiser ID | -
adServerId | yes | Enter ID for third-party adserver - refer to the "Ad Servers" page | integer; 1-11 | -
startDate | yes | Date on which the campaign will start (GMT) | java.util.Date object | -
endDate | yes | Last date of campaign in GMT | java.util.Date object; date must be after the startDate | -
goalType | yes | Goal type which campaign performance will be measured | GoalType enum object; possible values: 'CPA', 'CPC', 'CPE', 'REACH', 'SPEND', 'ROI' | -
goalValue | yes | Target goal value for campaign respective to the goalType selection | real number; must be greater than 0.01 | -
serviceType | yes | Indicate whether campaign will be self-service or managed (managed campaigns will incur manage service fee) | ServiceType enum object; possible values: 'SELF', 'MANAGED' | -
totalBudget | yes | Allocated budget for the campaign | real number valid to 2 decimals | -

<aside class="notice">
For more information on campaigns and their fields on MediaMath, you can also refer to MediaMath's documentation at [developer.mediamath.com](developer.mediamath.com).
</aside>

## SkottConcept

> This sample code shows how to create a new campaign in MediaMath T1 using SkottConcept's newBuilder method:

```java
SkottConcept skottConcept = 
	SkottConcept.newBuilder()
		.setName("Test Concept")
		.setAdvertiserId(12345)
		.build();
				
skottConcept.create(myMMConnection);
```

> This second sample code shows how to update an existing advertiser in MediaMath T1 using SkottConcept's buildUpon method:

```java
SkottConcept updatedConcept = 
	SkottConcept.buildUpon(new SkottConcept(123))
		.setName("Concept v2")
		.build();

updatedConcept.update(myMMConnection);
```

> Please note that in both cases you need to use an instance of a ConnectService object as an argument for the create method, if you want the changes to be done on your MediaMath T1 entity.


SkottConcept is a java object of our SkottGateway API that maps the *concept* entity of MediaMath T1.

### Creating or updating a campaign on MediaMath's T1 using SkottConcept

You can either create a new object entirely on MediaMath T1 using SkottConcept **newBuilder** method (see code examples on the right panel for more details), or update an existing advertiser from MediaMath T1 using SkottConcept's **buildUpon** method (see code examples on the right panel for more details).

In both cases you can then use a number of methods to affect desired values to the fields of this new or updated object. The table below lists all available methods to use with the builders. We use java's builder pattern to make these changes. You can find a lot more information about the builder pattern on the internet, here is just one example: [wikipedia.org/wiki/Builder_pattern](https://en.wikipedia.org/wiki/Builder_pattern). You can also check the code examples on the right panel for more details on how to use those methods with the newBuilder and buildUpon methods.

Please note that to actually create or update your object on MediaMath T1, you need an active connection to their server (the *myMMconnection* object in the code examples on the right panel). For more details on how to establish the connection, please read through our [Authentication](#authentication) section.


### Variables of SkottConcept

Name | Required? | Description | Allowed values | Default
----- | ---- | ------ | --------- | ----
name | yes | Descriptive name of the campaign | string; maximum 64 characters | -
advertiserId | yes | T1 Advertiser ID to which a concept is attached | integer; valid T1 advertiser ID | -
status | no | Status of concept | Status enum object; possible values: 'ON', 'OFF' | 'OFF'

<aside class="notice">
For more information on campaigns and their fields on MediaMath, you can also refer to MediaMath's documentation at [developer.mediamath.com](developer.mediamath.com).
</aside>

## SkottCreative

> This sample code shows how to create a new campaign in MediaMath T1 using SkottCreative's newBuilder method:

```java
SkottCreative skottCreative = 
	SkottCreative.newBuilder()
		.setName("Test Creative")
		.setAdvertiserId(12345)
		.setExternalIdentifier("test")
		.setWidth(300)
		.setHeight(250)
		.setTpasAdTagName("test")
		.build();

skottCreative.create(myMMConnection);
```

> This second sample code shows how to update an existing advertiser in MediaMath T1 using SkottCreative's buildUpon method:

```java
SkottCreative updatedCreative = 
	SkottCreative.buildUpon(new SkottCreative(654321))
		.setName("Creative v2")
		.setExternalIdentifier("test2")
		.setWidth(728)
		.setHeight(90)
		.setTpasAdTagName("test2")
		.build();

updatedCreative.update(myMMConnection);
```

> Please note that in both cases you need to use an instance of a ConnectService object as an argument for the create method, if you want the changes to be done on your MediaMath T1 entity.


SkottCreative is a java object of our SkottGateway API that maps the *creative* entity of MediaMath T1.

### Creating or updating a campaign on MediaMath's T1 using SkottCreative

You can either create a new object entirely on MediaMath T1 using SkottCreative **newBuilder** method (see code examples on the right panel for more details), or update an existing advertiser from MediaMath T1 using SkottCreative's **buildUpon** method (see code examples on the right panel for more details).

In both cases you can then use a number of methods to affect desired values to the fields of this new or updated object. The table below lists all available methods to use with the builders. We use java's builder pattern to make these changes. You can find a lot more information about the builder pattern on the internet, here is just one example: [wikipedia.org/wiki/Builder_pattern](https://en.wikipedia.org/wiki/Builder_pattern). You can also check the code examples on the right panel for more details on how to use those methods with the newBuilder and buildUpon methods.

Please note that to actually create or update your object on MediaMath T1, you need an active connection to their server (the *myMMconnection* object in the code examples on the right panel). For more details on how to establish the connection, please read through our [Authentication](#authentication) section.


### Variables of SkottCreative

Name | Required? | Description | Allowed values | Default
----- | ---- | ------ | --------- | ----
adFormat | no | Advertising format in which creative will appear | AdFormat enum object; possible values: 'DISPLAY', 'MOBILE', 'EXPANDABLE' | 'DISPLAY'
adServerType | no | Advertising format in which creative will appear | AdFormat enum object; possible values: 'DISPLAY', 'MOBILE', 'EXPANDABLE' | 'DISPLAY'
name | yes | Descriptive name of the campaign | string; maximum 64 characters | -
advertiserId | yes | T1 Advertiser ID to which a concept is attached | integer; valid T1 advertiser ID | -
conceptId | yes | ID of TerminalOne Concept ID which the creative belongs | integer; valid T1 concept ID | -
externalIdentifier | yes | Unique Placement ID from the Third Party Ad Server | string; maximum 64 characters | -
fileType | yes | Specify the file type | FileType enum object; possible values: 'GIF', 'HTML5', 'JPG', 'PNG', 'SWF', 'TIF', 'TIFF', 'UNKNOWN', 'VAST', 'ZIP' | -
height | yes | Height of the creative (in pixels) | integer | -
tagType | yes | Specify the implementation tag type into this field | CreativeTagType enum object; possible values: 'IFRAME_SCRIPT_NOSCRIPT', 'IFRAME_SCRIPT', 'IFRAME_NOSCRIPT', 'IFRAME_IMG', 'SCRIPT_NOSCRIPT', 'SCRIPT', 'NOSCRIPT', 'IFRAME', 'IMG' | -
tpasAdTagName | yes | Descriptive name of the placement from the 3PAS | string; maximum 255 characters | -
width | yes | Width of the creative (in pixels) | integer | -

<aside class="notice">
For more information on campaigns and their fields on MediaMath, you can also refer to MediaMath's documentation at [developer.mediamath.com](developer.mediamath.com).
</aside>

## SkottDeal

> This sample code shows how to create a new campaign in MediaMath T1 using SkottDeal's newBuilder method:

```java
SkottDeal skottDeal = 
	SkottDeal.newBuilder()
		.setName("Test Deal")
		.setAdvertiserId(12345)
		.setRtbProviderId(11)
		.setPublisherId(1987)
		.setPriceMethod(PriceMethod.CPM)
		.setPriceType(PriceType.FIXED)
		.setStartDate(new Date())
		.setEndDate(new SimpleDateFormat("yyyy-MM-dd'T'HH:mm:ss").parse("2015-12-30T00:00:00"))
		.build();

skottDeal.create(myMMConnection);
```

> This second sample code shows how to update an existing advertiser in MediaMath T1 using SkottDeal's buildUpon method:

```java
SkottDeal updatedDeal = 
	SkottDeal.buildUpon(new SkottDeal(1234))
		.setName("Test Deal")
		.setPriceType(PriceType.FLOOR)
		.setEndDate(df.parse("2015-12-31T00:00:00"))
		.build();
		
updatedDeal.update(myMMConnection);
```

> Please note that in both cases you need to use an instance of a ConnectService object as an argument for the create method, if you want the changes to be done on your MediaMath T1 entity.


SkottDeal is a java object of our SkottGateway API that maps the *deal* entity of MediaMath T1.

### Creating or updating a campaign on MediaMath's T1 using SkottDeal

You can either create a new object entirely on MediaMath T1 using SkottDeal **newBuilder** method (see code examples on the right panel for more details), or update an existing advertiser from MediaMath T1 using SkottDeal's **buildUpon** method (see code examples on the right panel for more details).

In both cases you can then use a number of methods to affect desired values to the fields of this new or updated object. The table below lists all available methods to use with the builders. We use java's builder pattern to make these changes. You can find a lot more information about the builder pattern on the internet, here is just one example: [wikipedia.org/wiki/Builder_pattern](https://en.wikipedia.org/wiki/Builder_pattern). You can also check the code examples on the right panel for more details on how to use those methods with the newBuilder and buildUpon methods.

Please note that to actually create or update your object on MediaMath T1, you need an active connection to their server (the *myMMconnection* object in the code examples on the right panel). For more details on how to establish the connection, please read through our [Authentication](#authentication) section.


### Variables of SkottDeal

Name | Required? | Description | Allowed values | Default
----- | ---- | ------ | --------- | ----
name | yes | Descriptive name of the campaign | string; maximum 64 characters | -
advertiserId | yes | T1 Advertiser ID to which a deal belongs | integer; valid T1 advertiser ID | -
rtbProviderId | yes | Enter ID for T1 supply source / rtb provider | integer; valid T1 supply source / rtb provider ID | -
publisherId | yes | Enter ID for T1 publisher | integer; valid T1 publisher ID | -
priceMethod | yes | Specify the price method of the deal | PriceMethod enum object; possible values: 'CPM' | -
priceType | yes | Specify the price type of the deal | PriceType enum object; possible values: 'FLOOR', 'FIXED' | -
startDate | yes | Date on which the campaign will start (GMT) | java.util.Date object | -
endDate | yes | Last date of campaign in GMT | java.util.Date object; date must be after the startDate | -

<aside class="notice">
For more information on campaigns and their fields on MediaMath, you can also refer to MediaMath's documentation at [developer.mediamath.com](developer.mediamath.com).
</aside>

## SkottOrganization

> This sample code shows how to create a new advertiser in MediaMath T1 using SkottAdvertiser's newBuilder method:

```java
SkottOrganization skottOrganization = 
	SkottOrganization.newBuilder()
		.setName("Test Organization")
		.build();

skottOrganization.create(myMMConnection);
```

> This second sample code shows how to update an existing advertiser in MediaMath T1 using SkottAdvertiser's buildUpon method:

```java
SkottOrganization updatedOrganization = 
	SkottOrganization.buildUpon(new SkottOrganization(321))
		.setName("Organization v2")
		.build();
updatedOrganization.update(myMMConnection);
```

> Please note that in both cases you need to use an instance of a ConnectService object as an argument for the create method, if you want the changes to be done on your MediaMath T1 entity.

SkottAdvertiser is a java object of our SkottGateway API that maps the *organization* entity of MediaMath T1.

### Creating or updating an advertiser on MediaMath's T1 using SkottAdvertiser

You can either create a new object entirely on MediaMath T1 using SkottAdvertiser's **newBuilder** method (see code examples on the right panel for more details), or update an existing advertiser from MediaMath T1 using SkottAdvertiser's **buildUpon** method (see code examples on the right panel for more details).

In both cases you can then use a number of methods to affect desired values to the fields of this new or updated object. The table below lists all available methods to use with the builders. We use java's builder pattern to make these changes. You can find a lot more information about the builder pattern on the internet, here is just one example: [wikipedia.org/wiki/Builder_pattern](https://en.wikipedia.org/wiki/Builder_pattern). You can also check the code examples on the right panel for more details on how to use those methods with the newBuilder and buildUpon methods.

Please note that to actually create or update your object on MediaMath T1, you need an active connection to their server (the *myMMconnection* object in the code examples on the right panel). For more details on how to establish the connection, please read through our [Authentication](#authentication) section.


### Variables of SkottOrganization

Name | Required? | Description | Allowed values | Default
----- | ---- | ------ | --------- | ----
name | yes | Name for the Advertiser | string; maximum 64 characters | -
status | no | Status of concept | Status enum object; possible values: 'ON', 'OFF' | 'OFF'

<aside class="notice">
For more information on advertisers and their fields on MediaMath, you can also refer to MediaMath's documentation at [developer.mediamath.com](developer.mediamath.com).
</aside>

## SkottPixel

> This sample code shows how to create a new campaign in MediaMath T1 using SkottPixel's newBuilder method:

```java
SkottPixel skottPixel = 
	SkottPixel.newBuilder()
		.setName("Test Pixel")
		.setAdvertiserId(12345)
		.setPixelType(PixelType.EVENT)
		.setTagType(TagType.IMAGE)
		.build();
		
skottPixel.create(myMMConnection);
```

> This second sample code shows how to update an existing advertiser in MediaMath T1 using SkottPixel's buildUpon method:

```java
SkottPixel updatedPixel = 
	SkottPixel.buildUpon(new SkottPixel(123))
		.setName("Pixel v2")
		.build();

updatedPixel.update(myMMConnection);
```

> Please note that in both cases you need to use an instance of a ConnectService object as an argument for the create method, if you want the changes to be done on your MediaMath T1 entity.


SkottPixel is a java object of our SkottGateway API that maps the *pixel* entity of MediaMath T1.

### Creating or updating a campaign on MediaMath's T1 using SkottPixel

You can either create a new object entirely on MediaMath T1 using SkottPixel **newBuilder** method (see code examples on the right panel for more details), or update an existing advertiser from MediaMath T1 using SkottPixel's **buildUpon** method (see code examples on the right panel for more details).

In both cases you can then use a number of methods to affect desired values to the fields of this new or updated object. The table below lists all available methods to use with the builders. We use java's builder pattern to make these changes. You can find a lot more information about the builder pattern on the internet, here is just one example: [wikipedia.org/wiki/Builder_pattern](https://en.wikipedia.org/wiki/Builder_pattern). You can also check the code examples on the right panel for more details on how to use those methods with the newBuilder and buildUpon methods.

Please note that to actually create or update your object on MediaMath T1, you need an active connection to their server (the *myMMconnection* object in the code examples on the right panel). For more details on how to establish the connection, please read through our [Authentication](#authentication) section.


### Variables of SkottPixel

Name | Required? | Description | Allowed values | Default
----- | ---- | ------ | --------- | ----
name | yes | Descriptive name of the campaign | string; maximum 64 characters | -
advertiserId | yes | T1 Advertiser ID to which a pixel belongs | integer; valid T1 advertiser ID | -
pixelType | yes | Specify the type of pixel | PixelType enum object; possible values: 'EVENT', 'DATA' | -
tagType | yes | Specify the type of tag for the pixel | TagType enum object; possible values: 'IMAGE', 'JS', 'DFA', 'UAT', 'IFRAME' | -

<aside class="notice">
For more information on campaigns and their fields on MediaMath, you can also refer to MediaMath's documentation at [developer.mediamath.com](developer.mediamath.com).
</aside>

## SkottStrategy

> This sample code shows how to create a new campaign in MediaMath T1 using SkottStrategy's newBuilder method:

```java
SkottStrategy myStrategy = 
	SkottStrategy.newBuilder()
		.setCampaignId(123456)
		.setBudget(1000.)
		.setGoalType(GoalType.SPEND)
		.setName("Test Strategy")
		.setPacingAmount(100.)
		.setType(StrategyType.AUD)
		.setStartDate(new Date())
		.setEndDate(new SimpleDateFormat("yyyy-MM-dd").parse("2015-12-30"))
		.setAudienceSegmentExcludeOp(AudienceSegmentExcludeOp.OR)
		.setAudienceSegmentIncludeOp(AudienceSegmentIncludeOp.AND)
		.build();
		
myStrategy.create(connectService);
```

> This second sample code shows how to update an existing advertiser in MediaMath T1 using SkottStrategy's setters and update method:

```java
SkottStrategy updatedStrategy = new SkottStrategy(12345678);
updatedStrategy.refresh(connectService);
updatedStrategy.setMaxBid(10.);
updatedStrategy.setPacingAmount(updatedStrategy.getPacingAmount()*2);
updatedStrategy.setFrequencyAmount(5);
updatedStrategy.update(connectService);
```

> Please note that in both cases you need to use an instance of a ConnectService object as an argument for the create method, if you want the changes to be done on your MediaMath T1 entity.


SkottStrategy is a java object of our SkottGateway API that maps the *strategy* entity of MediaMath T1.

### Creating or updating a campaign on MediaMath's T1 using SkottStrategy

You can either create a new object entirely on MediaMath T1 using SkottStrategy **newBuilder** method (see code examples on the right panel for more details), or update an existing advertiser from MediaMath T1 using SkottStrategy's **buildUpon** method (see code examples on the right panel for more details).

In both cases you can then use a number of methods to affect desired values to the fields of this new or updated object. The table below lists all available methods to use with the builders. We use java's builder pattern to make these changes. You can find a lot more information about the builder pattern on the internet, here is just one example: [wikipedia.org/wiki/Builder_pattern](https://en.wikipedia.org/wiki/Builder_pattern). You can also check the code examples on the right panel for more details on how to use those methods with the newBuilder and buildUpon methods.

Please note that to actually create or update your object on MediaMath T1, you need an active connection to their server (the *myMMconnection* object in the code examples on the right panel). For more details on how to establish the connection, please read through our [Authentication](#authentication) section.


### Variables of SkottStrategy

Name | Required? | Description | Allowed values | Default
----- | ---- | ------ | --------- | ----
name | yes | Descriptive name of the campaign | string; maximum 64 characters | -
campaignId | yes | Specify parent campaign of strategy | integer; valid T1 campaign ID | -
budget | yes | Allocated budget for strategy | real number valid to 2 decimals | -
startDate | yes | Date on which the campaign will start (GMT) | java.util.Date object | -
endDate | yes | Last date of campaign in GMT | java.util.Date object; date must be after the startDate | -
goalType | yes | Goal type which campaign performance will be measured | GoalType enum object; possible values: 'CPA', 'CPC', 'CPE', 'REACH', 'SPEND', 'ROI' | -
goalValue | yes | Target goal value for campaign respective to the goalType selection | real number; must be greater than 0.01 | -
pacingAmount | yes | Specify max amount strategy can spend within pacingInterval | real number valid to 2 decimals | -
pacingInterval | no | Specify interval for pacingAmount | PacingInterval enum object; possible values: 'HOUR', 'DAY' | 'DAY'
type | yes | Specify the type of strategy (re-marketing (REM), goal-based optimization (GBO), audience (AUD)) | StrategyType enum object; possible values: 'REM', 'GBO', 'AUD' | -

<aside class="notice">
For more information on strategies and their fields on MediaMath, you can also refer to MediaMath's documentation at [developer.mediamath.com](developer.mediamath.com).
</aside>
