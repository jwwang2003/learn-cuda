# Nvidia CUDA

## Developing on WSL2

Previously, I had some problems when trying to run the `nsys` profiler in my WSL2 instance.
I assumed that CUDA was working but my profiler did not capture any CUDA events.

The following forum solved my problem:

[Nsys doesn’t show cuda kernel and memory data](https://forums.developer.nvidia.com/t/nsys-doesnt-show-cuda-kernel-and-memory-data/315536/9)

I first installed the latest version of [Nsight Systems](https://developer.nvidia.com/nsight-systems/get-started)

```
wget https://developer.nvidia.com/nsight-systems/get-started#:~:text=Download%20.run%20Installer-,Download%20.deb%20Installer,-Download%20.rpm%20Installer
sudo dpkg -i ...
```

Check where the config is located:

```bash
$ nsys -z
/home/wjw/.config/NVIDIA Corporation/nsys-config.ini
```

Create one if it doesn't exist:
```bash
mkdir -p "/home/wjw/.config/NVIDIA Corporation"
touch "/home/wjw/.config/NVIDIA Corporation/nsys-config.ini"
```

Add this line to the config file:
```bash
echo "CuptiUseRawGpuTimestamps=false" > "/home/wjw/.config/NVIDIA Corporation/nsys-config.ini"
```

`nsys` profiler should work normally now.

## Installation & learning resources

- [CUDA on WSL](https://docs.nvidia.com/cuda/wsl-user-guide/index.html#getting-started-with-cuda-on-wsl-2)
- [Getting started with CUDA CPP](https://developer.nvidia.com/how-to-cuda-c-cpp)
- https://developer.nvidia.com/blog/new-dli-online-courses-for-hands-on-training-in-accelerated-computing/
- [CUDA Samples](https://github.com/NVIDIA/cuda-samples/tree/master)
- [Nvidia Toolkit](https://developer.nvidia.com/cuda-toolkit)
- [Pytorch CUDA Extension Example](https://docs.pytorch.org/tutorials/advanced/cpp_extension.html)
- https://www.geeksforgeeks.org/machine-learning/how-to-set-up-and-run-cuda-operations-in-pytorch/

## First: Hello, world! \(Cuda version\)

- [An introduction to CUDA](https://developer.nvidia.com/blog/even-easier-introduction-cuda/)


