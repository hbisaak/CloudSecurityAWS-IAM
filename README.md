# CloudSecurityAWS-IAM

<h2>Description</h2>
Project consists of useing AWS Identity and Access Management (IAM) to control who is authenticated (signed in) and authorized (has permissions) to use account resources. In this project I used AWS IAM to set up access control policies for new EC2 instances, usergroups and a new user. 
<br />


<h2>Utilities Used</h2>

- <b>AWS IAM</b> 
- <b>Amazon EC2</b>

<h2>Environments Used </h2>

- <b>Amazon Web Service</b>

<h2>Walkthrough</h2>

<b>Tags</b>

I've set up two EC2 instances to test the eddectiveness of the permission settings in AWS IAM. The Tags or lables help define mass grouping management and applying security priciples. 

![instance 2 name and tags](https://github.com/user-attachments/assets/5eba7141-7bf5-4373-a634-ee5891466e5e)

The tag I've used on my EC2 instances in called Env (environment). The value
I've assigned for my instances are "production" & "development". This
represents the 2 different environments that I'm using to simulate the build
and release of an app.

<b>IAM Policies</b>

IAM Policies are rules that allow/deny users/resources permissions to
perform specified actions to my AWS account's recourses.

For this project, I've set up a policy using JSON editor.
I've created a policy that allows all EC2 related actions to all EC2 instances
that have the environment (env) tag "development." It also denies creating
and deleting tags for all EC2 instances. When creating a JSON policy, you have to define
its Effect, Action and Resource.
When writing JSON policy statements you must specify the; Effect=i.e Allow
or Deny. Action=i.e the specific action we want to allow or deny. Resource=i.e
the specific resource/group of resources in my AWS account that this policy
will take effect on.

![persmissons in JSON](https://github.com/user-attachments/assets/77efad26-8257-4660-aaab-23dc25c87529)

<b>Account Alias</b>
An account alias is a custom name that I can assign to my AWS account. This
custom name would replace my numeric Account ID in my account's log in
URL in order to make the experience more user friendly.
Creating an account alias took me less than one minuet, very quick.
Now, my new AWS console sign-in URL is https://nextwork-aliashbisaak.signin.aws.amazon.com/console As you can see, this is much more friendly than a string of numbers.

![account alias](https://github.com/user-attachments/assets/0c36b9e2-bb60-44e3-bad8-e504c21cf8db)

<h>IAM Users and User Groups<h/>

<b> Users</b>

IAM users are other log-ins/people who have access to my AWS account.
These users are created by myself using the AWS IAM service. I can
designate my IAM users Access to my AWS accounts resources/ services

<b>User Groups<b/>

I created an IAM User Groups. IAM user groups are useful for grouping and
managing users permissions at a group level. They act like folders when it
comes to mass assigning permissions/policies to multiple users.
I attached the policy I created to this user group, which means all users added
to that user group will automatically inherit the user groups access
permissions.

<h2>Logging in as an IAM User </h2>
Once my new user was set up, there were two ways I could share the sign in
details. The first way is emailing sign in instructions and the second way
would be downloading an .osv file.
Once I logged in as my IAM user, I noticed several red access denied
messages on my user dashboard

![user sign in details](https://github.com/user-attachments/assets/5a27ba1e-d6c7-49ff-8c2f-0bff0a60d481)

<h2>Testing IAM Policies</h2>
I tested my JSON IAM policy by trying to STOP the production and
development instances. i.e triggering the STOP Instance action.
<b>Stopping the production instance</b>
When I tried to stop the production instance, an error message stopped me
and explained that this user was not authorized to stop the production
instance.

![stop app prevention](https://github.com/user-attachments/assets/506844f8-745b-4378-9cf4-00b6d805712a)

<b>Stopping the development instance<b/>

Next, when I tried to stop the development instance, it could be stopped by
this user. Reason being the policy I created and attached to this user's group
allowed all EC2 related actions to all instance/resources with the env development tag.

![instance dev stopped](https://github.com/user-attachments/assets/1318dd8d-e6bb-46f8-9c07-cb1c5f5d2aa1)

and that about wraps it up. easy-peezy lemon squeezie. 
