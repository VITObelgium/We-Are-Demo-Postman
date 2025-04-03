# We Are Postman Interaction 

## About this Postman Collection

The "We Are" framework defines a specific sequence of API calls that enable secure and transparent digital interactions. These interactions involve:

- Authenticating users and processes 
- Creating and using Verifiable Credentials (in the form of access requests and access grants)
- Interacting with personal data pods

To help developers understand and implement this flow correctly, We Are provides this Postman collection as a reference. 
It outlines the essential API calls and illustrates the complete interaction flow, including how Verifiable Credentials and pod access are handled.

This collection is intended as a practical guide for developers building on the We Are framework—whether you're working in JavaScript, 
Python, or any other programming language. 
By following the flow illustrated here, developers can quickly grasp the key concepts and integrate them into their own applications.

## Project Context

This Postman collection has been developed as a deliverable of the WellData collaboration.

WellData (Dataruimte voor Preventie) is a cross-border innovation project supported by Interreg Vlaanderen-Nederland, with co-funding from the Province of Antwerp (Flanders) and the Province of North Brabant (Netherlands).

The project brings together a diverse group of Flemish and Dutch partners, including:
VITO, Domus Medica vzw, Zorgzaam Leuven, Gaston Remmers – Stichting Mijn Data Onze Gezondheid, NSX – Normalized Systems, Selfcare BV, Sport Vlaanderen, Care Innovation Center West-Brabant, Nuts, Eindhoven University of Technology, LiCalab – Living & Care Lab, TNO, VAN – Vlaams Apothekers Netwerk, and Lokaal Bestuur Vorselaar.

For more information about We Are, visit [we-are-health.be](https://we-are-health.be/)

<img src="EI_Logo WellData_Dataruimte voor Preventie.jpg?raw=true" width="300px"></img>
<img src="provincie_antwerpen_logo_RGB.png?raw=true" width="300px">
<img src="VLAIO_sponsorlogo-antraciet.png?raw=true" width="300px">


## Prerequisites
The following items are prerequisites necessary to use the Postman project to interact with the We Are Solid pods.

- As a Belgian citizen, you are able to authenticate using the ItsMe OIDC provider
- As a European citizen, you can authenticate using the provided eiDAS authentication methods.
- Please contact the We Are helpdesk (https://we-are-health.be) to continue and receive the necessary secrets to do so.
- Import the Postman environment and collection
- Fill in the received secrets in the Postman environment

## API Calls

Below all the different API calls are listed. For more information on the individual steps please look at the documentation within the Postman collection.

Steps included (Postman Collection): 
1. Receive and persist We Are OpenID configurations
2. Use a browser to authenticate using the OIDC provider (ACM)
3. Perform a code exchange utilizing the OIDC Authorization Code Flow
4. Fetch the URI contained in the 'webid' claim within the ID token. Parse the storage URI from the SOLID Web ID.
5. Perform client authentication using the OAuth 2.0 Client Credentials Flow. 
6. Fetch and save verification credential authentication
7. 1. 1. Create access request using the VC service and received client credentials
      2. Consent to access request using a browser and the We Are AMA.
      3. Fetch the issued access grant from previous step within the client and the received client credentials from step 5.
7. 2. Use this option as a shortcut to create an access grant and skip the consent step.
8. Fetch and save UMA (User Managed Access) configurations
9. Receive an UMA ticket by performing a HEAD call on the Pod storage resource or container location.
10. Exchange your UMA ticket and access grant for an access token.
11. Write a RDF resource to the Pod storage using the access token received in the previous step.
12. Read the RDF resource from the Pod storage using the access token received in step 10.
