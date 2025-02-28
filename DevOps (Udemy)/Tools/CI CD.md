Continuous Integration, Continuous Delivery/Deployment

# Continuous Integration #ci

Take code, package it up, and passing it off to the CD process.

## Process

Some samples:
1. Clone a github repository that is going to be used, and packages it up
2. Test your code, unit tests, integration tests, etc. - Make sure it has all it's dependencies, etc.
3. Run security checks against the code - think like linter, or sonar cube, and running it against the code 

# Continuous Delivery #cd

Deploy the code to some system, container, serverless, bare metal, etc. Continuous delivery usually has a manual step where it is reviewed by a different party prior to being pushed to it's end location.

## Process
1. Assumes you are already authenticated to the system you are pushing to, or takes care of the authentication.
2. Delivers the code to the end destination.
3. Ensures the code is working as intended when deployed. -i.e. run tests to ensure it is running immediately after the code is pushed.


# Continuous Deployment #cd

VERY similar to Continuous Delivery, but this is fully automated, without the manual need for a review and another engineer to push a button before reaching it's end destination.


#### Notes: 
Differences between continuous delivery and continuous deployment 

As taught in this lab, they explain there being a very distinct different between continuous delivery and continuous deployment. 

The instructor explained the continuous delivery has a manual check or button where you must push for the code to be pushed to it's end destination, whereas, in continuous deployment, the code is automatically pushed to the end destination without the manual button or need for an engineer to manually check and continue on.