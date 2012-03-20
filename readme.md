BriteCode
=========
Intros, walkthroughs, how-tos, demos, and docs for the BriteVerify API set.

Getting Started with BriteVerify
--------------------------------
Well, the first step is to request for an account at https://www.briteverify.com/. Once your account has been approved you will be notified via email and you can follow the setup link to create your user account.

Once you have set up an account you can login, click "Account" and see your credentials and some live examples. For the Web Service APIs the most important thing to grab is your APIKEY.

If you are using the the JavaScript libray you will need to click on "Edit" to then scroll to the "Trusted Domains" section. From here you just enter the root domains that are authorized to run BriteVerify. So if your web form is hosted at http://www.mycoolsite.com/register, then all you enter in domain field is "mycoolsite.com". Click "Add" and you are ready to go. You can add as many domains as you wish. This step simply makes sure that no one can rip off your account by stealing the JavaScript on your website.

The BriteVerify Verification Web Services are all available individually, or you can validate multiple data elements in one call using the Contact Service.

BriteServices

* Email
* Phone
* US Postal Address
* Name
* IP Address
* Contact

All the Web Services are currently available via the JavaScript API with the exception of IP and Contact. 

Getting Started with the Web Services
------------------------------------- 