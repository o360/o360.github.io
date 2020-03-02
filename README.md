# Open360 P2P Feedback Software

Open360 helps HR personnel in various organizations design, plan and run P2P feedback events. It's based on well-known [360 degree](https://en.wikipedia.org/wiki/360-degree_feedback) feedback approach. 

The software was developed by [Bitworks Software](https://bitworks.software/en/) for internal purposes in 2016 and released to open source under Apache License 2.0 at the beginning of 2020. We have been used the system successfully since 2017, which helped us to improve internal HR processes significantly.

![](/open360.png)

## Integration with the Organizational Infrastructure

At Bitworks we actively use Google services for business, so initially, Open360 was intended to be used with Google OAuth and Google Applications (Spreadsheets).

However, before publishing in Open Source, we implemented several additional social authenticators and a universal authenticator which works through an external HTTP request, which allows organizations to easily integrate Open360 into their authentication infrastructure.

Currently, the feedback results are exported either in JSON format or in the form of spreadsheets on Google Drive. So for the system to work you need a Google account with the correct permissions. Currently, the system does not allow exporting feedback results in any other way.

## Basic Ideas

Open360 can serve sophisticated organizational structure. All users are organized into **projects** which are real-life projects or organizational units if the organization uses functional approach. Every project includes one or many **groups**, where every group is a set of users which are interviewed the same way, e.g. Engineers, Managers, C-level. Groups can be organized in a hierarchy, e.g. Project X/Managers  and Project Y/Managers.

Every **project** is a set of the following triplets:
* group which answers the questions;
* group which is the subject of answered questions;
* form with questions.

E.g. defined
```
Groups:
- Engineers: John, Mary
- Managers: Carl, Susan
- All: John, Mary, Carl, Susan
- HR: Helga

Forms:
- Form_Engineers: 
  - Always able to help with tasks? YES/NO
- Form_Managers:
  - Working according your expectations? YES/NO
- Form_All:
  - Want go in the next project with him/her? SURE/NO

Project:
  Interviewer: HR
  Relations:
     - Engineers > Form_Engineers > Managers
     - Managers > Form_Managers > Engineers
     - All > Form_All > All
```

So, based on the above example, when the **feedback event** is lauched, every person from the group 'Engineers' will be asked about the every person located in the group 'Managers' questions placed in the form 'Form_Engineers'. The same logic will be applied to all the relations established inside the project.

When the 360 degree event feedback is finished, all the responses are filled into spreadsheets and are placed into specified Google Account.

## User Documentation

We have user [documentation](https://github.com/o360/user-documentation) which helps start using the deployed system without extra hassle. This documentation will be especially useful for the personnel who design and run 360 degree feedback events. 

For the employees who participate in the events, the system usage is pretty straightforward and doesn't require special knowledge.

## Software Stack

The backend of the system is developed in Scala and the Play framework. At the time of publication, we migrated the backend code for the latest Scala release in branch 2 - 2.13. The system uses PostgreSQL as a DBMS; migrations are done using Flyway. The system API is designed in Swagger.

The frontend is developed in TypeScript and Angular. Before going to open source, we updated Angular to version 9.0.2.

The system is designed to be deployed as Dockerized application.

## Getting Started

To deploy the system you need to meet several requirements:

* **Linux system** which is able to run dockerized applications - we are using Ubuntu 18.04 deployed to 2 core, 4 GB RAM, 100 GB SSD VPS;
* **Google Drive Account** which is used to upload the feedback events results in the form of spreadsheets - the account can be personal or business, but proper account permissions must be configured;
* **SMTP server** - you can use the same gmail account for e-mail delivery or use separate server which is wise if you have pretty large group of users, because Gmail could give you a ban when you are trying to send a lot of messages.

Now you are ready to deploy the system. Follow the [deployment guide](/deployment-guide.html) provided in the documentation.

## Help & Requests

Several tips for collaboration:
* found a bug or promote a proposal, open new issue: [backend](https://github.com/o360/backend/issues/new), [frontend](https://github.com/o360/frontend/issues/new)
* propose a fix or improvement, send the PR: [backend](https://github.com/o360/backend/contributing.md), [frontend](https://github.com/o360/frontend/contributing.md)
* need other assistance or want implement a custom requirement with our help, email us: open360@bw-sw.com

