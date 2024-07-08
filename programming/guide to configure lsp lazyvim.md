---
tags:
  - own-guide
  - lazyVim
  - setting
---


**Create the `lsp.lua` Configuration File:**

- Begin by installing Mason in LazyVim.
- Create a file named `lsp.lua` to configure the language servers. You can reference a sample configuration provided in the video between the timestamps 49:09 and 50:00.
```lua
return {
  {
    "williamboman/mason.nvim",
    opts = function(_, opts)
      vim.list_extend(opts.ensure_installed, {

        "prettier", -- prettier formatter
        "stylua", -- lua formatter
        "isort", -- python formatter
        "black", -- python formatter
        "pylint", -- python linter
        "eslint_d", -- js linter
        "ruff-lsp",
      })
    end,
  },
}

```
**Run LazyVim Helper:**

- With the `lsp.lua` file in place, you can now deploy the LazyVim helper.
- Execute the command `leaders-cm` to view a comprehensive summary of installed and available packages related to LSP (Language Server Protocol), DAP (Debug Adapter Protocol), Linter, and Formatter.![[Captura desde 2023-11-27 18-24-24.png]]
**Install Additional Language Server Plugins:**

- Use the `:LazyExtra` command to install extra language server plugins.
- Enable or disable extensions based on your preferences.
- It's normal to encounter errors during this process due to missing dependencies. If any package returns an error, identify the missing dependency by checking the error message. You can manually install the missing dependency using the command `LspInstall [package]`.
- These steps should help you set up Mason in LazyVim and configure language servers for various programming languages. If you encounter errors, carefully read and address the error messages, ensuring that dependencies are installed as needed.