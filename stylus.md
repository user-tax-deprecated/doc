
[stylus 中文文档](https://www.stylus-lang.cn)

[stylus-supremacy](https://thisismanta.github.io/stylus-supremacy/) 
排版工具

vim 安装 `coc-vetur`

`~/.config/nvim/coc-settings.json` 配置如下

```
{
  "languageserver": {
    "vls": {
      "command": "/usr/local/bin/vls",
      "filetypes": ["vlang"]
    },
    "zls": {
      "command": "/usr/local/bin/zls",
      "filetypes": ["zig"]
    }
  },
  "diagnostic.hintSign": "→",
  "diagnostic.infoSign": "💡",
  "diagnostic.warningSign": "⚠️",
  "diagnostic.errorSign": "×",
  "suggest.floatEnable": true,
  "coc.preferences.formatOnSaveFiletypes": ["vue"],
  "python.linting.enabled": true,
  "python.linting.flake8Enabled": false,
  "python.linting.pylintEnabled": true,
  "stylusSupremacy.alwaysUseImport": true,
  "stylusSupremacy.alwaysUseZeroWithoutUnit": true,
  "stylusSupremacy.insertBraces": false,
  "stylusSupremacy.insertColons": false,
  "stylusSupremacy.insertNewLineAroundBlocks": true,
  "stylusSupremacy.insertNewLineAroundImports": true,
  "stylusSupremacy.insertNewLineAroundOthers": true,
  "stylusSupremacy.insertNewLineAroundProperties": true,
  "stylusSupremacy.insertSemicolons": false,
  "stylusSupremacy.preserveNewLinesBetweenPropertyValues": true,
  "stylusSupremacy.reduceMarginAndPaddingValues": true,
  "stylusSupremacy.sortProperties": "alphabetical",
  "vetur.format.defaultFormatter.css": "stylus-supremacy",
  "vetur.validation.style": false,
  "rust-analyzer.updates.channel": "nightly",
  "rust-analyzer.cargo.loadOutDirsFromCheck": true,
  "rust-analyzer.procMacro.enable": true,
  "rust-analyzer.diagnostics.disabled": ["unresolved-proc-macro"],
  "rust-analyzer.updates.checkOnStartup": false,
  "svelte.enable-ts-plugin": true
}
```
