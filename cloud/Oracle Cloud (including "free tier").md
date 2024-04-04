## Background
[Oracle Cloud Infrastructure (OCI)](https://www.oracle.com/cloud/) was made public October 20, 2016 providing servers, storage, network, applications and services through a global network of Oracle Corporation managed [data centers](https://en.wikipedia.org/wiki/Data_center "Data center").  Their services encompass [Infrastructure as a Service (IaaS)](https://en.wikipedia.org/wiki/Infrastructure_as_a_service "Infrastructure as a service"), [Platform as a Service (PaaS)](https://en.wikipedia.org/wiki/Platform_as_a_service), [Software as a Service (SaaS)](https://en.wikipedia.org/wiki/Software_as_a_service "Software as a service"), and [Data as a Service (DaaS)](https://en.wikipedia.org/wiki/Data_as_a_service "Data as a service") [^1]. 

## Free Tier
In addition to paid subscription plans they also offer "[Oracle Cloud Free Tier](https://www.oracle.com/cloud/free/)" subscriptions which provide limited featured at no cost to the user:
- Two Oracle Autonomous Databases with powerful tools like Oracle APEX and Oracle SQL Developer
- Two AMD Compute VMs
- Up to 4 instances (cpu cores) of ARM Ampere A1 Compute with 3,000 OCPU hours and 18,000 GB hours per month
- Block, Object, and Archive Storage; Load Balancer and data egress; Monitoring and Notifications [^2]
- Up to 200gb total block storage (divisible between compute VMs & applications)[^3]

### Specific "Free Tier" _compute_ options:
- x86: 2 AMD-based compute VMs up to 1/8 OCPU and 1 GB memory each.
- ARM: 4x Ampere A1 "FLEX" cores and 24 GB of memory usable as 1-4 VMs. `<-- key focus`

### Database
All tenancies get two Always Free [Oracle Autonomous Databases](https://docs.oracle.com/en/cloud/paas/autonomous-database/dedicated/adbaa/index.html#ADBAA-GUID-B5518C12-0362-4A98-AB35-3CB84AC83F31). You can use these databases for transaction processing, data warehousing, Oracle APEX application development, or JSON-based application development. For current regional availability, see the **Always Free Cloud Services** table in [Cloud Regions—Infrastructure and Platform Services](https://www.oracle.com/cloud/data-regions.html).

All tenancies also get an Oracle NoSQL Database with up to 133 million reads per month, 133 million writes per month, and 3 tables with 25 GB storage per table. [Learn more](https://docs.oracle.com/iaas/nosql-database/index.html) about Oracle NoSQL Database.[^4]

### Email Delivery
As part of your Always Free resources, you can send 3000 emails for free per month. Learn more about OCI's [Email Delivery service](https://docs.oracle.com/iaas/Content/Email/home.htm).[^5]
### Prerequisites:
Oracle "free tier" does require _individually unique identification_ in the form of method of payment.
Forms of payment/individually unique identifiers are only accepted as  "credit cards and debit cards that function like credit cards. We do not accept debit cards with a PIN or virtual, single-use, or prepaid cards" or private intermediaries i.e. `privacy.com` (for obvious reasons.)  Oracle assures that "free tier" subscribers **will not be** charged for services unless they agree to upgrading subscriptions to a paid tier.[^6]

### Reclamation of Idle Compute Instances:
Idle Always Free compute instances may be reclaimed by Oracle. Oracle will deem virtual machine and bare metal compute instances as idle if, during a 7-day period, the following are true:
- CPU utilization for the 95th percentile is less than 20%
- Network utilization is less than 20%
- Memory utilization is less than 20% _(applies to [A1 shapes](https://docs.oracle.com/en-us/iaas/Content/FreeTier/freetier_topic-Always_Free_Resources.htm#Details_of_the_Always_Free_Compute_instance__a1_flex) only)[^7]

### Key Take-Aways:
- Various Serice-As-A-Service or Systems-As-A-Service can be created within Oracle's "free tier"
- Compute instances provide up to  \[ARM] 4x CPU, 24gb RAM, 200gb block storage per account
- Ensure utilization remains above "Reclamation" thresholds to prevent them from being closed by the host for under utilization!

---
[1]: https://en.wikipedia.org/wiki/Oracle_Cloud
[2]: https://www.oracle.com/cloud/free/#free-cloud-trial
[3]: https://docs.oracle.com/en-us/iaas/Content/FreeTier/freetier_topic-Always_Free_Resources.htm#blockvolume
[4]: https://docs.oracle.com/en-us/iaas/Content/FreeTier/freetier_topic-Always_Free_Resources.htm#freetier_topic_Always_Free_Resources_Oracle_Database
[5]: https://docs.oracle.com/en-us/iaas/Content/FreeTier/freetier_topic-Always_Free_Resources.htm#freetier_topic_Always_Free_Resources_Notifications
[6]: https://www.oracle.com/cloud/free/faq/
[7]: https://docs.oracle.com/en-us/iaas/Content/FreeTier/freetier_topic-Always_Free_Resources.htm