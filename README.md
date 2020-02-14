# Open360 P2P Feedback Software

Open360 helps HR personnel in various organizations design, plan and run P2P feedback events. It's based on well-known [360 degree](https://en.wikipedia.org/wiki/360-degree_feedback) feedback approach. 

It was initially developed by [Bitworks Software](https://bitworks.software/) for internal purposes in 2016 and released to open source in 2020. We successfuly use the system since 2017, which helped us to improve internal HR processes significantly.

![](/open360.png)

## Integration with the Organizational Infrastructure

We at Bitworks actively use Google services for business, so it will be easiest to start using the system for those companies that also use this service.

However, before publishing in Open Source, we implemented several additional social authenticators and a universal authenticator which works through an external HTTP request, which allows organizations to easily integrate Open360 into their infrastructure.

Currently, the feedback results are exported either in JSON format or in the form of spreadsheets on Google Drive. So for the system to work you need a Google account with the correct permissions. Currently, the system does not allow exporting feedback results in any other way.

## Technological Stack & Requirements

The backend of the system is developed in Scala and the Play framework. At the time of publication, we migrated the backend code for the latest Scala release in branch 2 - 2.13. The system uses PostgreSQL as a DBMS; migrations are done using Flyway. The system API is designed in Swagger.

The frontend is developed in TypeScript and Angular. Before going to open source, we updated Angular to version 9.0.2.

The system is designed to be deployed as Dockerized application.

## User Documentation

We have user [documentation](https://github.com/o360/user-documentation) which helps start using the deployed system without extra hassle. This documentation will be especially useful for the personnel who design and run 360 degree feedback events. 

For the employees who participate in the events, the system usage is pretty straightforward and doesn't require special knowledge.

## Getting Started

To deploy the system you need to meet several requirements:

* **Linux system** which is able to run dockerized applications - we use Ubuntu 18.04 deployed to 2 core, 4 GB RAM, 100 GB SSD VPS;
* **Google Drive Account** which is used to upload the feedback events results in the form of spreadsheets - the account can be personal or business, but proper account permissions must be configured;
* **SMTP server** - you can use the same gmail account for e-mail delivery or use separate server which is wise if you have pretty large group of users, because Gmail could give you a ban when you are trying to send a lot of messages.

Now you are ready to deploy the system. Follow the [deployment guide](/deployment-guide.html) provided in the documentation.

## Help & Requests

If you found a bug or promote a proposal, open new issue: [backend](https://github.com/o360/backend/issues/new) | [frontend](https://github.com/o360/frontend/issues/new)

If you propose a fix or improvement, send the PR: [backend](https://github.com/o360/backend/contributing.md) | [frontend](https://github.com/o360/frontend/contributing.md)

If you need other assistance or want implement a custom requirement with our help, email us: open360@bw-sw.com

