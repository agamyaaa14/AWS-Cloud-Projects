<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Host a Website on Amazon S3

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-host-a-website-on-s3)

**Author:** Agamya David  
**Email:** agu.david1410@gmail.com

---

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-host-a-website-on-s3_5d4474f9)

---

## Introducing Today's Project!

### Project overview

In this project, I will demonstrate how to host a static website using AWS S3. I'm doing this project to learn how websites can be hosted on AWS and made publicly accessible, which is an important basic skill when working with cloud services.

### Tools and concepts

Services I used were Amazon S3, bucket creation, bucket policies, managing permissions, and uploading objects.

Key concepts I learnt include how S3 stores website files, how permissions work, and how policies control access to resources.

### Time, challenges, and wins

This project took me approximately 1 hour.
The most challenging part was understanding bucket policies and permissions.

The most rewarding part was seeing my static website successfully go live using the S3 endpoint.

---

## How I Set Up an S3 Bucket

### What I did in this step

In this step, I will open Amazon S3 because we first need to create a bucket that will store the website files.

### How long it took to create the bucket

Creating an S3 bucket took me about 2 minutes.

### Region selection

The Region I picked for my S3 bucket was Asia Pacific (Mumbai) – ap-south-1 because it is the closest region to my location, which usually helps reduce latency.

### Understanding bucket name uniqueness

S3 bucket names are globally unique, which means the bucket name must be unique across all AWS users worldwide. If someone else has already used the name, it cannot be reused.

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-host-a-website-on-s3_ba6d42ad)

---

## Upload Website Files to S3

### What I did in this step

In this step, I will download the HTML files and the zip file containing images because these files are needed to build the website layout and content.

### Files I uploaded

I uploaded two files to my S3 bucket:
● index.html
● a folder containing images and other supporting files

### How the files work together

Both files are necessary because the HTML file defines the structure of the webpage, while the images and other files provide the visual elements used in the page.

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-host-a-website-on-s3_a265af88)

---

## Static Website Hosting on S3

### What I did in this step

In this step, I will enable static website hosting because this allows the files stored in the bucket to behave like a public website instead of just stored files.

### Understanding website hosting

Website hosting means making website files available on the internet so that anyone with the link can access the website.

### How I enabled website hosting

To enable website hosting with my S3 bucket, I enabled static website hosting in the bucket settings and set index.html as the main page.

### Access Control Lists (ACLs)

An Access Control List (ACL) is a set of rules that decides who can access or interact with a resource.
I enabled ACL settings so that the objects inside my bucket could be accessed publicly when required.

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-host-a-website-on-s3_c22c54c0)

---

## Bucket Endpoints

### Understanding bucket endpoint URLs

Once static website hosting is enabled, S3 generates a bucket endpoint URL, which acts as the public web address for the hosted website.
When I first visited the bucket endpoint URL, I saw a 403 Forbidden error.

### What I saw when I tested the endpoint

The error happened because even though public access was allowed at the bucket level, the individual objects inside the bucket were still private.
This meant the website files themselves were not accessible to the public yet.

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-host-a-website-on-s3_22ce4daf)

---

## Success!

### What I did in this step

In this step, I will make the website files publicly accessible because only then the website can actually load for users visiting the link.

### How I resolved the 403 error

To resolve the 403 Forbidden error, I changed the permissions of the uploaded objects to public, which allowed the browser to access the website files.
After this change, the website loaded successfully using the S3 endpoint.

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-host-a-website-on-s3_5d4474f9)

---

## Bucket Policies

### What I did in this extension

In this project extension I'm about to set up a bucket policy.
I'm doing this so that important files like index.html cannot be accidentally deleted.

### Understanding bucket policies

An alternative to ACLs are bucket policies, which provide more detailed control over who can access or modify resources in the bucket.
The benefit of using bucket policies is that they allow control over actions like:
   ● who can delete objects
   ● who can upload new files
   ● who can modify resources

While ACLs are useful for basic object-level access control, bucket policies provide more flexible and secure permission management.

![Image](http://learn.nextwork.org/happy_azure_swift_duck/uploads/aws-host-a-website-on-s3_sm2sm2sm)

### What my bucket policy does

My bucket policy prevents the deletion of the index.html file.
I tested this by attempting to delete the file after applying the policy, and the deletion was blocked, which confirmed that the policy was working correctly.

---

---
