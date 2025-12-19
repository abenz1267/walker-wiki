# FAQ

## Why is my Walker opening so slow?

Walker is a GTK4 Application with a lot of customizability. Every time you open it, there's a lot of upfront processing that has to happen. To mitigate this, you can run a background service. Read the according section.

To debug: run `walker` in a terminal and check it's output.

### Service is running and Walker is still slow to open

If you have an Nvidia GPU, try setting `GSK_RENDERER=cairo` environment variable. GTK4 uses Vulkan by default, which might cause issues with Nvidia.

### I am seeing 'Waiting for elephant...' or 'No Results'

Make sure elephant is running and that you have a provider installed. Both are detailed in the Installation and Launching section.

### NO NVIDIA. SERVICE IS UP.

I have no idea. Open an issue with as much information as possible.
