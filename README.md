# A python library for the FitBit API

Forked from mrwz/FitBit.py and jplattel/FitBit.py .
No need to store id and password in code. 
Type id and passworld of fitbit account is all you need to get the PIN.
This will break if FitBit's HTML changes as follows mrwz's.

## Usage

Edit the fitbit.py file with your consumer key and secret, as well as your
email address and your FitBit password.

	import fitbit
	z = fitbit.FitBit()

Make a request token:

	auth_url, auth_token = z.GetRequestToken()

Use auth_url to get a PIN: (Type id and passworld manually)

    PIN = z.GetPIN(auth_url)

Use the PIN to get an access token:

	access_token = z.GetAccessToken(PIN, auth_token)
	
Store the access_token for later usage. You can now call the API with it:

	response = z.ApiCall(access_token, apiCall='/1/user/-/activities/log/steps/date/today/7d.json')

All responses for the functions are received in JSON but are also available in XML.
A list of endpoints is at https://wiki.fitbit.com/display/API/Fitbit+Resource+Access+API.
