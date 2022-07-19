# WebRTC
Acronym: Web Real time communication.
## Introduction 
WebRTC is a protocol used for chatting, streaming and video calling at scale.
It is developed by google.

It is used by 
- google hangout : https://webrtchacks.com/hangout-analysis-philipp-hancke/ 
- discord: https://discord.com/blog/how-discord-handles-two-and-half-million-concurrent-voice-users-using-webrtc  
- Google Stadia (google gaming console): https://webrtc.ventures/2021/02/webrtc-cloud-gaming-unboxing-stadia/ 
- YouTube Live streaming: https://youtu.be/htN-gIPOkP0 

## Advantages of WebRTC

- It is peer-to-peer in most of the cases. 
  - only in case of symmetric NAT (Network address translation), it is not peer to peer.
  In those cases, TURN (Turn around NAT) server is needed. Most of the traffic can be peer-to-peer though. 
- It is UDP in most of the cases. 
  - WebRTC defaults to UDP. just in case, the UDP is blocked, webRTC fallbacks to TCP.https://stackoverflow.com/questions/18897917/does-webrtc-use-tcp-or-udp 


## Disadvantage of WebRTC
- It works fine for 3 or max 4 participants in a meeting/ game. For more than this, the bandwidth and processing is more. 
- It is quite complex technology and requires more time to build compared to websockets. 

## Concepts of WebRTC
WebRTC has 4 major steps 
1. Signalling 
2. Connecting 
3. Securing
4. Communicating


### Signalling 
In this step, the Session description is there. An offer is created using Session Descriptor protocol.
The session descriptor protocol is a json with keys and values. The keys and value define the offer and what type of connection is needed to be created (is it video, is it text etc.).

### Connecting 
ICE candidates https://developer.mozilla.org/en-US/docs/Web/API/WebRTC_API/Connectivity#ice_candidates are generated to find the best method of communication between peers. The few of the options to connect between peers are
1. weather to connect in the same network vs different network.
2. weather TURN server is needed or not. 
3. weather to use UDP or TCP (with UDP being preferred and widely used)

This step uses STUN server which generates all the possible ways an outside world can connect to the peer.

### Securing 
It uses:
1. DTLS: Datagram transport layer security 
2. SRTP: Secure realtime transport protocol. 

### Communication 
#### Video Communication
**RTP**:  It contains the actual packet for transmission like not consuming bandwidth when there is a silence.  
**RTCP**: It contains the statistical information about transmission. 

#### Text communication 
**SCTP** Stream control transmission protocol. It is for non-video transmission. 
1. Real time network games
2. game player action events
3. asset exchange
4. text chat. 
It also maintains the congestion control. 


## Conclusion
WebRTC is a technology which uses a lot of existing technology under the hood. It provides a lot of features out of the box like congestion control, switching the protocol/network dynamically etc. 
Without WebRTC, one would have needed to build on own. 
WebRTC is very adaptive by network. One should always use WebRTC over web-sockets if they want to work on scale. 
In case of multiple participants webRTC has slight disadvantages, but those cases are solved using webRTC servers.
So, in case of multiple participants, event though the communication is not peer to peer, but other features like congestion control etc. are still there. 

## Good reads
1. Hussain Naseer video: https://www.youtube.com/watch?v=FExZvpVvYxA 
2. Hussain Naseer github:  https://github.com/hnasr/javascript_playground/tree/master/webrtc 
3. udemy : https://www.udemy.com/course/practical-webrtc-a-complete-webrtc-bootcamp-for-beginners/learn/lecture/2367824
4. webrtc official doc: https://webrtc.org 
