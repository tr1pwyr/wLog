---
title: 'Cloud Computing for Developers'
date: '2022-06-17'
status: publish
permalink: /cloud-computing-for-developers
author: TECHNOR471
description: 'Amazon AWS does not seem to be the most cost effective solution.'
type: post
id: 1110
thumbnail: /uploads/2022/06/cloud-computing.webp
category:
    - Tech
tags:
    - amazon
    - aws
    - azure
    - cloud
    - gcp
    - google
    - 'google cloud platform'
    - microsoft
---

The time eventually comes for every developer when they have to choose a cloud provider to deploy their app on. Microsoft’s Azure, Amazon AWS, and the Google Cloud Platform are the big three cloud platforms. Each offer slightly different services and each seem to have their pluses and minuses. It is almost impossible to come up with an apples to apples comparison, but I am going to try!

![Cloud Computing](/uploads/2022/06/cloud-computing.webp)

### Amazon AWS

[Amazon’s AWS](https://aws.amazon.com/) cloud computing offering is the most mature and the biggest dog on the block. AWS has been around since 2002 but relaunched in 2006 combining the three initial service offerings of Amazon S3 cloud storage, SQS, and EC2.

From my admittedly less than scientific research Amazon AWS does not seem to be the most cost effective solution. This is obviously more important to me than it might be to big organizations. AWS does seem to be the leader in market-share as well as number of offerings and number of data centers.

If I were working for a big company and wanted to make sure that I kept my job, I would chose AWS. Their pricing is competitive ( and for the biggest installations maybe even cheaper ) and the services are rock solid and mature. However I am just an independent developer trying to get the most bang for the buck.

Another huge plus for AWS is that they offer server-side encryption for S3. Additionally they also offer the most cloud based services but this is less important to me.

### Microsoft’s Azure

[Microsoft Azure](https://www.microsoft.com/en-us/azureessentials/) is a cloud computing service created by Microsoft for deploying applications and services through a global network of Microsoft-managed data centers. Say what you want about Microsoft but they have been making some interesting products lately, they have [embraced Linux](https://www.infoworld.com/article/3050845/microsoft-windows/microsoft-embraces-linux-way-too-late.html), and have worked hard to make Python on Windows easy as installing any other program.

[Microsoft](https://headlin3s.com/tag/microsoft)‘s cloud platform is a strong offering. They offer hundreds of integrated services on Azure including storage and backups, virtual machines, databases, and more importantly for me: services for mobile and web apps.

If I were developing applications for Windows 10 Azure would be a no-brainer choice. Obviously that’s not all you can do on the platform, but the Azure Active Directory is fantastic if you do have allot of Windows PC’s to manage. Azure can also be used with standards-based technologies as well as proprietary Microsoft solutions.

### The Google Cloud

First, a bit of a disclaimer: I have always been a Google fan boy. I distinctly remember when I first used Google and realized that Infoseek, AltaVista, et all, were doomed… While I freely admit that [Google](https://headlin3s.com/tag/google) has it’s own privacy related issues, I remain a fan. I use Gmail, feel lucky often, and write in Google Docs. But I digress…

![Cloud Computing Data Center](/uploads/2023/02/cloud-computing-too.webp)

Google’s cloud computing](https://cloud.google.com/) is the newest of the three and runs on the same infrastructure as their search, gmail, docs, etc. While their cloud computing platform is not as mature as AWS, in my testing their CLI tools and service API are more usable. Another thing in Google’s favor is that they love Python almost as much as I do. While you can also use Python on the other platforms, there are ( very good ) Python specific tutorials for using the [Google Cloud to build Python apps](https://cloud.google.com/python/docs/). AWS is billed by the hour, while Google Cloud uses the Pay per use (billed by the minute).

Hopefully I will be working with big data, and nobody does big data as well as Google. Google’s BigQuery alone sets Google apart from the other offerings on this point.

There are many many other cloud platforms like IBM Bluemix, Oracle Cloud; and smaller offerings such as Linode, [Vultr](https://www.vultr.com/?ref=8874381) and Heroku. However I will be using one of the big three for a number of reasons. Doing this research and post has me leaning towards Google’s Cloud Platform but my mind is not completely made up. Us the comments below to convince me your favorite cloud platform is better.