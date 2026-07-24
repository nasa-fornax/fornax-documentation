---
short_title: User Resource Allotments and Costs
---

# Fornax User Resource Allotments and Costs

V.1.3  July 17, 2026

Upon your first login to the Fornax Science Console you will have:

* **1000 credits** for spending on cloud resources (compute, storage, and egress); this is renewed yearly, at the beginning of the fiscal year (Oct. 1). If you need more credits before the renewal date, contact the [Fornax Helpdesk](https://docs.fornax.sciencecloud.nasa.gov/fornax-community-forum/#helpdesk).
* **A 200 GB ceiling** to the private storage available in your Home Directory; if your work requires more, please see the options below or contact the [Fornax Helpdesk](https://docs.fornax.sciencecloud.nasa.gov/fornax-community-forum/#helpdesk).
* **Access to additional, private S3 storage**, mounted as “s3-storage” under your Home Directory, for a cheaper storage option (see table, below)
* **Additional /scratch storage** space that can be expanded to temporarily house very large datasets for software that expects data mounted as a traditional file system. See [Data Storage](https://docs.fornax.sciencecloud.nasa.gov/data-storage/) in the Fornax docs for more details

The [Fornax Science Console Dashboard](https://docs.fornax.sciencecloud.nasa.gov/dashboard/) will help you keep track of what you have spent.

**For more information**, see: [Compute and Storage](https://docs.fornax.sciencecloud.nasa.gov/intro-forsc/#intro-best-practices) in the Fornax docs

**Typical usage costs**, for reference:

* Running the small instance for 100 hours: 8.70 credits
* Running the large instance for 100 hours: 77 credits
* Running the XL instance for 100 hours: 759 credits
* Running the small instance 40 hours a week for a year: 181 credits
* Using 100 GB of storage in your home directory for a year: 108 credits
* Using 1 TB of storage in your home directory for a year: 1,080 credits
* Using 1 TB of private S3-storage for one year: 276 credits
* Egressing 20 GB of data: 1.80 credits

The table below shows the approximate costs of various compute, storage, and egress options.

| Compute (\# CPU, GB RAM) | Cost (credits/hour) |  |
| :---- | :---- | :---- |
| Small (2, 8\) | 0.087 |  |
| Medium (4, 8\) | 0.153 |  |
| Large (16, 64\) | 0.768 |  |
| XLarge (128, 512\) | 7.59 |  |
| **Storage (AWS media)** | **Cost (credits/GB/month)** |  |
| Home Directory (FSx) | 0.090 | User is charged for amount of storage in use. |
| Additional private storage (S3)   | 0.023 | User is charged for amount of storage in use. |
| /scratch storage (EBS) | 0.080 | User is charged for amount of storage requested \- see docs in link above. |
| **Egress** | **Cost (credits/GB)** |  |
| Standard Egress rate | 0.090 |  |
