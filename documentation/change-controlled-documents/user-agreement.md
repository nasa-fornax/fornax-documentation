---
short_title: User Agreement
---

# Fornax User Agreement v.1.0

2025-11-24

The Fornax Team is excited to welcome you to the Fornax Science Console. Please be aware that as a Fornax user you will receive the following resources and need to obey the following guidelines:

1. **NASA will provide you with a certain amount of cloud resource “credits”** that can be spent on compute, storage, and egress. (See [Fornax User Resource Allotments and Costs for Open Beta](https://docs.fornax.sciencecloud.nasa.gov/user-resource-allotments-and-costs)).

2. **To help you keep track of your cloud resources** and spending on them, there are “dashboards” in the Fornax Science Console.

3. **In** **the cloud, every second that compute, storage, or egress is in use will cost credits.** This is substantially different from traditional on-premises hardware costs:

   1. **You pay credits for storage every second from the moment it is *allocated* to you**.

      1. If you are allocated 20 GB of storage when you log in, you are charged credits for 20 GB every second thereafter, even if you are only storing 1 GB of data.

      2. You continue to pay credits for storage as long as it is allocated to you; if the cost of 20 GB of storage is 2 credits/month, you pay that every month you own that storage

      3. If you request additional storage, the cost for that comes out of your total allotted credits.

   2. **The second you start a compute instance** (e.g., 2 CPUs with 8 GB RAM), **you are paying credits for compute**, whether you are running a notebook in JupyterHub, or not. For more info, see [Shut Down Your Server](https://docs.fornax.sciencecloud.nasa.gov/quick-start/#id-7-shut-down-your-server) in the Fornax Quick Start Guide.

   3. **Larger compute instances cost more than smaller ones**. Cost goes up with the number of CPUs and the amount of RAM, with the smallest instance costing a hundredth of the largest one.

      1. **We strongly recommend you use the smallest instance for development and debugging of your code**; save the larger instances for when you are sure there are no errors and are ready to run at scale.

4. **If you run out of credits, your access to compute will be severely curtailed, and your storage space may be compacted and archived,** until you receive more credits.

   1. Please plan your use accordingly. Remember, egressing data costs credits \- factor that into your estimates.

   2. You will receive warning messages when you start to get low on credits (at approximately 20% of your starting amount)

   3. Currently, credits are awarded on a yearly basis. If you expend your initial credits before that year is up, you can apply for more by opening a Topic in the [Support area of the Fornax Community Forum](https://discourse.fornax.sciencecloud.nasa.gov/c/support/6).

5. **The Fornax Science Console is for scientific research and education only**.  Anyone found using it for other purposes may have their account instantly revoked.

6. **Please behave professionally when interacting with other users and Fornax staff.**

7. **Failure to follow these guidelines may result in termination of your Fornax account.**

8. **If you have questions**:

   1. For users who don’t have a Fornax Account, send e-mail to: [fornax-helpdesk@lists.nasa.gov](mailto:fornax-helpdesk@lists.nasa.gov)

   2. For users who have a Fornax Account: post in the ["Support” section of the Fornax Community Forum](https://discourse.fornax.sciencecloud.nasa.gov/c/support/)
