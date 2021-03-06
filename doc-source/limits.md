# Limits in Amazon SES<a name="limits"></a>

This topic lists limits within Amazon Simple Email Service \(Amazon SES\)\.

## Limits Related to Email Sending<a name="limits-email-sending"></a>

The following tables list limits related to email sending\.

### Sending Limits<a name="limits-sending"></a>

**Note**  
Sending limits are based on recipients rather than on messages\.


****  

| Limit | Description | 
| --- | --- | 
| Sending limits in the sandbox environment |  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/ses/latest/DeveloperGuide/limits.html) To increase your sending limits, open an SES Sending Limit case in Support Center\. For more information, see [Moving Out of the Amazon SES Sandbox](request-production-access.md)\.  | 

### Message Limits<a name="limits-message"></a>


****  

| Limit | Description | 
| --- | --- | 
|  Maximum message size \(including attachments\)  |  10 MB per message \(after base64 encoding\)\.  | 
|  Accepted header fields  |  Amazon SES accepts any email headers that follow the format described in [RFC 822](https://www.ietf.org/rfc/rfc0822.txt)\.  | 
|  Accepted attachment types  |  Amazon SES accepts all file attachment types *except* for attachments with file extensions listed in [Appendix: Unsupported Attachment Types](mime-types-appendix.md)\.  | 

### Sender and Recipient Limits<a name="limits-sender-recipient"></a>


****  

| Limit | Description | 
| --- | --- | 
|  Sender address  |  Both in and out of the sandbox, you are required to verify the "From", "Source", "Sender", and "Return\-Path" email addresses or domains, although *not* "Reply\-To"\.  | 
|  Recipient address   |  In the sandbox environment, all "To" addresses except for Amazon SES mailbox simulator addresses must be verified\. If you don't want to verify your "To" addresses, open an SES Sending Limit case in Support Center\. For more information, see [Moving Out of the Amazon SES Sandbox](request-production-access.md)\.  | 
|  Maximum number of recipients per message  |  50 recipients per message\.A recipient is any "To", "CC", or "BCC" address\.  | 
|  Maximum number of identities you can verify  |  10,000 identities \(domains or email addresses, in any combination\) per AWS Region\.  | 

### Limits Related to Email Sending Event Publishing<a name="limits-publishing"></a>


****  

| Limit | Description | 
| --- | --- | 
|  Maximum number of configuration sets  |  10,000  | 
|  Maximum number of event destinations per configuration set  |  10  | 
|  Maximum number of dimensions per CloudWatch event destination  |  10  | 

### Amazon EC2\-Related Limits<a name="limits-ec2"></a>


****  

| Limit | Description | 
| --- | --- | 
|  Email sending over port 25  |  Amazon EC2 throttles email traffic over port 25 by default\. To avoid timeouts when sending email through the Amazon SES SMTP endpoint from Amazon EC2, use a different port \(587 or 2587\) or fill out a [Request to Remove Email Sending Limitations](https://aws-portal.amazon.com/gp/aws/html-forms-controller/contactus/ec2-email-limit-rdns-request)\.  | 

## Limits Related to Email Receiving<a name="limits-email-receiving"></a>

The following table lists limits related to email receiving\.


****  

| Limit | Description | 
| --- | --- | 
|  Maximum number of rules per receipt rule set  |  100  | 
|  Maximum number of actions per receipt rule  |  10  | 
|  Maximum number of recipients per receipt rule  |  100  | 
|  Maximum number of receipt rule sets per AWS account  |  20  | 
|  Maximum number of IP address filters per AWS account  |  100  | 
|  Maximum email size \(including headers\) that can be stored in an Amazon S3 bucket  |  30 MB  | 
|  Maximum email size \(including headers\) that can be published using an Amazon SNS notification  |  150 KB  | 

## General Limits<a name="limits-email-general"></a>

The following table lists limits that apply to both email sending and email receiving\.

### Amazon SES API Limits<a name="limits-api"></a>


****  

| Limit | Description | 
| --- | --- | 
|  Rate at which you can call Amazon SES API actions  |  All actions \(except for `SendEmail` and `SendRawEmail`\) are throttled at one request per second\. For more information about the Amazon SES API, see the [Amazon Simple Email Service API Reference](http://docs.aws.amazon.com/ses/latest/APIReference/)\.  | 


****  

|  | 
| --- |
| For technical discussions about various Amazon SES topics, visit the [Amazon SES Blog](https://aws.amazon.com//blogs/ses/)\. To browse and post questions, go to the [Amazon SES Forum](https://forums.aws.amazon.com/forum.jspa?forumID=90)\. | 