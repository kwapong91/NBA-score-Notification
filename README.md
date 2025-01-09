# NBA-score-Notification

This is an event-driven AWS architecture that sends **SNS subscribers** real-time NBA score updates using data from the **SportsDataIO API**. The architecture leverages **AWS Lambda** and **AWS EventBridge** for efficient automation and scalability.

## Architecture Overview

![1736355453454](https://github.com/user-attachments/assets/b0ff4f96-e4c1-4147-8ec1-e489d37b184b)


### Components
1. **Amazon EventBridge**: Triggers the Lambda function on a scheduled interval.
2. **AWS Lambda**: Fetches NBA game data from the SportsDataIO API and processes it.
3. **Amazon SNS**: Sends notifications with game updates to all subscribed endpoints (email, SMS, etc.).

### Key Features
- **Event-Driven Architecture**: Automated updates based on a scheduled trigger.
- **Real-Time Data**: Fetches live NBA game data from the SportsDataIO API.
- **Scalable Notifications**: Supports multiple subscribers via Amazon SNS.
- **Infrastructure as Code (IaC)**: Uses AWS CloudFormation for infrastructure management.

## How It Works
1. **Scheduled Rule**: EventBridge Scheduler runs the Lambda function at a predefined interval (e.g., every hour).
2. **Data Fetching**: Lambda function makes an API request to SportsDataIO to retrieve NBA game information.
3. **Processing**: Lambda formats the data into user-friendly notifications.
4. **Notification Delivery**: SNS sends the formatted game updates to all subscribed endpoints.

## Requirements
- **AWS Account** with permissions to use EventBridge, Lambda, and SNS.
- **SportsDataIO API Key** for accessing NBA game data.

## Setup Instructions
1. Clone this repository:
   ```bash
   git clone <repository-url>
   ```
2. Deploy the CloudFormation template:
   ```bash
   aws cloudformation deploy --template-file template.yaml --stack-name NBA-Score-Notification
   ```
3. Configure environment variables for the Lambda function:
   - `NBA_API_KEY`: Your SportsDataIO API key.
   - `SNS_TOPIC_ARN`: The ARN of the SNS topic created by CloudFormation.
4. Subscribe to the SNS topic:
   - Add your email or phone number to receive notifications.
   ```bash
   aws sns subscribe --topic-arn <SNS_TOPIC_ARN> --protocol email --notification-endpoint <your-email>
   ```

## Example Notification
```text
Game Status: Final
Golden State Warriors vs Los Angeles Lakers
Final Score: 120-115
Start Time: 2023-01-07T03:00:00Z
Channel: ESPN
Quarter Scores: Q1: 30-25, Q2: 25-30, Q3: 35-30, Q4: 30-30
```

## Future Enhancements
- Add support for multiple sports leagues.
- Enable dynamic scheduling of notifications.
- Integrate with additional APIs for extended data insights.

---

Feel free to reach out or contribute to improve this project!
