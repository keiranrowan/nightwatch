# Nightwatch

A a simple mailer which allows you to receive email notifications of the output of Cron Jobs. Nightwatch reads Standard Input and then dispatches emails based on the given flags. In the configuration there are both users and groups. You can send emails directly to one or multiple users or you can opt to group them. 

### Usage

```
nightwatch [-u] [-g] [-j] [-h]
           [--user=]                    Send mail to specific user
           [--group=]                   Send mail to users in group
           [--job=]                     Job Name
           [--config="conf.json"]       Path to configuration file
           [--help]                     Display this prompt
```

### Configuration 

```json
{
	"mail" : {
		"host": "mail.example.com",
		"username": "user@example.com",
		"password": "alpine",
		"encryption": "STARTTLS",
		"port": 587
	},
	"groups" : {
		"test": [
			"user"
		]
	},
	"users" : {
		"user": "user@example.com",
	}
}
```

The mail object allows you to set configuration values for SMTP. Host is the hostname of the SMTP server. Encryption is the encryption protocol for SMTP to use. You can opt for either ```STARTTLS``` or ```SMTPS```. Port is the SMTP port for the host. The groups object allows you to assign users to groups. Simply add a new entry given the name and the users who belong to the group. The value for each user is their respective key in the users object. The users object allows you to specify users and their associated email addresses. 

### Dependencies

```
composer
phpmailer/phpmailer: "^6.1"
```
