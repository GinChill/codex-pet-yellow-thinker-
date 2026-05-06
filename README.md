# Codex Pet: Yellow Thinker (奶蛙 / Naifrog Variant)

这是一个基于 Codex `hatch-pet` 流程制作的自定义宠物项目。  
角色是社区流行“奶龙变种奶蛙”风格的 `Yellow Thinker`，已完成可导入包产物。

## Project Highlights

- 使用 `hatch-pet` 标准流程生成与封装
- 输出符合 Codex pet 规范的 `spritesheet.webp + pet.json`
- 已完成“严格语义映射”版本状态调整
- 已推送到 GitHub 仓库用于持续迭代

## Repository Structure

主要内容在 `yellow-thinker-run/`：

- `prompts/`：每个状态行的生成提示词
- `decoded/`：各状态原始行图
- `frames/`：拆帧结果
- `final/`：最终图集与验证结果
- `qa/`：联系表与质检结果
- `package/`：可分发宠物包（`pet.json` + `spritesheet.webp`）
- `imagegen-jobs.json`：生成任务与溯源记录
- `pet_request.json`：宠物请求配置

## Strict State Mapping (当前版本)

Codex 内部状态名与语义映射如下：

- `idle` -> 待机
- `review` -> 思考（thinking）
- `running` -> 工作（working）
- `jumping` -> 成功庆祝（success）
- `failed` -> 错误/崩溃（error）
- `waiting` -> 睡眠（sleeping）

说明：Codex 引擎使用固定状态键（如 `review/jumping/waiting`），本项目通过提示词将其语义严格对齐到目标人格状态。

## Final Artifacts

可直接使用的核心文件：

- `yellow-thinker-run/final/spritesheet.webp`
- `yellow-thinker-run/package/pet.json`
- `yellow-thinker-run/package/spritesheet.webp`

## Install to Local Codex Pets

将打包产物复制到本地 pets 目录，例如：

`~/.codex/pets/yellow-thinker/`

目录中需要同时包含：

- `pet.json`
- `spritesheet.webp`

## Rebuild Workflow (hatch-pet)

1. 准备 run 目录与任务清单（`prepare_pet_run.py`）
2. 生成并记录 base / rows（`record_imagegen_result.py`）
3. 需要时修复指定状态行（重生单行）
4. 终稿组装（`finalize_pet_run.py`）
5. 打包（`package_custom_pet.py`）

## Known Notes

- 在部分 Windows 环境，`finalize_pet_run.py` 的视频预览步骤可能因系统临时目录权限失败（`WinError 5`），但不影响最终宠物包使用。
- “是否始终置顶”属于 Codex App 窗口层级行为，不由 `pet.json/spritesheet` 决定。

## Credits

- Character direction: 社区奶龙变种奶蛙风格（Yellow Thinker）
- Pipeline: Codex `hatch-pet` skill + image generation workflow
