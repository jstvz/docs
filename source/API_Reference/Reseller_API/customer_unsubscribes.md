---
layout: page
weight: 0
title: Customer Unsubscribes
navigation:
   show: true
---

{% anchor h2 %}
Retrieve Unsubscribes 
{% endanchor %}

Note that you can use *either* the days parameter *or* the start_date and end_date parameter.

<table class="table table-bordered table-striped">
   <thead>
      <tr>
         <th>Parameter</th>
         <th>Required</th>
         <th>Requirements</th>
         <th>Description</th>
      </tr>
   </thead>
   <tbody>
      <tr>
         <td>user</td>
         <td>Yes</td>
         <td>Customer must be registered under your account</td>
         <td>The customer we are retrieving unsubscribes from</td>
      </tr>
      <tr>
         <td>task</td>
         <td>Yes</td>
         <td>
            Must be set to
            <em>get</em>
         </td>
         <td>This will allow you to retrieve the unsubscribes for the specified customer</td>
      </tr>
      <tr>
         <td>date</td>
         <td>No</td>
         <td>Must be set to 1</td>
         <td>Retrieves the timestamps, it will return a date in a MySQL timestamp format - YYYY-MM-DD HH:MM:SS</td>
      </tr>
      <tr>
         <td>method</td>
         <td>Yes</td>
         <td>
            Must be set to
            <em>unsubscribes</em>
         </td>
         <td>Allows you to access unsubscribe functionality</td>
      </tr>
   </tbody>
</table>

{% apiexample get POST https://api.sendgrid.com/apiv2/reseller.manage api_user=your_sendgrid_username&api_key=your_sendgrid_password&method=unsubscribes&user=customer@example.com&task=get&date= %}
  {% response json %}
[
  {
    "email": "email1@domain.com",
    "created": "2009-06-01 19:41:39"
  },
  {
    "email": "email2@domain2.com",
    "created": "2009-06-01 19:41:39"
  }
]
  {% endresponse %}
  {% response xml %}
<?xml version="1.0" encoding="ISO-8859-1"?>

<unsubscribes>
   <unsubscribe>
      <email>email1@domain.com</email>
      <created>2009-06-10 12:40:30</created>
   </unsubscribe>
   <unsubscribe>
      <email>email2@domain2.com</email>
      <created>2009-06-10 12:40:30</created>
   </unsubscribe>
</unsubscribes>

  {% endresponse %}
{% endapiexample %}

* * * * *

{% anchor h2 %}
Delete Unsubscribes 
{% endanchor %}

Since SendGrid does not deliver to unsubscribe addresses, users can remove unsubscribes from their list at any time if re-delivery to an unsubscribed address is desired.

<table class="table table-bordered table-striped">
   <thead>
      <tr>
         <th>Parameter</th>
         <th>Required</th>
         <th>Requirements</th>
         <th>Description</th>
      </tr>
   </thead>
   <tbody>
      <tr>
         <td>user</td>
         <td>Yes</td>
         <td>Customer must be registered under your account</td>
         <td>The customer we are retrieving unsubscribes from</td>
      </tr>
      <tr>
         <td>task</td>
         <td>Yes</td>
         <td>
            Must be set to
            <em>delete</em>
         </td>
         <td>This will allow you to delete an unsubscribe record for the specified customer</td>
      </tr>
      <tr>
         <td>email</td>
         <td>No</td>
         <td>Must be an unsubscribe record</td>
         <td>You must specify the unsubscribe record to remove</td>
      </tr>
   </tbody>
</table>

{% apiexample delete POST https://api.sendgrid.com/apiv2/reseller.manage api_user=your_sendgrid_username&api_key=your_sendgrid_password&method=unsubscribes&user=customer@example.com&task=delete&email=unsubscribe@sample.com %}
  {% response json %}
{
  "message": "success"
}
  {% endresponse %}
  {% response xml %}
<?xml version="1.0" encoding="ISO-8859-1"?>

<result>
   <message>success</message>
</result>

  {% endresponse %}
{% endapiexample %}

* * * * *

{% anchor h2 %}
Add Unsubscribes 
{% endanchor %}

Add unsubscribe email records to their account if they need to stop sending email messages to a specific recipient.

<table class="table table-bordered table-striped">
   <thead>
      <tr>
         <th>Parameter</th>
         <th>Required</th>
         <th>Requirements</th>
         <th>Description</th>
      </tr>
   </thead>
   <tbody>
      <tr>
         <td>user</td>
         <td>Yes</td>
         <td>Customer must be registered under your account</td>
         <td>The customer we are retrieving unsubscribes from</td>
      </tr>
      <tr>
         <td>task</td>
         <td>Yes</td>
         <td>
            Must be set to
            <em>add</em>
         </td>
         <td>This will allow you to add an unsubscribe record for the specified customer</td>
      </tr>
      <tr>
         <td>email</td>
         <td>No</td>
         <td>Must be an unsubscribe record</td>
         <td>You must specify the unsubscribe record to add</td>
      </tr>
   </tbody>
</table>

{% apiexample add POST https://api.sendgrid.com/apiv2/reseller.manage api_user=your_sendgrid_username&api_key=your_sendgrid_password&method=unsubscribes&user=customer@example.com&task=add&email=unsubscribe@sample.com %}
  {% response json %}
{
  "message": "success"
}
  {% endresponse %}
  {% response xml %}
<?xml version="1.0" encoding="ISO-8859-1"?>

<result>
   <message>success</message>
</result>

  {% endresponse %}
{% endapiexample %}