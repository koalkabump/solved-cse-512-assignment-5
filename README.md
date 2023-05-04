Download Link: https://assignmentchef.com/product/solved-cse-512-assignment-5
<br>
The required task is two write two functions, which will perform some textual and spatial searching on MongoDB. Details are explained below.

Steps for Assignments: –

<ol>

 <li>Install <em>MongoDB 2.6.11</em>.</li>

 <li>Install <em>pymongo</em> to act as helper interface with MongoDB.</li>

 <li>Run the tester file to check everything runs and nothing fails.</li>

 <li>Now, Implement the function provided in Assignment5_Interface.py to <sub>      </sub>perform the operations as listed below:

  <ol>

   <li><em>FindBusinessBasedOnCity(cityToSearch, saveLocation1, collection) </em></li>

  </ol></li>

</ol>

This function searches the ‘collection’ given to find all the business present in the city provided in ‘cityToSearch’ and save it to ‘saveLocation1’. For each business you found, you should store name Full address, city, state of

<em>                              </em>business in the following format.

Each line of the saved file will contain,

Name$FullAddress$City$State. ($ is the separator and must be

<em>                                    </em>present)

<ol>

 <li><em>FindBusinessBasedOnLocation(categoriesToSearch, myLocation, </em></li>

</ol>

<em>                              maxDistance, saveLocation2, collection) </em>

This function searches the ‘collection’ given to find name of all the business present in the ‘maxDistance’ from the given ‘myLocation’ that covers <strong><em>all</em></strong> the given categories (please use the distance algorithm given below) and save them to ‘saveLocation2’. Each line of the output file will contain the <strong><em>name of the business only</em></strong>.

— categoriesToSearch: a list of categories need to be covered — ‘myLocation’ will be given with format [“40.3”, “51.6”].

— maxDistance: the search distance

— saveLocation2: output location

<strong>NOTE: – Please Make sure all fields are in Uppercase while writing in file, makes it easy to check. </strong>&#x263a;




<h1>      Files given to you: –</h1>

<strong>Assignment5_Interface.py – </strong>You should complete this file. You would need to implement the function present in this file.




<strong>testData.json – </strong>This is the json file which is used as a document to put inside

MongoDb. The structure of one record of this file is &lt; Key value pair&gt;: –

{

‘type’: ‘business’,

‘business_id’: (encrypted business id),

‘name’: (business name),

‘neighborhoods’: [(hood names)],

‘full_address’: (localized address),

‘city’: (city),

‘state’: (state),

‘latitude’: latitude,

‘longitude’: longitude,

<sub>                  </sub>‘categories’: [(localized category names)]

<sub>                  </sub>‘open’: True / False (corresponds to permanently closed, not business hours),

}




<h1><sub>                  </sub>Example: –</h1>

<sub>                  </sub>{“city”: “Ahwatukee”,

<sub>                  </sub>“review_count”: 3,

<sub>                  </sub>“name”: “McDonald’s”,

<sub>                  </sub>“neighborhoods”: [],

<sub>                  </sub>“type”: “business”,

<sub>                  </sub>“business_id”: “LNdwp-9Isnd6xmBKUz4K_A”,

<sub>                  </sub>“full_address”: “10823 S 51st St
Ahwatukee, AZ 85044”,

<sub>                  </sub>“state”: “AZ”,

<sub>                  </sub>“longitude”: -111.975004,

<sub>                  </sub>“stars”: 2.0,

<sub>                  </sub>“latitude”: 33.348560900000003,

<sub>                  </sub>“open”: true,

<sub>                  </sub>“categories”: [“Burgers”, “Fast Food”, “Restaurants”]} <strong>Note: – The order of key value pair does not matter. </strong>




<strong>tester.py – </strong>DO NOT change this file. This is just to help you run the code for your implementation.




<sub>      </sub><strong>Distance Algorithm needs to be used: </strong>

Given two pair of latitude and longitude as [lat2, lon2] and [lat1, lon1], you can <sub>  </sub>calculate the distance between them using the formula given below:

<sub>      </sub>DistanceFunction(lat2, lon2, lat1, lon1):

<sub>            </sub>var R = 3959; // miles <sub>     </sub>var φ1 = lat1.toRadians(); <sub>           </sub>var φ2 = lat2.toRadians();

<sub>                 </sub>var Δφ = (lat2-lat1).toRadians();

var Δλ = (lon2-lon1).toRadians();




<sub>                 </sub>var a = Math.sin(Δφ/2) * Math.sin(Δφ/2)


<sub>                             </sub>Math.cos(φ1) * Math.cos(φ2) *

<sub>             </sub>Math.sin(Δλ/2) * Math.sin(Δλ/2);

<sub>                </sub>var c = 2 * Math.atan2(Math.sqrt(a), Math.sqrt(1-a)); var d = R * c;




d is the distance between the given pair of latitude and longitude. The distance is in <strong>miles.</strong> Reference: <u>http://www.movable-type.co.uk/scripts/latlong.html</u>




<h1><sub>      </sub></h1>




<sub>    </sub>