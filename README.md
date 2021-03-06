# commit-alarm
> You must commit! commit! commit! today.
>
> commit-alarm is daily commit alarm pusher to remind you to commit/coding every day.

<br>

### Deploy & Run
-
* Install APEX and Setting the AWS credentials
  > APEX is AWS Lambda management tools

  Follow these [Install APEX](https://github.com/apex/apex/blob/master/docs/installation.md), [Setting AWS credentials](https://github.com/apex/apex/blob/master/docs/aws-credentials.md)
* Modify the profile field in `project.json`

  ```
  {
    ...
    "profile": "<your-profile>"
    ...
  }
  ```
  But, if you want to use default profile, remove the "profile" field
* Replace `role` attribute values in `project.json`, `function.json` with yours
  * project.json
  
    ```
    {
      ...
      "role": "<your-role-arn-of-lambda>",
      ...
    }
    ```
  * functions/push_message/function.json
  
    ```
    {
      ...
      "role": "<your-role-arn-of-lambda>",
      ...
    }
    ```
* Setting the simple slack configuration. Make `slack.ini` in `functions/push_message` directory and write this

  ```
  [slack]
  incoming_webhook_url: https://hooks.slack.com/services/T00000000/B00000000/XXXXXXXXXXXXXXXXXXXXXXXX (your slack incoming webhook url)
  ```
* Deploy!

  ```bash
  apex deploy
  ```
* You should set trigger for scheduling using AWS CloudWatch on AWS console
* The commit-alarm pusher send the random messages to your slack periodically! (It could often bothered you)
* You can test it with apex

  ```bash
  apex invoke push_message
  ```
  
  ![push receive](images/push_receive.png)

  Oh! I'm going to commit now
