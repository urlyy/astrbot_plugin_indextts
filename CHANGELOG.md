# 更新日志

## 2.0.1 — 2026-11-11

- 新增 `glossary_enabled` 与 `glossary_terms`：术语表在 AstrBot 插件配置中管理，默认让 `ASOUL`、`A-SOUL` 读作「诶叟」。
- 手动 `/tts` 与自动语音通过已有 `/on_add_glossary_term` 和 `/on_glossary_checkbox_change` 同步读音，再调用原有 24 参数 `/gen_single`，无需修改 IndexTTS 服务。
- 记录本插件已同步的词条；删除或关闭后，下次合成将旧词条恢复为原词。`/tts_params` 显示插件术语数量。

## 2.0.0 — 2026-09-05

### 新增

- 新增 `_conf_schema.json`：全部配置改为在 AstrBot Desktop / WebUI 的「插件配置」页编辑，保存后由 AstrBot 注入，无需再手工修改插件目录里的 JSON 文件。

### 变更

- 适配 **IndexTTS 2.0** 的 `/gen_single` 接口，改用 24 个位置参数调用，不再依赖 Gradio 自动生成的 `param_16`～`param_23` 参数名。
- 配置项 `infer_mode`、`max_text_tokens_per_sentence`、`sentences_bucket_max_size` 收敛为 `max_text_tokens_per_segment`。
- `temperature` 默认值 1.0 → 0.8；`max_mel_tokens` 默认值 600 → 1500。
- `default_reference_audio` 支持相对插件根目录的路径（如 `data/voice.wav`），留空时回退到内置的 `data/voice.wav`。
- 插件显示名改为「IndexTTS 2.0 语音合成」，README 与 metadata 中注明目前不保证兼容 IndexTTS 2.5。
- `/tts_status` 中「推理模式」一项替换为「单段最大 Token」。

### 移除

- 移除 `auto_capture_voice` 功能（用户发送语音时自动保存为个人音色）及其配置项。
- 移除 `data/config.json` 手工配置文件与 `_load_config()` / `_save_config()`。

### 其他

- `.gitignore` 恢复忽略 `.idea/`，仓库不再跟踪 IDE 配置。
- 版本号统一为 2.0.0，`repo_url` 指向 `https://github.com/urlyy/astrbot_plugin_indextts`，作者改为 `urlyy`。

---

更早版本的改动请查看 git 提交历史。
