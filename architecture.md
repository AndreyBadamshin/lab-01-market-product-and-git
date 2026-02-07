## Product Choice

Product name: Telegram
Link to the product's website: https://web.telegram.org/
Short description of the product: Telegram is social media and instant messaging service, founded by Pavel Durov and Nikolai Durov.

## Main Components

[!Telegram Component Diagram](docs/diagrams/out/telegram/component-diagram/Component%20Diagram.svg)

[Link to PlantUml code](docs/diagrams/src/telegram/component-diagram.puml)

-Notification/Updates Service: Sends out push-notifications to users and manages updates of the Telgram app

-Message Handling Service: Manages sending messages and cache, writes messages from the group chats to the database

-Media & File Service: Manages the file system and file input/output

-Channel/Broadcaset Service: Controls publications in telegram channels, database read/write operations and cache access

-Auth & Session Service: Controls the authorization process

## Data Flow

[!Telegram Sequence Diagram](docs/diagrams/out/telegram/sequence-diagram/Sequence%20Diagram.svg)

[Link to PlantUml code](docs/diagrams/src/telegram/sequence-diagram.puml)

Media Upload

Selected photo is propageted to the Mobile App, saveFilePart is downloaded to the Media Service through the MTProto Gateway. File Chunk is written into the Distribute DFS, File Metadata is written into the Sharded DataBase. When part of the file is downloaded successfully, the signal is sent to the MTProto Gateway and the next part gets written into the database. The process is repeated until the file fully downloaded.

## Deployment

[!Telegram Deployment Diagram](docs/diagrams/out/telegram/deployment-diagram/)

[Link to PlantUml code](docs/diagrams/src/telegram/deployment-diagram.puml)

Core telegram Components are deployed in the Telegram Global Infrastructure. Mobile and desktop apps along with the web-client are deployed locally on users devices. External services like SMS and Push services are deployed in external ecosystems.

## Assumptions

I assume that message sending process is divide into several steps to ensure the fastest delivery possible while applying the appropriate security measures.

## Open questions

How databases' information is stored to avoid duplication?
How external services are integrated with telegram core services?
