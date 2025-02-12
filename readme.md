# A rust binding for yolov8 or higher aimed at detection

Quick Start:
```rust
use yolo_binding::{core::*, utils::*};
use std::ops::Index;
fn main() {
    const IMAGE_PATH: &str = "test.jpg";
    const OUTPUT_PATH: &str = "output.jpg";
    const MODEL_PATH: &str = "yolov5s.torchscript.pt";

    let model = YOLO::new(MODEL_PATH, true);
    let image = load_one_image("test.jpg").unwrap();
    let output = model.predict(&image).unwrap();
    let results = get_results(&output, 0.5, 0.5).unwrap();
    let picture = picture::export_one_image(&model.types, results.index(0).to_vec(), IMAGE_PATH).unwrap();
    picture.save(OUTPUT_PATH).unwrap();
}
```

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

TODO:fix docs.rs build problem.