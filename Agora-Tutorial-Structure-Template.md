# Agora Tutorial Structure Template

> The title describes a task that you want to do. For example: **Build a Video Calling App with Agora**.
> For docs published on dev portal, the doc title is configured in the internal cms.
> To write a page, use the style and tone suggested in the style guide.

# Title

> Explain why the content is relevant and what the user will achieve.
> Use "page" at the top of a document and "section" wherever else.
> For example:

Real-time video calling enhances user engagement and provides an immersive communication experience in your applications. With Agora's Video SDK, you can easily implement high-quality, low-latency video calls that work reliably even in challenging network conditions.

This page shows you how to add video calling functionality to your application using the Agora Video SDK.

## Understand the tech

> A helicopter view that explains the architecture and workflow that the user is implementing.
>
> For example:

To implement video calling with Agora, you use the Agora RTC (Real-Time Communication) SDK that works in the following way:

1. Your app initializes the Agora client
2. Users join a channel (video call room) with unique identifiers
3. The SDK handles publishing and subscribing to audio/video streams
4. The SDK manages all the complexities of real-time communication including network traversal, packet loss recovery, and dynamic bitrate adaptation

> Add an architecture diagram, workflow diagram, animation, screenshot here.
>
> For example:

The following figure shows the data flow between the client application and Agora's real-time communication network:
![Agora Video Call Architecture](./images/agora_video_flow.png 'Agora Video Call Architecture')

> Add a concise but complete explanation of the task. Where needed, link to a trusted source.

## Prerequisites

> List what the reader needs to know, as well as packages or SDKS that must be available, to successfully work through the tutorial. Keep the list short, but be sure to include language and concepts the reader should be familiar with.
>
> **IMPORTANT**: The first prerequisite will always include a link to the _"Get Started with Agora"_ tutorial using URL: https://docs.agora.io/en/Agora%20Platform/get_appid_token?platform=All%20Platforms.
>
> For example:

To successfully implement video calling with Agora, you must have the following:

- A valid [Agora account](https://docs.agora.io/en/Agora%20Platform/sign_in_and_sign_up). If you don't have an account, see how to [Get started with Agora](https://docs.agora.io/en/Agora%20Platform/get_appid_token?platform=All%20Platforms).
  > The URL to the setup the Agora account is made up of _URL_:_PAGE_TITLE_.
  > For a blog named _How to Build a Video Calling App with Agora_ the link is: https://www.agora.io/en/blog/how-to-get-started-with-agora?utm_source=medium&utm_medium=blog&utm_campaign=How_to_Build_a_Video_Calling_App_with_Agora
  >
  > It's imperative that you type this URL correctly as it will be the primary way Agora can properly track developer conversion from individual content posts.
- An Agora project with the [app certificate](https://docs.agora.io/en/Agora%20Platform/manage_projects?platform=All%20Platforms#manage-your-app-certificates) enabled if you want to use token-based authentication.
- Basic knowledge of [JavaScript/HTML/CSS](https://developer.mozilla.org/en-US/docs/Web) for this web-based example.

## Project setup

> Describe the steps to create a new project and set up the environment. For example,
>
> - Create a xxx project
> - Necessary configurations
> - Create the UI
>
> **IF NONE ARE NEEDED, REMOVE THIS SECTION**
>
> For example:

To create the environment necessary to **TITLE OF THIS PAGE**:

1. Do this.
1. Do that.
1. Do something else.

> Markup commands to run in the terminal as `code`.
>
> If you need a specific file structure, do it as a text diagram:
> For example:
>
> <environment_root> \
> ├── index.html \
> ├── scripts \
> │ └── script.js \
> └── styles \
> │ └── style.css

## Build \<A rewording of the page title>

> The title for the steps does not have to be "Build".
> Note: When showing code, break down your implementation into incremental steps, showing smaller code blocks that build upon each other
> rather than pasting a single large block of code. This approach makes it easier for readers to follow along.
>
> Always include descriptive comments in your code examples. Comments should be:
>
> - Single line for general explanations
> - Function header comments when appropriate (these can be multi-line if the language convention requires it)

> If there are multiple logical sections in the procedure such as back-end and frond-end, use subsections. The goal is to modularize the various elements and build the project in a logical way that makes it easy for the user to follow along.
>
> Write an intro sentence to explain the subsections:
>
> For example:

Implementing video calling with Agora involves setting up the client and creating the user interface. This section shows you how to:

- [Initialize the Agora client and join a channel](link to module1)
- [Enhance the video experience with quality optimization](link to module2)

> If there are no logical subsections, write a single procedure here.

### Build \<module1 in procedure>

> A module explains how to implement a set of functions that operate together to produce a specific feature of the project.
> Be sure to explain all inputs and outputs (not necessarily a complete API reference), discuss their significance within the code and how they work together.
>
> Show code in incremental steps. First show a simple implementation, explain it, then build upon it with more features.
>
> For example:

To implement a basic video call in your web application using the Agora SDK:

1. First, initialize the Agora client:

```javascript
// Create an instance of the Agora Engine
const client = AgoraRTC.createClient({ mode: 'rtc', codec: 'vp8' });

// Initialize the Agora client with your App ID
async function initializeAgoraClient() {
  // Replace with your Agora App ID
  const appId = 'your-app-id';

  // Set up event listeners for remote users joining
  client.on('user-published', async (user, mediaType) => {
    // Subscribe to the remote user when they publish
    await client.subscribe(user, mediaType);
    console.log('Successfully subscribed to remote user');

    // Handle video streams when the user publishes a video track
    if (mediaType === 'video') {
      // Get the RemoteVideoTrack from the user object
      const remoteTrack = user.videoTrack;
      // Play the remote video track in the container
      remoteTrack.play('remote-stream-' + user.uid);
    }
  });

  // Initialize the client with your Agora App ID
  await client.init(appId);
}
```

2. Next, implement the function to join a video call channel:

```javascript
// Create an instance of the Agora Engine
const client = AgoraRTC.createClient({ mode: 'rtc', codec: 'vp8' });

// Initialize the Agora client with your App ID
async function initializeAgoraClient() {
  // Replace with your Agora App ID
  const appId = 'your-app-id';

  // Set up event listeners for remote users joining
  client.on('user-published', async (user, mediaType) => {
    // Subscribe to the remote user when they publish
    await client.subscribe(user, mediaType);
    console.log('Successfully subscribed to remote user');

    // Handle video streams when the user publishes a video track
    if (mediaType === 'video') {
      // Get the RemoteVideoTrack from the user object
      const remoteTrack = user.videoTrack;
      // Play the remote video track in the container
      remoteTrack.play('remote-stream-' + user.uid);
    }
  });

  // Initialize the client with your Agora App ID
  await client.init(appId);
}

// Join a channel and create local tracks
async function joinChannel() {
  try {
    // Get a token from your token server if you have enabled token authentication
    const token = null; // Set to null if token is not required

    // Join the channel with a unique user ID
    const uid = await client.join(appId, 'test-channel', token, null);
    console.log('User ' + uid + ' joined channel successfully');

    // Create and publish local audio and video tracks
    const localAudioTrack = await AgoraRTC.createMicrophoneAudioTrack();
    const localVideoTrack = await AgoraRTC.createCameraVideoTrack();

    // Play the local video track in a container
    localVideoTrack.play('local-stream');

    // Publish the local tracks to the channel
    await client.publish([localAudioTrack, localVideoTrack]);
    console.log('Published local tracks successfully');
  } catch (error) {
    console.error('Error joining channel:', error);
  }
}
```

3. Finally, implement the function to leave the channel:

```javascript
// Function to leave the channel and release resources
async function leaveChannel() {
  // Destroy the local audio and video tracks
  localAudioTrack.close();
  localVideoTrack.close();

  // Leave the channel
  await client.leave();
  console.log('User left channel successfully');
}

// Add UI button event handlers
document.getElementById('join-btn').addEventListener('click', async () => {
  // Disable the join button after clicking
  document.getElementById('join-btn').disabled = true;
  // Enable the leave button
  document.getElementById('leave-btn').disabled = false;
  // Call the joinChannel function
  await joinChannel();
});

document.getElementById('leave-btn').addEventListener('click', async () => {
  // Disable the leave button
  document.getElementById('leave-btn').disabled = true;
  // Enable the join button
  document.getElementById('join-btn').disabled = false;
  // Call the leaveChannel function
  await leaveChannel();
});
```

### Build \<module2 in procedure>

> Brief explanation about what the technology does in this section, then a procedure.
> Remember to show incremental code changes with clear comments.
>
> For example:

To implement real-time video quality adjustment based on network conditions:

1. First, implement a function to monitor network quality:

```javascript
/**
 * Sets up event listeners to monitor network quality
 * and adjusts video quality accordingly
 */
function setupNetworkQualityMonitoring() {
  // Add an event listener for network quality changes
  client.on('network-quality', (stats) => {
    // stats.downlinkNetworkQuality: The uplink network quality
    // stats.uplinkNetworkQuality: The downlink network quality
    // 0: Unknown, 1: Excellent, 2: Good, 3: Poor, 4: Bad, 5: Very Bad, 6: Down

    // Log the current network quality
    console.log('Downlink network quality:', stats.downlinkNetworkQuality);
    console.log('Uplink network quality:', stats.uplinkNetworkQuality);

    // Call function to adjust video quality based on network conditions
    adjustVideoQuality(stats.uplinkNetworkQuality);
  });
}
```

2. Next, implement the function to adjust video quality:

```javascript
/**
 * Sets up event listeners to monitor network quality
 * and adjusts video quality accordingly
 */
function setupNetworkQualityMonitoring() {
  // Add an event listener for network quality changes
  client.on('network-quality', (stats) => {
    // stats.downlinkNetworkQuality: The uplink network quality
    // stats.uplinkNetworkQuality: The downlink network quality
    // 0: Unknown, 1: Excellent, 2: Good, 3: Poor, 4: Bad, 5: Very Bad, 6: Down

    // Log the current network quality
    console.log('Downlink network quality:', stats.downlinkNetworkQuality);
    console.log('Uplink network quality:', stats.uplinkNetworkQuality);

    // Call function to adjust video quality based on network conditions
    adjustVideoQuality(stats.uplinkNetworkQuality);
  });
}

/**
 * Adjusts video encoding parameters based on network quality
 * @param {number} networkQuality The current uplink network quality value
 */
async function adjustVideoQuality(networkQuality) {
  // Only proceed if we have a valid local video track
  if (!localVideoTrack) return;

  // Define video encoding presets for different network conditions
  const encodingPresets = {
    high: {
      // For excellent network (1)
      width: 1280,
      height: 720,
      frameRate: 30,
      bitrateMin: 600,
      bitrateMax: 1000,
    },
    medium: {
      // For good network (2)
      width: 640,
      height: 480,
      frameRate: 15,
      bitrateMin: 400,
      bitrateMax: 600,
    },
    low: {
      // For poor network (3+)
      width: 320,
      height: 240,
      frameRate: 15,
      bitrateMin: 200,
      bitrateMax: 400,
    },
  };

  // Select the appropriate encoding preset based on network quality
  let selectedPreset;
  if (networkQuality <= 1) {
    selectedPreset = encodingPresets.high;
  } else if (networkQuality === 2) {
    selectedPreset = encodingPresets.medium;
  } else {
    selectedPreset = encodingPresets.low;
  }

  // Set the encoding parameters
  await localVideoTrack.setEncoderConfiguration(selectedPreset);
  console.log('Video quality adjusted to:', selectedPreset);
}
```

## Test \<A rewording of the page title>

To ensure that you have implemented video calling correctly:

1. Open the application in two different browser tabs or devices.
2. Enter the same channel name in both instances:
   1. Click the "Join" button on both tabs/devices.
   2. Verify that you can see and hear the remote user in each instance.
3. Test the following functionality:
   1. Muting and unmuting audio
   2. Turning video on and off
   3. Leaving and rejoining the channel

## Next Steps

> Avoid using "Conclusion" as the header. Instead, use "Next Steps" or another action-oriented title.
> Write a short paragraph summarizing what the reader has learned and what they can accomplish with this knowledge.
> Include a link to the complete source code on GitHub (all finished project code must be publicly available).
> Limit external links to 1-2 high-value resources (such as Agora documentation or GitHub repositories).

You've successfully implemented a basic video calling application with Agora's Video SDK! You now have a solid foundation for building more advanced real-time communication features into your applications. The complete source code for this tutorial is available on [GitHub](https://github.com/agoraio-community/agora-video-tutorial).

Your next steps after implementing this functionality:

- Explore [Advanced Video Features](https://docs.agora.io/en/video-calling/develop/product-workflow) to enhance your application with features like screen sharing and virtual backgrounds
- Join the [Agora.io Developer Slack community](https://www.agora.io/en/join-slack/) to connect with other developers

## Special Considerations for Larger Projects

> This section is only relevant for larger tutorials with significant UI components or features beyond Agora's scope.
> Choose one of the following approaches based on your tutorial needs. If your tutorial doesn't involve a large project, you can remove this section.

For this tutorial, which involves building a complex video application with many UI components beyond the scope of Agora, we have chosen the following approach:

**Option 1: Focus on Agora Integration**
We've provided a link to the [complete project on GitHub](https://github.com/yourusername/complete-project) and focused this tutorial on implementing the key Agora Video SDK features. This allows you to understand how Agora integrates with a larger application without getting distracted by non-essential implementation details.

**Option 2: Starter Template Approach**
We've created a [starter template project on GitHub](https://github.com/yourusername/starter-template) that you can clone. This template includes all the non-Agora features already implemented, with clear code comments indicating where Agora integrations should be added. Follow this tutorial to complete the implementation by adding the Agora video features to the template.

## Reference

> If there is reference information you want to share with the user, add it here. If not, remove this section.
>
> For example:

For more information about Agora's Video SDK, see the [Agora Video SDK documentation](https://docs.agora.io/en/Video/video_sdk_overview?platform=All%20Platforms).
Check out the full code for this tutorial on [GitHub](https://github.com/agoraio-community/agora-video-tutorial).
