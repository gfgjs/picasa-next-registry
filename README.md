# Picasa Next — Internal Test Registry / 内测发行源

本仓库是 Picasa Next **内部测试**构建的插件发行源(exotic 格式插件的签名 registry 与插件包),
经 `raw.githubusercontent.com` 直链被内测安装包拉取。

- **不是正式发行渠道**:所有工件由**内测密钥**(`release-internal-2026-07`)签名,
  只有编译期注入了内测信任根的内测构建会接受;正式版本的信任根与发行源另行建立。
- 布局:`exotic/v1/{index.json, index.sig, <plugin_id>.zip}`,`index.json` 由 Ed25519 签名
  (`index.sig`),含防回滚单调序号与有效期。
- 更新方式:由私有仓 `scripts/exotic-internal-registry.mjs` 重新生成三件套后推送到本仓。

This repository hosts the **internal-testing** plugin registry for Picasa Next.
Artifacts are signed with internal test keys only and are rejected by any build
that does not embed the internal trust root. Not a production distribution channel.
