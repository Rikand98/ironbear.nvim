# ⚙️🐼`ironbear.nvim`🐻‍❄️ ⚙️

A neovim plugin for debugging `pandas` and `polars` DataFrames, based on [bear.nvim](https://github.com/nelnn/bear.nvim).

## ⚡️ Requirements

- [iron.nvim](https://github.com/Vigemus/iron.nvim)
- [visidata](https://www.visidata.org/install/) installed globally
- [polars](https://github.com/pola-rs/polars) and/or
  [pandas](https://github.com/pandas-dev/pandas) installed in your virtual
  environment

## 📦 Installation

### [lazy.nvim](https://github.com/folke/lazy.nvim)

```lua
{
  "rikand98/ironbear.nvim",
  dependencies = {
    "Vigemus/iron.nvim",
  },
}
```


<details>
<summary>Default Confguration</summary>

```lua
{
  "rikand98/ironbear.nvim",
  dependencies = {
    "Vigemus/iron.nvim",
  },
  opts = {
      cache_dir = "~/.cache/nvim/ironbear",
      file_name = "tmp_" .. os.date("%m%d_%H%M%S") .. ".csv",
      remove_file = true, -- remove file upon quitting visidata
      window = {
        width = 0.9,
        height = 0.8,
        border = "rounded"
      },
      keymap = {
        visualise = "<leader>dff",
        visualise_buf = "<leader>dff",
        exit_terminal_mode = "<C-o>",
      }
  },

  config = function(_, opts)
    local df_visidata = require("ironbear")
    df_visidata.setup(opts)
  end,

  ft = { "python" },
}

```
</details>

## 🚀 Usage (with default keymaps)
- `<leader>dff`/`<leader>dfb` to view the dataframe under the cursor.
- `<leader>dff`/`<leader>dfb` in the repl session and input the dataframe variable.
- `<C-o>` to exit from terminal to normal mode and `i` to enter. This is useful
  when you want to change buffers.
- `q` to close floating window or buffer in normal and terminal mode.


## ⌘ Commands
| Command | Action |
| ------------- | -------------- |
| DFView | View dataframe in a floating window|
| DFViewBuf | View dataframe in a new buffer|
| DFClean | Clear cache directory|


> [!NOTE]
> This is a modified package of [bear.nvim](https://github.com/nelnn/bear.nvim) that uses iron.nvim instead of nvim-dap.
