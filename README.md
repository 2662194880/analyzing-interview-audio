# Analyzing Interview Audio

一个用于复盘面试录音的 Codex Skill。它可以帮助 Codex 按固定流程分析业务面、HRBP 面、电话面试等音频材料：先转写，再区分面试官和候选人，最后输出面试总结、表现不足和下一轮准备建议。

## 适用场景

- 业务面试录音复盘
- HRBP 面试录音复盘
- 校招、实习、管培生面试总结
- 从录音中提取岗位信息、面试官关注点和风险信号
- 根据真实回答改写下一轮面试话术

## 能做什么

- 本地转写面试音频，优先保护隐私
- 根据问答结构区分“面试官”和“候选人”
- 梳理面试官问了什么、候选人怎么答
- 总结岗位信息点，比如部门、工作内容、培养路径、稳定性要求
- 分析回答中的不足，比如表达太绕、职业规划不够坚定、岗位理解偏泛
- 给出可直接练习的下一轮回答模板

## 目录结构

```text
analyzing-interview-audio/
├── SKILL.md
├── README.md
├── agents/
│   └── openai.yaml
└── scripts/
    └── transcribe_interview.py
```

## 安装方式

把整个 `analyzing-interview-audio` 文件夹复制到 Codex 的个人 skills 目录：

```powershell
Copy-Item -Recurse .\analyzing-interview-audio $env:USERPROFILE\.codex\skills\
```

如果已经存在旧版本，可以先备份或覆盖。

## 转写依赖

转写脚本使用 `faster-whisper`。如本机没有安装，需要先安装：

```powershell
python -m pip install faster-whisper
```

首次运行模型时可能会下载 Whisper 模型。面试音频默认在本机处理，不需要上传到公共平台。

## 使用示例

在 Codex 中可以这样说：

```text
用 analyzing-interview-audio 帮我分析这段业务面试音频，区分我和面试官的声音，总结面试信息点，并指出我的不足。
```

或者：

```text
帮我复盘这段 HRBP 面试录音，提取面试官关注点，并给我下一轮回答模板。
```

也可以单独运行转写脚本：

```powershell
python .\scripts\transcribe_interview.py "D:\interview.mp3" --model small --language zh
```

脚本会生成：

- `interview.transcript.json`
- `interview.transcript.txt`

## 输出建议格式

Skill 会引导 Codex 输出：

1. 整体判断
2. 面试信息点
3. 问题复盘
4. 不足与风险
5. 下次怎么说

## 隐私说明

面试录音可能包含个人信息和公司业务信息。建议优先使用本地转写工具。如需联网安装工具或下载模型，应先确认是否接受。

