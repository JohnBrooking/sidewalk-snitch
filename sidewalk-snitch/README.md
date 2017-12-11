# sidewalk-snitch
A web application to allow citizens to bulk-upload sidewalk snow violation reports to the City of Portland, Maine's "SeeClickFix" database.

~~~~curl -u "[my email]:[my seeclickfix password]" -i \
       --header "Content-Type: application/json" \
       --data '{
         "lat": 43.663130,
         "lng": -70.253181,
         "address": "27 Smith St., Portland, ME",
         "request_type_id": 8871,
         "answers": {
           "summary": "Icy sidewalk",
           "description": "Sidewalk on hillside was unshovelled after recent snowstorms and now is very icy and impassable."
         }
       }'\~~~~

So the critical pieces here are "request_type_id", which, for our purposes, will always be 8871 (the code for a City of Portland sidewalk snow violation), the location (lat, lng, and address) and the summary/description.

Here's my thinking on how to create a basic website where we can bulk-upload sidewalk snow complaints:

  *  Build a simple web form that can take data for location, summary and descriptions of violations (as many as 4-5 at a time), and send them via a POST method to the SeeClickFix API
  * Figure out OAuth2 authentication for other users' ids and passwords
  * (less important, but nice to have) allow image uploading
  * (less important, but nice to have and pretty easy to implement) on mobile devices, have an option to pull in a user's lat/lng/address from their device location instead of entering that info manually


