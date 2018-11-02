<?php
/**
 * Created by PhpStorm.
 * User: Oscar.Cabezas
 * Date: 02/11/2018
 * Time: 13:25
 */

namespace Fcm;

use Fcm\Push\Notification;

/**
 * Class FCMController
 * @package Fcm
 */
class FCMController
{
    /**
     * @param $api_key
     * @param $title
     * @param string $body
     * @param array $data
     * @param array $topics
     * @param array $recipients
     * @return array
     */
    public function sendNotification($api_key, $title, $body = '', $data = [], $topics = [], $recipients = [])
    {
        //FCM client
        $client = new FcmClient($api_key, '');

        //Notification instance
        $notification = new Notification();
        $notification = $notification
            ->addRecipient($recipients)//Send to recipients
            ->addTopic($topics)//Send to topics
            ->setTitle($title)//Notification title
            ->setBody($body); //Notification body

        //Notification data
        foreach ($data as $key => $value) {
            $notification->addData($key, $value);
        }

        //Send notification
        $response = $client->send($notification);

        //Response return
        return [
            'notification' => [
                'title' => $title,
                'body' => $body,
                'data' => $data,
                'topics' => $topics,
                'recipients' => $recipients

            ],
            'response' => $response,
        ];
    }
}
