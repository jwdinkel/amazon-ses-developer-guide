# Monitoring Using Amazon SES Notifications<a name="monitor-sending-using-notifications"></a>

Amazon SES can notify you of the status of your emails by email or through [Amazon Simple Notification Service \(Amazon SNS\)](https://aws.amazon.com/sns)\. Amazon SES supports the following three types of notifications:

+ **Bounces –** The email is rejected by the recipient's ISP or rejected by Amazon SES because the email address is on the Amazon SES suppression list\. For ISP bounces, Amazon SES reports only hard bounces and soft bounces that will no longer be retried by Amazon SES\. In these cases, your recipient did not receive your email message, and Amazon SES will not try to resend it\. Bounce notifications are available through email and Amazon SNS\. You are notified of out\-of\-the\-office \(OOTO\) messages through the same method as bounces, although they don't count toward your bounce statistics\. To see an example of an OOTO bounce notification, you can use the Amazon SES mailbox simulator\. For more information, see [Testing Amazon SES Email Sending](mailbox-simulator.md)\.

+ **Complaints –** The email is accepted by the ISP and delivered to the recipient, but the recipient does not want the email and clicks a button such as "Mark as spam\." If Amazon SES has a feedback loop set up with the ISP, Amazon SES will send you a complaint notification\. Complaint notifications are available through email and Amazon SNS\.

+ **Deliveries –** Amazon SES successfully delivers the email to the recipient's mail server\. This notification does not indicate that the actual recipient received the email because Amazon SES cannot control what happens to an email after the receiving mail server accepts it\. Delivery notifications are available only through Amazon SNS\.

You can set up notifications using the Amazon SES console or the Amazon SES API\.

There are several important points to know about notifications:

+ **Notification settings are configured on a per\-verified\-identity basis – ** There is no global setting, and notification settings apply only to the verified identity in the AWS region in which you configured the settings\.

+ **Verified domain notification settings apply to all mail sent from email addresses in that domain *except* for email addresses that are also verified – **The configurations for email addresses are separate from the configuration for the domain, so changing the domain configuration will have no effect on the email address configuration\. For example, if you verify only *example\.com* and configure its bounce notification settings, bounce notifications for email from *sender@example\.com* will use those settings\. However, if you verify both *example\.com* and *sender@example\.com*, *sender@example\.com* will **not** use the bounce notification settings that are configured for *example\.com*\.

+ **You must receive bounce and complaint notifications either by email or through Amazon SNS – **The default method is by email, through a feature called *email feedback forwarding*\. Delivery notifications are optional and available only through Amazon SNS\. 

+ **If you choose to receive notifications for all three types of events, then you might receive multiple notifications for one email – **For example, the receiving mail server accepts the email \(triggering a delivery notification\), but the recipient marks the email as spam, triggering a complaint notification\.

+ **Before you start sending email, make sure that you set up a process to handle bounces and complaints – **Your process needs to monitor bounces and complaints and to remove those addresses from your mailing list\. Excessive bounces and complaints put your Amazon SES account at risk of termination\. You will need to analyze each bounce and complaint message that you receive to determine the cause\. Bounces are usually caused by attempting to send to a nonexistent recipient; complaints arise when recipients indicate that they do not want to receive your message\. In either case, we strongly recommend that you stop sending to these email addresses\.

+ **You can test notifications by using the Amazon SES mailbox simulator – **Emails that you send to the mailbox simulator do not affect your bounce and complaint rates\. For more information, see [Testing Amazon SES Email Sending](mailbox-simulator.md)\.

The following sections describe the notification methods:

+ To receive notifications by email \(which applies to bounces and complaints only\), see [Amazon SES Notifications Through Email](notifications-via-email.md)\.

+ To receive notifications through Amazon SNS \(which applies to all three notification types\), see [Amazon SES Notifications Through Amazon SNS](notifications-via-sns.md)\.