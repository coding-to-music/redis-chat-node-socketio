# redis-chat-node-socketio

# 🚀 Javascript full-stack 🚀

https://github.com/coding-to-music/redis-chat-node-socketio

https://redis-chat-node-socketio.vercel.app

by ansel brandt https://github.com/anselbrandt

https://ansel.vercel.app/map

https://github.com/anselbrandt/redis-chat-node-socketio

## Environment Values

```java

PUBLIC_URL="https://redis-chat-node-socketio.vercel.app"
REDIS_ENDPOINT_URL="redis.us-east-1-3.ec2.cloud.redislabs.com:18007"
REDIS_PASSWORD=""

      return `${process.env.PUBLIC_URL}/avatars/0.jpg`;
const endpoint = process.env.REDIS_ENDPOINT_URL || "127.0.0.1:6379";
const password = process.env.REDIS_PASSWORD || null;

```

## GitHub

```java
git init
git add .
git remote remove origin
git commit -m "first commit"
git branch -M main
git remote add origin git@github.com:coding-to-music/redis-chat-node-socketio.git
git push -u origin main
```

In this tutorial, you will learn how to deploy a Node.js based Redis chat application using Vercel in just 5 minutes.

Getting Started with Vercel and Redis

https://developer.redis.com/create/vercel/

https://github.com/redis-developer/redis-developer.github.io/edit/master/docs/create/vercel/index-vercel.mdx

id: index-vercel
title: Getting Started with Vercel and Redis
sidebar_label: Getting Started with Vercel and Redis
slug: /create/vercel
authors: [ajeet]

import RedisCard from '@site/src/theme/RedisCard';

[Vercel ](https://vercel.com/)is a popular static web hosting serverless platform for frontend developers. The platform allows developers to host websites and web services, deploy instantly, and scale automatically with minimal configuration.

Vercel is the preferred platform to host [Next.js-based web applications](https://vercel.com/docs/concepts/next.js/overview). It allows you to deploy serverless functions that take an HTTP request and provide a response. You can use [serverless functions](https://vercel.com/docs/concepts/functions/serverless-functions) to handle user authentication, form submission, database queries, custom Slack commands, and more.

Vercel integrates well with popular tools, such as [GitHub](https://vercel.com/docs/concepts/git/vercel-for-github), [GitLab](https://vercel.com/docs/concepts/git/vercel-for-gitlab), [Lighthouse](https://vercel.com/integrations/lighthouse), [Doppler](https://vercel.com/integrations/doppler), and [Divjoy](https://divjoy.com/). NodeJS, Go, Python, and Ruby are the leading [official runtimes supported by Vercel](https://vercel.com/docs/runtimes).

![vercel](images/vercel_redis.png)

### Features of Vercel

- Vercel is focused on the build and deployment aspects of the [JAMstack approach](https://jamstack.org/what-is-jamstack/).
- [The Vercel API](https://vercel.com/docs/rest-api) provides full control over the Vercel platform, exposed as simple HTTP service endpoints over SSL.
- All endpoints live under the URL [https://api.vercel.com](https://api.vercel.com) and follow the REST architecture.
- Vercel provides custom domains to deploy your code on the live server (vercel.app as the suffix in the domain).
- Vercel provides you with an option to choose any framework of the repository you wish to deploy either Node.js, React, Gatsby, or [Next.js](https://nextjs.org/) (a full-stack React serverless framework that integrates seamlessly with Vercel).
- Vercel integrates with a GitHub repository for automatic deployments upon commits.

In this tutorial, you will learn how to deploy a Node.js based Redis chat application using Vercel in just 5 minutes.

### Table of Contents

- Step 1. Set up a free Redis Enterprise Cloud account
- Step 2. Install Vercel CLI
- Step 3. Log in to your Vercel Account
- Step 4. Clone your GitHub repository
- Step 5. Create a vercel.json file
- Step 6. Set up environment variables
- Step 7. Deploy the Node.js app
- Step 8. Access your app

### Step 1. Set up a free Redis Enterprise Cloud account

Visit [developer.redis.com/create/rediscloud/](https://developer.redis.com/create/rediscloud/) and create [a free Redis Enterprise Cloud account](https://redis.com/try-free/). Once you complete this tutorial, you will be provided with the database endpoint URL and password. Save it for future reference.

:::info TIP
For a limited time, use **TIGER200** to get **$200** credits on Redis Enterprise Cloud and try all the advanced capabilities!

:tada: [Click here to sign up](https://redis.com/try-free)

:::

![alt_text](images/details_database.png)

### Step 2. Install Vercel CLI

```
npm i -g vercel

vercel -v
Vercel CLI 23.1.2
23.1.2

```

### Step 3. Log in to your Vercel account

The `vercel login` command allows you to log in to your Vercel account through Vercel CLI.

```
vercel login
Vercel CLI 23.1.2
> Log in to Vercel github
> Success! GitHub authentication complete for xx@xx.com
Congratulations! You are now logged in. In order to deploy something, run `vercel`.
💡  Connect your Git Repositories to deploy every branch push automatically (https://vercel.link/git).
```

Once Vercel gets connected to your GitHub account, it displays your public repositories. Let us clone [https://github.com/redis-developer/basic-redis-chat-app-demo-nodejs](https://github.com/redis-developer/basic-redis-chat-app-demo-nodejs) to the local repository.

### Step 4. Clone the GitHub repository

The complete source code of the Redis Chat application is hosted [here](https://github.com/redis-developer/basic-redis-chat-app-demo-nodejs). React and Socket.IO are used for building the frontend while Node.js and Redis power the backend. Redis is used mainly as a database to keep the user/messages data and for sending messages between connected servers.

```
git clone https://github.com/redis-developer/basic-redis-chat-app-demo-nodejs
```

### Step 5. Create a vercel.json for Node.js app

If you run the `vercel init` command, it will list various frameworks but you won’t be able to find Node.js, hence you will need to create a `vercel.json` file as shown below:

```
{
  "version": 2,
  "builds": [
    {
      "src": "./index.vercel.js",
      "use": "@vercel/node"
    }
  ],
  "routes": [
    {
      "src": "/(.*)",
      "dest": "/"
    }
  ]
}

```

### Step 6. Set up environment variables

The `vercel env` command is used to manage [environment variables](https://vercel.com/docs/concepts/projects/environment-variables) under a Project, providing functionality to list, add, remove, and pull.

Let us first set up environment variables.

```
 vercel env add
Vercel CLI 23.1.2
? What's the name of the variable? REDIS_ENDPOINT_URI
? What's the value of REDIS_ENDPOINT_URI? redis-XXXX.c110-qa.us-east-1-1-1.ec2.qa-cloud.redislabs.com:XXX

```

Listing the environment variables:

```
vercel env ls
Vercel CLI 23.1.2
> Environment Variables found in Project basic-redis-chat-app-demo-nodejs [684ms]

 name                       value               environments                        created
 REDIS_PASSWORD             Encrypted           Production, Preview, Development    2d ago
 REDIS_ENDPOINT_URL         Encrypted           Production, Preview, Development    2d ago

```

### Step 7. Deploy the Node.js app

When you run a vercel command in a directory for the first time, [Vercel CLI](https://vercel.com/cli) needs to know which [scope](https://vercel.com/docs/cli#options/global-options/scope) and [Project](https://vercel.com/docs/concepts/projects/overview) you want to deploy your directory to. You can choose to either link an existing project or create a new one.

```
vercel
Vercel CLI 23.1.2
? Set up and deploy "~/projects/10feb/basic-redis-chat-app-demo-nodejs"? [Y/n] y
? Which scope do you want to deploy to? redis-developer
? Found project "redis-developer/basic-redis-chat-app-demo-nodejs". Link to it? [Y/n] y
🔗  Linked to redis-developer/basic-redis-chat-app-demo-nodejs (created .vercel)
🔍  Inspect: https://vercel.com/redis-developer/basic-redis-chat-app-demo-nodejs/5KZydRNsXwnjRxDYa65x4Ak8KwZT [4s]
✅  Preview: https://basic-redis-chat-app-demo-nodejs-redis-developer.vercel.app [copied to clipboard] [27s]
📝  To deploy to production (basic-redis-chat-app-demo-nodejs.vercel.app), run `vercel --prod`
❗️  Due to `builds` existing in your configuration file, the Build and Development Settings defined in your Project Settings will not apply. Learn More: https://vercel.link/unused-build-settings

```

Once the deployment process has completed, a new `.vercel` directory will be added to your directory. The `.vercel` directory contains both the organization and project ID of your project.

The "project.json" file contains:

- The ID of the Vercel project that you linked ("projectId")

- The ID of the user or team your Vercel project is owned by ("orgId")

:::note
Vercel CLI automatically detects the framework you are using and offers default project settings accordingly.
:::

### Step 8. Accessing the app

Run the following command to deploy the Redis chat app to the Prod environment.

```
vercel --prod
Vercel CLI 23.1.2
🔍  Inspect: https://vercel.com/redis-developer/basic-redis-chat-app-demo-nodejs/GoRdy7LKxqhBfJNW8hSvvFLQC6EN [2s]
✅  Production: https://basic-redis-chat-app-demo-nodejs.vercel.app [copied to clipboard] [14s]


```

By now, you will be able to login to Chat app and start chatting.

![alt_text](images/vercel13.png)

The chat server works as a basic REST API which involves keeping the session and handling the user state in the chat rooms (besides the WebSocket/real-time part). When a WebSocket/real-time server is instantiated, which listens for the next events:

![alt_text](images/vercel3.png)

If you want to know how the chat app works internally, [refer to this detailed blog tutorial](/howtos/chatapp#how-it-works)

### References

- [Getting Started with Vercel](https://vercel.com/docs/get-started)
- [Serverless Functions under Vercel](https://vercel.com/docs/concepts/functions/serverless-functions)
- [A Look at Vercel Supported Languages](https://vercel.com/docs/concepts/functions/supported-languages)
- [Next.js on Vercel](https://vercel.com/docs/concepts/next.js/overview)

# Basic Redis Chat App Demo (Node.js)

Showcases how to impliment chat app in Node.js, Socket.IO and Redis. This example uses **pub/sub** feature combined with web-sockets for implementing the message communication between client and server.

<a href="https://github.com/redis-developer/basic-redis-chat-app-demo-nodejs/raw/main/docs/screenshot000.png"><img src="https://github.com/redis-developer/basic-redis-chat-app-demo-nodejs/raw/main/docs/screenshot000.png" width="49%"></a>
<a href="https://github.com/redis-developer/basic-redis-chat-app-demo-nodejs/raw/main/docs/screenshot001.png"><img src="https://github.com/redis-developer/basic-redis-chat-app-demo-nodejs/raw/main/docs/screenshot001.png" width="49%"></a>

# Overview video

Here's a short video that explains the project and how it uses Redis:

[![Watch the video on YouTube](https://github.com/redis-developer/basic-redis-chat-app-demo-nodejs/raw/main/README.md)](https://www.youtube.com/watch?v=miK7xDkDXF0)

## Technical Stacks

- Frontend - _React_, _Socket_ (Socket.IO)
- Backend - _Node.js_, _Redis_

## How it works?

### Initialization

For simplicity, a key with **total_users** value is checked: if it does not exist, we fill the Redis database with initial data.
`EXISTS total_users` (checks if the key exists)

The demo data initialization is handled in multiple steps:

**Creating of demo users:**
We create a new user id: `INCR total_users`. Then we set a user ID lookup key by user name: **_e.g._** `SET username:nick user:1`. And finally, the rest of the data is written to the hash set: **_e.g._** `HSET user:1 username "nick" password "bcrypt_hashed_password"`.

Additionally, each user is added to the default "General" room. For handling rooms for each user, we have a set that holds the room ids. Here's an example command of how to add the room: **_e.g._** `SADD user:1:rooms "0"`.

**Populate private messages between users.**
At first, private rooms are created: if a private room needs to be established, for each user a room id: `room:1:2` is generated, where numbers correspond to the user ids in ascending order.

**_E.g._** Create a private room between 2 users: `SADD user:1:rooms 1:2` and `SADD user:2:rooms 1:2`.

Then we add messages to this room by writing to a sorted set:

**_E.g._** `ZADD room:1:2 1615480369 "{'from': 1, 'date': 1615480369, 'message': 'Hello', 'roomId': '1:2'}"`.

We use a stringified _JSON_ for keeping the message structure and simplify the implementation details for this demo-app.

**Populate the "General" room with messages.** Messages are added to the sorted set with id of the "General" room: `room:0`

### Registration

![How it works](docs/screenshot000.png)

Redis is used mainly as a database to keep the user/messages data and for sending messages between connected servers.

#### How the data is stored:

- The chat data is stored in various keys and various data types.
  - User data is stored in a hash set where each user entry contains the next values:
    - `username`: unique user name;
    - `password`: hashed password

* User hash set is accessed by key `user:{userId}`. The data for it stored with `HSET key field data`. User id is calculated by incrementing the `total_users`.

  - E.g `INCR total_users`

* Username is stored as a separate key (`username:{username}`) which returns the userId for quicker access.
  - E.g `SET username:Alex 4`

#### How the data is accessed:

- **Get User** `HGETALL user:{id}`

  - E.g `HGETALL user:2`, where we get data for the user with id: 2.

- **Online users:** will return ids of users which are online
  - E.g `SMEMBERS online_users`

#### Code Example: Prepare User Data in Redis HashSet

```JavaScript
const usernameKey = makeUsernameKey(username);
/** Create user */
const hashedPassword = await bcrypt.hash(password, 10);
const nextId = await incr("total_users");
const userKey = `user:${nextId}`;
await set(usernameKey, userKey);
await hmset(userKey, ["username", username, "password", hashedPassword]);

/**
* Each user has a set of rooms he is in
* let's define the default ones
*/
await sadd(`user:${nextId}:rooms`, `${0}`); // Main room
```

### Rooms

![How it works](docs/screenshot001.png)

#### How the data is stored:

Each user has a set of rooms associated with them.

**Rooms** are sorted sets which contains messages where score is the timestamp for each message. Each room has a name associated with it.

- Rooms which user belongs too are stored at `user:{userId}:rooms` as a set of room ids.

  - E.g `SADD user:Alex:rooms 1`

- Set room name: `SET room:{roomId}:name {name}`
  - E.g `SET room:1:name General`

#### How the data is accessed:

- **Get room name** `GET room:{roomId}:name`.

  - E. g `GET room:0:name`. This should return "General"

- **Get room ids of a user:** `SMEMBERS user:{id}:rooms`.
  - E. g `SMEMBERS user:2:rooms`. This will return IDs of rooms for user with ID: 2

#### Code Example: Get all My Rooms

```JavaScript
const rooms = [];
for (let x = 0; x < roomIds.length; x++) {
    const roomId = roomIds[x];

    let name = await get(`room:${roomId}:name`);
    /** It's a room without a name, likey the one with private messages */
    if (!name) {
        /**
         * Make sure we don't add private rooms with empty messages
         * It's okay to add custom (named rooms)
         */
        const roomExists = await exists(`room:${roomId}`);
        if (!roomExists) {
            continue;
        }

        const userIds = roomId.split(":");
        if (userIds.length !== 2) {
            return res.sendStatus(400);
        }
        rooms.push({
            id: roomId,
            names: [
                await hmget(`user:${userIds[0]}`, "username"),
                await hmget(`user:${userIds[1]}`, "username"),
            ],
        });
    } else {
        rooms.push({
            id: roomId,
            names: [name]
        });
    }
}
return rooms;
```

### Messages

#### Pub/sub

After initialization, a pub/sub subscription is created: `SUBSCRIBE MESSAGES`. At the same time, each server instance will run a listener on a message on this channel to receive real-time updates.

Again, for simplicity, each message is serialized to **_JSON_**, which we parse and then handle in the same manner, as WebSocket messages.

Pub/sub allows connecting multiple servers written in different platforms without taking into consideration the implementation detail of each server.

#### How the data is stored:

- Messages are stored at `room:{roomId}` key in a sorted set (as mentioned above). They are added with `ZADD room:{roomId} {timestamp} {message}` command. Message is serialized to an app-specific JSON string.
  - E.g `ZADD room:0 1617197047 { "From": "2", "Date": 1617197047, "Message": "Hello", "RoomId": "1:2" }`

#### How the data is accessed:

- **Get list of messages** `ZREVRANGE room:{roomId} {offset_start} {offset_end}`.
  - E.g `ZREVRANGE room:1:2 0 50` will return 50 messages with 0 offsets for the private room between users with IDs 1 and 2.

#### Code Example: Send Message

```Javascript
async (message) => {
    /** Make sure nothing illegal is sent here. */
    message = {
        ...message,
        message: sanitise(message.message)
    };
    /**
     * The user might be set as offline if he tried to access the chat from another tab, pinging by message
     * resets the user online status
     */
    await sadd("online_users", message.from);
    /** We've got a new message. Store it in db, then send back to the room. */
    const messageString = JSON.stringify(message);
    const roomKey = `room:${message.roomId}`;
    /**
     * It may be possible that the room is private and new, so it won't be shown on the other
     * user's screen, check if the roomKey exist. If not then broadcast message that the room is appeared
     */
    const isPrivate = !(await exists(`${roomKey}:name`));
    const roomHasMessages = await exists(roomKey);
    if (isPrivate && !roomHasMessages) {
        const ids = message.roomId.split(":");
        const msg = {
            id: message.roomId,
            names: [
                await hmget(`user:${ids[0]}`, "username"),
                await hmget(`user:${ids[1]}`, "username"),
            ],
        };
        publish("show.room", msg);
        socket.broadcast.emit(`show.room`, msg);
    }
    await zadd(roomKey, "" + message.date, messageString);
    publish("message", message);
    io.to(roomKey).emit("message", message);
}
```

### Session handling

The chat server works as a basic _REST_ API which involves keeping the session and handling the user state in the chat rooms (besides the WebSocket/real-time part).

When a WebSocket/real-time server is instantiated, which listens for the next events:

**Connection**. A new user is connected. At this point, a user ID is captured and saved to the session (which is cached in Redis). Note, that session caching is language/library-specific and it's used here purely for persistence and maintaining the state between server reloads.

A global set with `online_users` key is used for keeping the online state for each user. So on a new connection, a user ID is written to that set:

**E.g.** `SADD online_users 1` (We add user with id 1 to the set **online_users**).

After that, a message is broadcasted to the clients to notify them that a new user is joined the chat.

**Disconnect**. It works similarly to the connection event, except we need to remove the user for **online_users** set and notify the clients: `SREM online_users 1` (makes user with id 1 offline).

**Message**. A user sends a message, and it needs to be broadcasted to the other clients. The pub/sub allows us also to broadcast this message to all server instances which are connected to this Redis:

`PUBLISH message "{'serverId': 4132, 'type':'message', 'data': {'from': 1, 'date': 1615480369, 'message': 'Hello', 'roomId': '1:2'}}"`

Note we send additional data related to the type of the message and the server id. Server id is used to discard the messages by the server instance which sends them since it is connected to the same `MESSAGES` channel.

`type` field of the serialized JSON corresponds to the real-time method we use for real-time communication (connect/disconnect/message).

`data` is method-specific information. In the example above it's related to the new message.

#### How the data is stored / accessed:

The session data is stored in Redis by utilizing the [**connect-redis**](https://www.npmjs.com/package/connect-redis) client.

```JavaScript
const session = require("express-session");
let RedisStore = require("connect-redis")(session);
const sessionMiddleware = session({
  store: new RedisStore({ client: redisClient }),
  secret: "keyboard cat",
  saveUninitialized: true,
  resave: true,
});
```

## How to run it locally?

#### Write in environment variable or Dockerfile actual connection to Redis:

```
   REDIS_ENDPOINT_URL = "Redis server URI"
   REDIS_PASSWORD = "Password to the server"
```

#### Run frontend

```sh
cd client
yarn install
yarn start
```

#### Run backend

```sh
yarn install
yarn start
```

## Try it out

#### Deploy to Heroku

<p>
    <a href="https://heroku.com/deploy" target="_blank">
        <img src="https://www.herokucdn.com/deploy/button.svg" alt="Deploy to Heorku" />
    </a>
</p>

#### Deploy to Google Cloud

<p>
    <a href="https://deploy.cloud.run" target="_blank">
        <img src="https://deploy.cloud.run/button.svg" alt="Run on Google Cloud" width="150px"/>
    </a>
</p>
