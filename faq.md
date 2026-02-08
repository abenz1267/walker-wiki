# FAQ

## Why is my Walker opening so slow?

Walker is a GTK4 Application with a lot of customizability. Every time you open it, there's a lot of upfront processing that has to happen. To mitigate this, you can run a background service. Read the according section.

To debug: run `walker` in a terminal and check it's output.

### Service is running and Walker is still slow to open

If you have an Nvidia GPU, try setting `GSK_RENDERER=cairo` environment variable. GTK4 uses Vulkan by default, which might cause issues with Nvidia.

### My videos don't have a thumbnail

Walker will auto-play video files. Make sure you have these installed:

```
  gst-libav \
  gst-plugins-bad \
  gst-plugins-base \
  gst-plugins-good \
  gst-plugins-ugly \
```

### NO NVIDIA. SERVICE IS UP.

I have no idea. Open an issue with as much information as possible.
