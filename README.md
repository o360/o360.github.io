# Open360 P2P Feedback Software

Open360 helps HR personnel in various organizations design, plan and run P2P feedback events. It's based on well-known [360 degree](https://en.wikipedia.org/wiki/360-degree_feedback) feedback approach. 

It was initially developed by [Bitworks Software](https://bitworks.software/) for internal purposes in 2016 and released to open source in 2020. We at Bitworks successfuly use Open360 since 2016, which helped us to improve internal HR processes significantly.

## Integration with organizational infrastructure

We at Bitworks actively use Google services for business, so it will be easiest to start using the system for those companies that also use this service.

However, before publishing in Open Source, we implemented several additional social authenticators and a universal authenticator which works through an external HTTP request, which allows organizations to easily integrate Open360 into their infrastructure.

Currently, the feedback results are exported either in JSON format or in the form of spreadsheets on Google Drive. So for the system to work you need a Google account with the correct permissions. Currently, the system does not allow exporting feedback results in any other way.

## Technological stack

The backend of the system is developed in Scala and the Play framework. At the time of publication, we migrated the backend code for the latest Scala release in branch 2 - 2.13. The system uses PostgreSQL as a DBMS; migrations are done using Flyway. The system API is designed in Swagger.

The frontend is developed in TypeScript and Angular. Before going to open source, we updated Angular to version 9.0.2.

The system is designed to be deployed as Dockerized application.
