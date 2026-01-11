#### Prompt
Hi! I’m currently learning English as my second language by speaking and practicing the words here. My first language is Chinese, and I would say my English level is beginner.
My goal is to become fluent in English one day, and I’d like your help with that.
Please make follow paragraph more verbal and sense. Put the edited contents in code block so that I can directly copy it.

## 05/01/2026
origin contents
```
Hi, I'm Otto, a mobile developer and Computer Vision Engineer, I dedicated to deploy AI models in life which make our life become beauty. I am very happy here to have the chance sharing my work with you.

When I interviewed a Flutter developer on October last year, I was asked whether I had experiences on deploying deep learning models on mobile devices. They asked me to achieve realtime object detection on mobile devices, their project was tennis accompany training. They designed tracked tennis ball and recorded trajectories every frame. They desired only use mobile hardware and developed App to sell their product. They will develop wearable hand ring hardware in the future. They gave me a chance to try deploy model on mobile devices and required 60 FPS detection since it's a live process, they don't want just record and wait for process on recorded videos. At first, I researched on internet and social communities to see whether other people had did the same thing. There are many resources about YOLO model deploy on mobile devices. However, these articles didn't show how fast was the performance, they only provided the results on pictures. I had looked a lot of articles, they almost used ONNX framework to fulfill deploying on mobile because of the allowance package size in App Store. So my first try was used ONNX framework. The work was actually smooth, which I just converted the Pytorch parameters to ONNX format. The model can work correctly on mobile devices, but the performance was really poor, even I transfer my Dart code to C++ and customized building OpenCV library for mobile devices and tried quantizing model or opened GPU for inference. The performance still can't be raise, always stuck 3-5 FPS. I reported the bad result to interviewers, they were very disappointed with me and without any patience with me. I was ignored in their communication group, they didn't reply me anymore. As the result, I didn't trust Microsoft's solution anymore, I directly see Ultralytics's project and repository, I found they only used native Apple SDK for deploying model on iPhones. But they just wrote in Swift, I thought that I used C++ shouldn't slower than them used Swift, and I have an excellent library OpenCV which can cover preprocess and postprocess during inference. Just when I annoyed how could I used CoreML to load model in Flutter, I suddenly came up with I can mixed compile Objective-C and C++, which I had relative experiences and it is workable on iOS. Have the idea, I immediately go ahead to implement it. While I switched framework from ONNX to CoreML the cost of inference from 120ms to 20ms, it was obvious improvement! However, there was still a stuck on camera stream when we displayed and detected object in every single frame, which only can approach 50 FPS. I already knew that the issue was I just used a single thread, I had to used two threads to isolate capture and detection process. In additionally, the requirement don't need the detection results have very closed movements between frame sequence. On the other hand, I can add another thread to execute tracker as a compensation to get more resolution when the detection failed or loss in certain frame. In order to avoid detection block capture and ensure the frames didn't loss, I used lock-free queue to cache every frame. The main thread just push captured frame into queue, the detection thread pop it to do detect objects then return the bounding boxes result to main thread that rendered them on screen. So the detection thread never block main thread of App, the App finally approach 60 FPS in realtime object detection on mobile devices.
```
#### GPT modified
Hi, I’m Otto, a mobile developer and computer vision engineer. Recently, I’ve been working on edge computing and on-device AI. In this video, I’m excited to share my work with you.

Last October, when I interviewed for a Flutter developer position, I was asked whether I had experience deploying deep learning models on mobile devices.

The team was working on a tennis training application. Their goal was to track a tennis ball in real time, record its trajectory frame by frame, and run everything purely on mobile hardware. This was a hard requirement because they wanted to sell the app as a standalone product, without relying on cloud inference. They also planned to integrate wearable hardware in the future.

They gave me a technical challenge: deploy a YOLO-based object detection model on mobile and achieve real-time performance — specifically around 60 FPS — because the app needed to process live camera streams, not recorded videos.

I started by researching existing solutions online and in developer communities. There were many articles about deploying YOLO on mobile, and most of them used ONNX because it helps reduce app size and is commonly accepted in app stores. However, most of these resources only showed detection results on images and didn’t provide any concrete performance benchmarks.

Based on this research, my first implementation used ONNX. Technically, the deployment itself was smooth — I converted the PyTorch model to ONNX, and the model ran correctly on mobile devices. However, performance quickly became the biggest issue. Even after rewriting the Dart logic in C++, building a custom OpenCV pipeline, enabling GPU inference, and experimenting with FP16 and INT8 quantization to reduce inference latency, the performance was still stuck at around 3 to 5 FPS.

At that point, I reported the results honestly to the interviewers. They were disappointed, and communication gradually stopped. That was frustrating, but I didn’t want to stop there. I felt that the problem wasn’t impossible — I just hadn’t found the right approach yet.

Instead of giving up, I went back to the source and studied Ultralytics’ official implementation more closely. I noticed that on iOS, they didn’t use ONNX at all — they relied entirely on Apple’s native CoreML framework. Their implementation was written in Swift, and that made me rethink my assumptions. I realized that using a cross-platform framework wasn’t necessarily the best choice for maximum performance on iOS.

The challenge then became: how can I use CoreML in a Flutter app?

That’s when I remembered that iOS allows mixed compilation of Objective-C and C++. Since I already had experience with Objective-C++, I decided to bridge Flutter to CoreML using native iOS code, while keeping my preprocessing and postprocessing logic in C++ with OpenCV.

After switching from ONNX to CoreML, the inference time dropped dramatically — from around 120 milliseconds per frame to about 20 milliseconds. This was a huge breakthrough.

However, I still noticed frame drops when running detection on every camera frame. The app could only reach around 50 FPS. By profiling the system, I identified the root cause: everything was running on a single thread, so detection was blocking camera capture and rendering.

To solve this, I redesigned the pipeline using multiple threads. I separated camera capture and model inference, and introduced a lock-free queue to buffer frames. The main thread only pushed captured frames into the queue, while a dedicated detection thread popped frames, ran inference, and sent the bounding box results back to the UI thread for rendering.

Because the product didn’t require perfectly continuous detection results between every frame, I further optimized the system by allowing the detector to skip frames when needed and using a lightweight tracker as a fallback to maintain smooth motion.

With this architecture, detection never blocked the main thread, no frames were lost, and the system finally reached stable 60 FPS real-time object detection on mobile devices.

This project taught me an important lesson: when performance becomes a bottleneck, it’s critical to question initial assumptions, understand platform-specific strengths, and be willing to redesign the architecture rather than forcing an existing solution to work. Most importantly, I learned not to give up just because the first approach failed.
