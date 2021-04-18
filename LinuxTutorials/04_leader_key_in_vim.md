# What Is The <Leader> Key In Vimrc?

---

A simple command `noremap <Leader>W :w !sudo tee % > /dev/null`. But what does it means `<Leader>` key in vim?

Well, In this example, it simply means in vim typing \W (Backslash then W) in Normal Mode will save the current file using the `sudo` command.

---

[ x ] Does that mean `<Leader>` means backslash? Well, not quite. 

The `<Leader>` key is a reference to specific key defined by the `mapleader` variable. Many people change `\ to ,` because they find it easier to type.
Change `<Leader>` key using:
```

let mapleader=","

```

The mapleader variable is easy to change, and if you always remember to map keys with <Leader> then you'll avoid confusing your own customization with Vim's default keyboard shortcuts. The beauty of the `<Leader>` key is it effectively gives us a namespace for customized keyboard shortcuts. You don't need to worry about treading on Vim's toes when you set a Keyboard shortcut using `<Leader>`.

Vim waits for 1000 milliseconds after the `<Leader>` key has been pressed, so if you take too long to press the next key in the sequence it won't be matched. This timeout canbe changed by using `:set timeoutlen` to set specific value.
