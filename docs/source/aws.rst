########################
Server Security With AWS
########################

Elasticsearch Services (Amazon ES)
==================================

Amazon ES is an open-source search engine. We will access the Amazon ES Service via the `Amazon ES console <https://console.aws.amazon.com/es/home>`_ 
which can create, configure, and monitor your domains and upload data.

Click on the Elasticsearch Service from the list of AWS service displayed. The next action displays the list of existing Elasticsearch domains.

On selecting the desired Domain, the domain configurations which have already been set are displayed. Let us see how you can manage the domain security from here.


**Configure Cluster**

*Amazon ES EndPoints*

A domain search endpoint for uploading data and submitting search requests. Using this, you can access the configuration API and have domain-specific endpoints for accessing the search API.

.. image:: https://s3-ap-southeast-1.amazonaws.com/kontikilabs.com/readthedocs/endpoint.png

**Modify the access policy**

This section lets you allow or block access to your selected domain. You can directly edit the access policy from *'Add or edit the access policy'* or you can opt for any one of the policy templates from the *'Select a template'* dropdown list as displayed below.

.. image:: https://s3-ap-southeast-1.amazonaws.com/kontikilabs.com/readthedocs/modify+access+policy.png
    :align: center


+-----------------------------------------------------------------+-----------------------------------------------------------------+
|                                                                 |                                                                 |
|                      Access Policies                            |                      Description                                |
|                                                                 |                                                                 |
+=================================================================+=================================================================+
| Allow or deny access to one or more AWS accounts or IAM users   | Allow or deny access to one or more AWS accounts or IAM users   |
+-----------------------------------------------------------------+-----------------------------------------------------------------+
|                                                                 |                                                                 |
|                                                                 | This policy is not recommended because it allows anyone to      |
|                                                                 | delete, modify, or access indexes and documents in your domain. | 
| Allow open access to the domain                                 | It is intended only as a convenience for testing. Don't load    |
|                                                                 | sensitive data to a domain that has these settings.             |
|                                                                 |                                                                 |
|                                                                 |                                                                 |
+-----------------------------------------------------------------+-----------------------------------------------------------------+
|                                                                 |                                                                 |
|                                                                 | This policy allows access only through the Amazon ES console or |
| Deny access to the domain                                       | or by the owner of the AWS account who created the domain.      | 
|                                                                 |                                                                 |
+-----------------------------------------------------------------+-----------------------------------------------------------------+
|                                                                 |                                                                 |
|                                                                 | This policy is used to restrict anonymous access to a specific  |
| Allow access to the domain from specific IP(s)                  | IP address. It also allows us to add multiple IP addresses      | 
|                                                                 | The activation process takes 10-15 mins                         |                  
|                                                                 |                                                                 |
+-----------------------------------------------------------------+-----------------------------------------------------------------+
|                                                                 |                                                                 |
|                                                                 | This policy provides a convenient way to import an existing     |
| Copy access policy from another domain                          | access policy from another domain.                              | 
|                                                                 |                                                                 |
+-----------------------------------------------------------------+-----------------------------------------------------------------+


Amazon Elastic Compute Cloud (Amazon EC2)
=========================================

Amazon EC2 provides scalable computing capacity in the AWS cloud. You can use Amazon EC2 to launch as many, or as few virtual servers as you need, configure security and networking, and manage storage. 

Select 'Running Instances' from the Amazon EC2 resources. The running instance displays a list of already created servers. Each instance can be assigned a particular security group.

**Security Group**

A virtual firewall that controls the traffic for one or more instances. Whenever an instance is launched, it is important that at least one security group is assigned to the instance for reliability. 
You can create a security group from the below screen which appears on clicking on the existing security group or while creating a server.


.. image:: https://s3-ap-southeast-1.amazonaws.com/kontikilabs.com/readthedocs/create+SG.png

**Security Group Rules**

Outbound: Protects against outgoing traffic from the enterprise network.By default, all the outbound traffic is allowed.

+------------------+-------------+---------------------+
|                  |             |                     |
|  Protocol type   | Port number | Destination IP      |
|                  |             |                     |
+==================+=============+=====================+
|   All            | All         | 0.0.0.0/0           |
+------------------+-------------+---------------------+

Inbound: Protects the network against incoming traffic from the internet. You can set the inbound rules as:

+------------------+-------------+---------------------+
|                  |             |                     |
|  Protocol type   | Port number | Destination IP      |
|                  |             |                     |
+==================+=============+=====================+
|   TCP            | 22 (SSH)    | 203.0.113.1/32      |
+------------------+-------------+---------------------+
|   TCP            | 80 (HTTP)   | 0.0.0.0/0           |
+------------------+-------------+---------------------+
|   ICMP           | All         | 0.0.0.0/0           |
+------------------+-------------+---------------------+


.. image:: https://s3-ap-southeast-1.amazonaws.com/kontikilabs.com/readthedocs/security+group.png



Amazon Simple Storage Service (S3)
==================================

Storage space for images, videos and anything which needs a link format to be displayed publicly.

Create bucket and select it from the list of buckets displayed and go to the permissions tab to manage the control.

**Bucket Policy Tab**

Opt for the *'policy generator'* option, present below the text area to set the bucket policies. Policy generator is a tool that enables you to create policies that control access to AWS products and resources.

.. image:: https://s3-ap-southeast-1.amazonaws.com/kontikilabs.com/readthedocs/policy+generator.png
    :align: center


.. figure:: https://s3-ap-southeast-1.amazonaws.com/kontikilabs.com/readthedocs/step+1.png

    Choose the 'S3 Bucket Policy' from the drop down.

.. image:: https://s3-ap-southeast-1.amazonaws.com/kontikilabs.com/readthedocs/step+2.png


+--------------+---------------------------------------------------------------------------+
|              |                                                                           |
| Option       |                      Description                                          |
|              |                                                                           |
+==============+===========================================================================+
| Effect       | Specifies whether the statement will result in allow or an explicit deny. |
+--------------+---------------------------------------------------------------------------+
|              |                                                                           |
|              | Specify the user (IAM user, federated user, or assumed-role user),        |
| Principle    | AWS account, AWS service, or other principal entity that is allowed       |
|              | or denied access to a resource.  We use * to give every one access.       |
|              |                                                                           |
+--------------+---------------------------------------------------------------------------+
|              |                                                                           |
| Actions      | Describes the specific action or actions that will be allowed or denied.  |
|              |                                                                           |
+--------------+---------------------------------------------------------------------------+
|              |                                                                           |
| ARN          | Amazon Resource Name (ARN) condition operators let you construct condition| 
|              | elements that restrict access based on comparing a key to an ARN.         |
|              |                                                                           |
+--------------+---------------------------------------------------------------------------+


How to copy ARN and use it?

* Go to the bucket list and click on your desired bucket row. 

* A popup will appear on your right side allowing you to copy the 'Bucket ARN' 

* Add '/<key_name>' at the end of 'arn:aws:s3:::<bucket_name>'. We use '*' to give access to all uploaded files.

* Use the file name, if you want a particular file to be exposed publicly and use comma to separate the names.

.. image:: https://s3-ap-southeast-1.amazonaws.com/kontikilabs.com/readthedocs/copy+ARN.png
    :align: center
    :height: 400px

Click on '*Add statement'* after completing the 2 steps. You will then be asked to confirm the statement. Next proceed with the '*Generate policy*' button that gives you policy JSON document. Paste the JSON on policy generator text area under the '*Bucket Policy*' tab of Amazon S3.

**CORS configuration Tab**

Cross origin resource sharing defines a way for client web applications that are loaded in one domain to interact with resources in a different domain. ::

	<!-- Sample policy -->
	<CORSConfiguration>
	    <CORSRule>
	        <AllowedOrigin>*</AllowedOrigin>
	        <AllowedMethod>GET</AllowedMethod>
	        <MaxAgeSeconds>3000</MaxAgeSeconds>
	        <AllowedHeader>Authorization</AllowedHeader>
	    </CORSRule>
	</CORSConfiguration>

All the above steps will help you secure our server. In order to get your AWS credentials, please contact Anurag Mishra, our Server Admin.



