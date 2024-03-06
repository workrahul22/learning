### Segmentation
    Dividing video file into smaller segments.

### Adaptive Bitrate Streaming
    It is the ability to adjust video quality in the middle of a stream as network conditions changes.
    It is possible because the origin server encodes videos segments at several different quality levels.

### RTMP (Real time messaging protocol)
1. It is a video streaming technology.
2. When it comes to streaming video over the internet, though since flash player is no longer supports and some browsers and mobile devices don't accept RTMP. its often only used for first mile delivery. Last mile delivery, usually require the help of another protocol such as HLS
3. It is based on TCP: Although HTTP is more secure and easier to scale up for larger audiences.
4. Many of the web browsers and devices no longer accepth RTMP so it's often used in combination with another streaming protocol to deliver the live video to the viewer.

How RTMP works
1. Video Capture
2. Encoding
3. Server Processing
4. Playback

Encoder can be hardware or software
Hardware encoder tend to be more reliable & expensive
RTMP streamKey + server URL : The server URL stays the same and the stream key changes with each new stream.


### RTP (Real time protocol)

### HLS (Http Live Streaming)
1. Oly support H.264 or H.265
2. Can be played every device.
3. Developed by apple

### MPEG-DASH

1. DASH stands for Dynamic Adoptive streaming over HTTP
2. It is similar to HLS
3. It uses HTTP, which is an advantage because most of the internet already uses HTTP. with HTTP the stream goes to a standard part (80 or 443) that is almost always open. This ensures that the stream is rarely blocked by a firewall.
4. Support any encoding standards
5. can not be played on apple device.
6. International Standards.

MPEG-DASH streaming process
1. Encoding & Segmentation
2. Delivery
3. Decoding & Playback
