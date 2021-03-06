# Sites Endpoint

The `/sites` endpoint provides information about 
[NEON field sites](https://www.neonscience.org/field-sites/field-sites-map) where data 
are currently available.  Numerous data products are produced from each site. 
Site names are abbreviated into four-letter site codes -- for example, 
the Arikaree River site abbreviation is ARIK. For more information about sites, 
including the four-letter code for each site, you can find a list on our 
[main website](https://www.neonscience.org/field-sites/field-sites-map/list). 
If you need to know about our remote 
sensing data availability, visit the 
[Airborne Data webpage](https://www.neonscience.org/data-collection/airborne-remote-sensing).  

<a name="paths"></a>
## **Paths**

<a name="get_sites"></a>
### GET `/sites`

#### **Description**
Get information about all sites.


#### **Responses**

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|List of sites|[Response 200](#get_sites-response-200)|
|**default**|General error|[error](#error)|

<h5 id="get_sites-response-200">Response 200</h5>

|Name|Schema|
|---|---|
|**data**  <br>*optional*|[[site](#site)]|


#### **Produces**

* `application/json`


#### **Tags**

* Sites


<a name="get_sites-sitecode"></a>
### GET `/sites/{siteCode}`

#### **Description**
Get information about a site.


#### **Parameters**

|Type|Name|Description|Schema|
|---|---|---|---|
|**Path**|**siteCode**  <br>*required*|Site to get|string|


#### **Responses**

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Single site|[Response 200](#get_sites_sitecode-response-200)|
|**400**|Site(s) not found|[Response 400](#get_sites_sitecode-response-400)|
|**default**|General error|[error](#error)|

<h5 id="get_sites_sitecode-response-200">Response 200</h5>

|Name|Schema|
|---|---|
|**data**  <br>*optional*|[site](#site)|

<h5 id="get_sites_sitecode-response-400">Response 400</h5>

|Name|Schema|
|---|---|
|**errors**  <br>*optional*|[[error](#error)]|


#### **Produces**

* `application/json`


#### **Tags**

* Sites

<a name="definitions"></a>
## **Definitions**


<a name="site"></a>
### **site**

|Name|Description|Schema|
|---|---|---|
|**siteCode**|Four character code for the site|string|
|**siteName**|Full name for the site|string|
|**siteDescription**|Brief site description|string|
|**siteType**|Core or Relocatable site|enum (CORE, RELOCATABLE)|
|**siteLatitude**|Point latitude for the site|number|
|**siteLongitude**|Point longitude for the site|number|
|**stateCode**|Two letter state code that this site is in|string|
|**stateName**|Full name of the state or territory that this site is in|string|
|**domainCode**|Three character domain abbreviation (D01, D02, etc) for the domain this site is in|string|
|**domainName**|Brief description for the domain this site is in|string|
|**dataProducts**|List of data products and months of available data|[[productAvailability](#productavailability)]|

<a name="productavailability"></a>
### **productAvailability**

|Name|Description|Schema|
|---|---|---|
|**dataProductCode**|Revisioned, shortened code for the data product (DP1.00001.001, DP1.10072.001, etc)|string|
|**dataProductTitle**|Full title for the data product.|string|
|**availableMonths**|List of years and months that products are available.  Formatted as YYYY-MM.|[string]|
|**availableDataUrls**|List of data urls for products that are available.|[string]|


<a name="error"></a>
### **error**

|Name|Schema|
|---|---|
|**detail**  <br>*optional*|string|
|**status**  <br>*optional*|number (int)|


<br />
