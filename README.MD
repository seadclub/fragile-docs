# Aggregator of friends' ratings

## Software Engineering and Development Club

**Names, of, all, members**

## Contents

<img align="right" width="210" height="210" src="images/rate.png">

- [Welcome](#welcome)
  - [About the PalOps](#about-the-palops)
- [Business Case](#business-case)
- [System Requirements](#system-requirements)
  - [Functional Requirements](#functional-requirements)
  - [Architecture Characteristics Requirements](#architecture-characteristics-requirements)
  - [Constraints](#constraints)
  - [Assumptions](#assumptions)

## Welcome

This page is architectural documentation for `PalOps` from **Software Engineering and Development Club** by k-a-webdev, November 29, 2023.

### About the PalOps

> Rating
> Friends
> Mutual aid
> Film
> Serial
> Anime
> Music

We are glad to introduce you our project, which will <ins>help</ins> everyone in choosing <ins>the best</ins> and <ins>quality</ins> <ins>content</ins> based on the <ins>choices of your friends and other users</ins>.

## Business Case

Many resources can be evaluated, which will make your further choice easier and better. This foundation is laid in our project.

Our clients will interact with the service both in free mode and by paying for certain functionality. Different capabilities will be implemented in different ways, for example through front-end and back-end. One of these features will be:

- review of friends' ratings;
- view other users' ratings;
- generator of random elections based on the field;
- chat with friends;
- blocking the viewing of your page with ratings by other users (paid);
- possibility to personalize the account page;
- the ability to personalize the account page in a super-duper ultra-stylish way (for example, animations on your page) (paid);
- generation of AI recommendations based on established filters, namely: your ratings, ratings of your friends, general ratings of all users of the service, in a certain area;
- to be continued....

**Business Drivers**

What business drivers can we learn from the situation:

- Unavailability of information about your friends' preferences from popular services as Netflix, Spotify, Soundcloud, AnimeList and other on one platform.
- Users desire a user-friendly interface coupled with ratings from other services on one platform.

**Business Goals**

The company establishes the following business goal to help the situation:

- Create a new evaluation platform where data from other services will be collected and provide the possibility of displaying and sharing this data, combining it with user-friendly design

## System Requirements

### Stakeholders

This section describes key stakeholders of the system and their architectural concerns.

- **SH-1**: **Administrator** (security)

  - security is the second name for an administrator; these people deal with user accounts and the internal processes.

- **SH-2**: **Customer** (availability, performance, scalability, robustness)

  - customers want the system they're accessing is available anytime they want to use it, and that it responses quickly to their actions;
  - they also want their rating points to be correct and in full.

- **SH-3**: **Manager** (reportability)

  - these people need to pay careful attention on what's going on: are there unsatisfied customer, are there rating from all connected services, etc.

- **SH-4**: **Helpdesk** (availability, performance)

  - this is the first line of support for the customers, so they need to have access to the troubleshooting articles and data from requested account when customer are calling for that;
  - they provide direct person-to-person phone/email support, so their answers will have to be found as quickly as possible.

- **SH-5**: **Development team** (extensibility)
  - these guys are having hard time deploying changes to production because of high coupling and poor modularity of the current system.

### Functional Requirements

- **UC-1**: **User maintenance**:

  - administrator maintains internal user accounts (SH-1);
  - administrator maintains expert skillset, location, and availability (SH-1);

- **UC-2**: **Customer registration**:

  - customers register their profile, additional services, support plan and credit card if necessary (SH-2);

- **UC-3**: **Rating workflow**:

  - customer somehow confirms the connection of the external service (SH-2, SH-4);

- **UC-4**: **Survey submission**:

  - customers fill out and submit satisfaction surveys (SH-2);

- **UC-5**: **Reporting**:

  - customers generate report with their problem and this report view the manager (SH-2, SH-3);

- **UC-6**: **Notification**:

  - customers receive email or email about decisions regarding their notification (SH-2);

- **UC-7**: **Simple questions**:

  - if customars have the questions for example about which functions it have, how it use and which benifits of the paid plane (SH-2, SH-4);

### Architecture Characteristics Requirements

- **QA-1**: **scalability** (UC-3)

  - country scale geography (USA?);
  - number of customers - hundreds;

- **QA-2**: **availability** (UC-2, UC-3, UC-4)

  - customer-facing services and KB must be highly available because outages will make a negative impact on business;
  - 99.9% seems reasonable here;

- **QA-3**: **performance** (UC-2, UC-3, UC-5)

  - response time < 2s for page load;
  - knowledge search time several seconds;
  - data requests and process them should not take an excessive amount of time;

- **QA-4**: **security** (UC-2, UC-5)

  - customer personal information and credit cards should be stored in secure and comply to PCI requirements;

- **QA-5**: **extensibility** (all use cases, SH-5)
  - one of the critical concerns regarding the current system is that whenever a change is made, it takes too long and something else usually breaks. This makes us think about improved modularity of the new system.

### Constraints

- **CON-1**: Integration? Cloud/on-prem? Technology stak?

### Assumptions

- **ASM-1**: The mobile app is a part of the system and can be changed.
- **ASM-2**: Helpdesk assistants (aka Call Center) need access to the account information(what internal servicies he use, list of friend, etc). These are also users of the system although are not listed in the "Main Four Users" of the original requirements.
- **ASM-3**: The company stores customer credit card information locally and does not interoperate with a 3-party authority (like authorize.net in the US).

![PalOps](images/PalOps_additional-logo.png)
