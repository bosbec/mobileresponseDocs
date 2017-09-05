# Message templates #
The messages (MessageTemplates) are just as the name suggests a template. The template contains up to
4 different message parts, but the parts must be of different type.
- App-message to send messages to MobileResponse - iOS and Android Apps.
	- Unique properties are SenderId and InboxId can be configured to send app-messages
from different app-users.

• Email-message to send email-messages to receivers with email configured.
o IsBodyHtml property should be true if sending email with HTML-content.
o From should be a valid email-address.
• IOT-message to send MQTT-messages to a specific service/topic that is defined by the receiving
unit.
• SMS-message to send SMS text-messages to mobile phone receivers.
o SenderName must be valid alphanumeric (or mobile-phone number)
To be able to send a questionnaire, a form, which in turn is replaced with a link or ShortLink2. When
sending a form in an Email or SMS message you need to put the text [form] in the body of the message to
let MobileResponse know where to insert the link to the form.
When sending messages in a workflow, it is possible to insert unique data for each receiver simply by
typing the metadata key, for instance [firstname] would cause MobileResponse to try to replace the text
[firstname] in the message body with data found on the receiving unit.
It is also possible to replace parts or the entire message body with data from the workflow context
metadata. Then all receivers will have the same replacement. For example, if I were to have a message
body: “[my-data-1] [firstname]!” and in some way set the workflow context metadata.my-data-1 to
“Hello”, then all receivers of my message would have a message saying Hello (from workflow context
metadata) and their own first name (defined in each unit’s metadata).