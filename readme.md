# A rust binding for yolov8 or higher aimed at detection

This create is a binding for yolov8 or higher.

Currently, it supports load module from a torchscript file.

it offers apis to load from a `file`, load from `dir` and load from `bytes`.

it offers apis to export to `DynamicImage` or a `dir`.

I try my best to make it easy, but obviously it can just deal with the basic function.

It uses the yolo-metadata information and detect `0x504b0708` as the end of metadata,

so it may not work correctly on your computer.

The module fix the import bug of torch-rs (could not use cuda)

so in this module you can use your cuda without import `torch_cuda.dll`

If possible I will add more useful functions but currently it is a tool for my competition.

By the way, I will add linux support soon.