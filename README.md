# Information
This is a Fork (EdwinHoksberg/php-fcm) that includes FCMController.

You can use the function sendNotification() to send a simple notification.

# PHP-FCM [![Build Status](https://travis-ci.org/EdwinHoksberg/php-fcm.svg?branch=master)](https://travis-ci.org/EdwinHoksberg/php-fcm) [![Coverage Status](https://coveralls.io/repos/github/EdwinHoksberg/php-fcm/badge.svg?branch=master)](https://coveralls.io/github/EdwinHoksberg/php-fcm?branch=master) [![Documentation](https://readthedocs.org/projects/php-fcm/badge/?version=latest)](https://php-fcm.readthedocs.io/en/latest/)
A PHP library for sending Firebase Cloud Messages and managing user topic subscriptions, device groups and devices.

## Installation
Installation with composer:

composer require edwinhoksberg/php-fcm


Installation with composer:
Add to composer.json file:

```bash
  "repositories": [
    {
      "type": "vcs",
      "url": "https://github.com/turboveja/php-fcm"
    }
  ]
```

And:


```bash
  "require": {
    "edwinhoksberg/php-fcm": "dev-master",
  }
```
## Quickstart

You can use the original code to send custom notifications, or the fork method to send simply notifications with the parameters

Fork function:
```php
$apiKey = 'Firebase key code';

$title = 'Notification title';

$body = 'Notification body'; 

$data = [
  'extra_data' => '',
  'example_id' => '',
];

$topics = [
  'topic1', 'topic2' //optional
];

$recipients = [
  'recipient1', 'recipient2' //optional
];

//Send this notification
$fcm = (new FCMController)->sendNotification($apiKey, $title, $body, $data, $topics, $recipients);

```

Original implementation:
```php
// Instantiate the client with the project api_token and sender_id.
$client = new \Fcm\FcmClient($apiToken, $senderId);

// Instantiate the push notification request object.
$notification = new \Fcm\Push\Notification();

// Enhance the notification object with our custom options.
$notification
    ->addRecipient($deviceId)
    ->setTitle('Hello from php-fcm!')
    ->setBody('Notification body')
    ->addData('key', 'value');

// Send the notification to the Firebase servers for further handling.
$client->send($notification);
```

## Full documentation
Read the documentation [here](https://php-fcm.readthedocs.io/en/latest/) or look in the [docs](docs/) directory.

## Tests
Run the unit tests with PHPUnit:
```bash
vendor/bin/phpunit -c phpunit.dist.xml
```

## License
[MIT](LICENSE.md)
