
## ContentDistro

### Description
**ContentDistro** is a social media scheduling tool designed for high-volume agencies that manage multiple clients across various platforms. With a content calendar built on Airtable, users can easily add captions, upload images and videos, and manage their content efficiently.

ContentDistro leverages Airtable for front-end content management and **Make.com** for handling automations and scheduling, offering a cost-effective solution to agencies managing large volumes of content without significant cost increases like mainstream tools such as Buffer or Hootsuite.

### Features
- **Multi-client management**: Handle content for several clients across multiple platforms in a single Airtable workspace.
- **Cost-effective**: Save money by using Airtable's basic team plan, avoiding price increases that typically come with other social media management tools.
- **Automation**: Seamless integration with Make.com for scheduling and automating content distribution.
- **Custom scripts**: Trigger Airtable scripts to automate the workflow, reducing manual efforts.
- **Content calendar**: Manage all your content through an intuitive Airtable calendar interface.

### Tech Stack
- **Airtable**: For managing the content database and user interface.
- **Make.com**: For automation and handling scheduling based on custom scripts.
- **Webhooks**: Used to trigger logic in Make.com workflows.

### Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/okuobongntuk/ContentDistro.git
   cd ContentDistro
   ```

2. Set up your Airtable account and create a base for content management.
3. Configure the webhooks and automation workflows in Make.com using the provided blueprint.

### Usage
1. Set up your content calendar on Airtable by adding captions, images, and videos.
2. Define the due date for each content item.
3. When the content's due date arrives, the Airtable automation triggers a script that sends the content to a Make.com webhook.
4. Make.com retrieves the record from Airtable and schedules it for distribution.

### Automation Logic

The **Make.com** Blueprint handles content distribution logic through webhooks and Airtable integration. Below is an overview of the automation process:

1. **Webhook Trigger (CustomWebHook)**: The webhook is triggered when a content item’s due date is reached in Airtable. This retrieves the content record, including the post ID, media URLs, and associated details.
   
2. **Retrieve Record from Airtable (ActionGetRecord)**: The webhook sends the post ID to retrieve the associated record from Airtable. This record contains the caption, media (images or videos), and the platforms to which the content will be posted.

3. **Platform-Specific Routing**: The content is routed to the appropriate platform (e.g., Facebook, Instagram, LinkedIn) based on the platforms listed in the record.
    - **Facebook**: Posts can be text, photos, videos, or reels.
    - **Instagram**: Posts can be photos, videos, or reels. For carousel posts, multiple photos or videos are supported.
    - **LinkedIn**: Supports text, photo, and video posts for company pages.

4. **Media Upload**: If the post contains media (images or videos), the respective media file is uploaded to the platform along with the caption from the Airtable record.

5. **Error Handling**: For each platform, if an error occurs during the post creation, the automation is designed to ignore the error and move on without disrupting the rest of the workflow.

6. **Completion**: Once the media and caption are successfully uploaded, the post is scheduled or published on the corresponding platform.

For a detailed breakdown of the platform-specific routes and conditions, refer to the blueprint file included in this repository.

### Contributing
1. Fork the repository.
2. Create a new branch for your feature:
   ```bash
   git checkout -b feature-name
   ```
3. Make your changes and commit:
   ```bash
   git commit -m "Add some feature"
   ```
4. Push to the branch:
   ```bash
   git push origin feature-name
   ```
5. Open a pull request.

### License
Distributed under the MIT License. See `LICENSE` for more information.
