# 更新日志

本项目的重要变更都会记录在此文件中。

格式基于 [Keep a Changelog](https://keepachangelog.com/zh-CN/1.1.0/)，
版本号遵循 [Semantic Versioning](https://semver.org/lang/zh-CN/)。

## [Unreleased]

### 变更

- README 修正仓库归属链接，并更新 LZMA SDK、Snappy、7-Zip、brotli.js、zlib-rs 等条目的链接与描述
- 文档站入口改为 GitHub Pages 地址
- CI 工作流增加并发控制并收窄触发路径；ccache 缓存路径改为 `~/.cache/ccache`
- CHANGELOG 版本链接改用 commit SHA，避免在尚未创建 tag 时出现 404

### 修复

- 更新 `docs/package-lock.json`，修复可自动修复的依赖漏洞

## [1.1.0] - 2026-09-28

### 新增

- README 转型为面向中文社区的精选列表（awesome list）：收录 70+ 条经过链接验证的压缩库、工具与学习资源
- 新增 `CONTRIBUTING.md`（中文贡献指南）、`.editorconfig`、`.gitattributes`
- 新增 issue 模板（bug report / feature request）与 PR 模板
- 新增 `awesome-lint` CI 工作流，自动检查列表格式与链接有效性
- 使用 libbsc 块排序实现真实的 BSC 压缩示例
- CI 现在构建并测试 BSC 示例（`-DAWESOME_COMPRESSION_ENABLE_BSC=ON`）
- CI 增加 ccache 缓存以加快增量构建
- 启用 `CMAKE_EXPORT_COMPILE_COMMANDS`，便于编辑器/LSP 集成
- 所有 C++ 示例通过共享 `run` 帮助函数统一错误处理

### 变更

- README 由英文项目介绍改为中文精选列表，含目录、分类（算法库/学习资源/工具/基准/格式规范/中文资源等）与配套内容指引
- 许可证由 MIT 切换为 CC0-1.0（与 awesome 社区惯例一致）
- 文档站 GitHub 链接从 AICL-Lab 更新为当前仓库地址
- C++ 示例失败时输出友好的 stderr 信息并以退出码 1 结束，不再调用 `std::terminate`
- `read_file` 接受 `std::string_view`；`print_stats` 接受 `std::string_view`
- 将 libbsc 固定到特定 commit（`5e5c2ef`，bsc 3.3.12），以保证构建可复现
- 将 `cmake_minimum_required` 从 3.24 降至 3.16，以支持更广泛的工具链
- 简化 `.gitignore`（合并构建目录模式）
- 文档站改为仅中文；移除不完整的英文 locale

### 修复

- 修正 BSC 仓库链接为 `IlyaGrebnov/libbsc`（原路径已失效）
- 更新中文总览中过时的“BSC placeholder”表述，以反映真实示例
- 修复 BSC 示例编译：上游 libbsc target 缺少头文件目录
- BSC 示例增加输入大于 `INT_MAX` 的保护（与 LZ4 一致）
- LZMA 示例使用 `std::numeric_limits` 替代 C 的 `UINT64_MAX` 宏
- ZSTD 示例使用 `ZSTD_CLEVEL_DEFAULT` 替代硬编码级别
- Brotli 示例检查 `BrotliEncoderMaxCompressedSize` 的失败返回值 0
- `read_file` 通过 `gcount()` 校验实际读取的字节数

## [1.0.0] - 2026-05-22

### 新增

- VitePress 文档站（中文优先）
- 压缩学习指南：
  - 压缩基础
  - 编码模型（Huffman、LZ77、BWT）
  - 算法选择指南
- 6 个压缩库的算法笔记：
  - ZSTD
  - LZMA
  - BSC
  - LZ4
  - zlib
  - Brotli
- 对比矩阵与场景选型
- C++17 压缩示例与 CMake 构建系统
- GitHub Actions CI/CD 工作流：
  - 文档部署到 GitHub Pages
  - C++ 构建与测试自动化

### 变更

- 丰富算法笔记，补充工程实践与学习路径
- 新增 C++ 示例使用文档
- 澄清 BSC 示例的 placeholder 状态

### 修复

- 修复可选 BSC 链接的跨平台兼容性
- 临时 CMake 构建目录现在正确加入 gitignore

## [0.1.0] - 2026-05-19

### 新增

- 初始项目结构
- VitePress 文档骨架
- C++ 示例工程骨架
- ZSTD、LZMA、LZ4、zlib、Brotli 基础压缩示例
- BSC placeholder 示例

[Unreleased]: https://github.com/holtwood/awesome-compression/compare/62bcd25...HEAD
[1.1.0]: https://github.com/holtwood/awesome-compression/compare/da4b800...62bcd25
[1.0.0]: https://github.com/holtwood/awesome-compression/compare/1f6ba21...da4b800
[0.1.0]: https://github.com/holtwood/awesome-compression/compare/175bb3b...1f6ba21
