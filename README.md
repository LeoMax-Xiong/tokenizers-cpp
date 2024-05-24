# tokenizers-cpp

## 介绍
这个工程提供了一个跨平台的C++ tokenizer库，这个库可以作为一个通用的tokenizer库进行部署使用。

这个库是对 [HuggingFace tokenizers library](https://github.com/huggingface/tokenizers) 和 [sentencepiece](https://github.com/google/sentencepiece) 进行封装，同时这个库是对c++一个最小依赖库。

这个库的目标是给基于语言模型的应用服务以最小依赖提供 tokenizer 本地部署能力，同时移除了跨平台封装的一些障碍。这个库也是 [MLC LLM](https://github.com/mlc-ai/mlc-llm) 工程的一部分。

我们已经再如下的平台上完成了测试：

* ios
* Android
* Windows
* Linux
* Web browser

## 开始

使用这个库的最简单的方式是将这个库添加为一个仓库的子模块，然后通过CMake的 `add_sub_directory` 命令添加这个仓库的头文件。需要注意的是，你的编辑器需要开启 `c++17` 的支持。

* 首先，你需要确保你本地已经安装了 `rust`
* 如果你正在进行交叉编译，需要确保目标平台 `rust` 相关依赖已经安装好了。例如，运行 `rustup target add aarch64-apple-ios` 安装 iOS 平台的相关依赖。
* 你需要链接 tokenizer 这个库

在 [example](example) 文件夹下有 CMake 工程的示例代码



## 其他的细节内容
当下，这个工程提供三种静态库：
* `libtokenizers_c.a`: C 语言对 `rust` 库的封装
* `libsentencepice.a`: sentencepiece 的静态库
* `libtokenizers_cpp.a` C++ 实现

如果你正在使用 IDE，你可以先试用cmake生成这三个库，然后将这三个库添加到你正在开发的环境中。

如果你正在使用 cmake，通过 `target_link_libraries(yourlib tokenizers_cpp)` 这个命令将会自动量链接这两个库。

当然你也可以下载 [MLC LLM](https://github.com/mlc-ai/mlc-llm)，尝试通过 MLC 将该库集成R到一个 LLM 应用中
