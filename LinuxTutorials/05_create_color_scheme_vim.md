# Create Color Scheme For Vim

---

[] Why create your own theme?

Because you can and it's very simple and fun.

[] How do you set your vim theme?

If you want to use any theme in vim, you need to save the name.vim (the .vim file of the color scheme) in your color directory `~/.vim/colors` If it doesn't exists, you can create one. Then go to .vimrc file and add `colorscheme colorscheme_name`

[] Terms you know before you start

In vim you have 7 terms for highlighting:
**guifg**, **guibg:** The colors of your graphical vim (gui = graphical user interface) .guifg is for your text color, and guibg is for the background.
**gui:** The text style, can be bold, italic or underline (as far as I know).
**ctermfg**, **ctermbg**, **cterm:** same as guifg, guibg and gui, but for the terminal.
There is also **term**, but we won't talk about it now.

[] Writing your color scheme

First, we have boilerplate code that we need to write in our colorscheme.vim file:

```

highligh clear
if exists("syntax_on")
	syntax reset
endif

```

This code is clearing any highlights defined before. 'highligh clear' resets the highlighting the user added, and 'syntax reset' gets the color back to default ones. The default colors are determined by the background variable, that we should set too:

```

set background=dark

```

This sets the color palette, it can be dark or light. And of course naming our color scheme:

```

set g:colors_name="theme-name"

```

It helps identifying our color scheme. So our final boilerplate code is:

```

highlight clear
if exists("syntax on")
	syntax reset
endif

set background=dark
set g:colors_name="theme-name"

```

That's it. Now the real deal - the commad to set new high light is `highlight group_name key=value`

When the key is one of the terms we met above (guifg, guibg, etc...) group name by syntax.txt

[syntax](https://vimdoc.sourceforge.net/htmldoc/syntax.html) group name is to be used for syntax item that match the same kind of thing. These are then linked to a highlight group that specifies the color.

You can find groups names conventions if you type in your vim `:help syntax.txt` and scroll down to NAMING CONVENTIONS.

So for example, if you want to change the backgroud of the gui vim to white, and the comment text color to red and bold

```

highlight Normal guibg=#ffffff
highlight Comment guifg=#ff0000 gui="bold"

```

And let the magic happen.

**Important Note: You want to highlight the terminal**

When you choose color for your gui, you use rgb, but in the terminal you use "Indexed Color" which can include 8|16|88|256 colors, depends on your terminal. Mine is 256 so I found [this page](https://jonasjacek.github.io/colors/) that contains the 256 colors and their numbers. So, if you want your text terminal color to be red you write `highlight Normal ctermfg=9`

As programmers, we should always search for shortcuts, so instead of writting commands for each group, we should write a function! My function assumes that you always pass it group name, guibg, guifg, gui, ctermfg, ctermbg (no need for cterm since it will be same as gui). You can also check out [thi article](https://www.codementor.io/sandeepkumar4/vimlearning-how-to-create-vim-color-scheme-j7lmp1xkc), which shows a different kind of function for highlighting.
```

function! Coloring(group,guibg,guifg,gui,ctermbg,ctermfg)
	let highlightstr = 'highlight ' . a:group . ' '
	let highlightstr = 'guibg=' . a:guibg . ' '
	let highlightstr = 'guifg=' . a:guifg . ' '
	let highlightstr = 'gui=' . a:gui . ' '
	let highlightstr = 'ctermbg=' . a:ctermbg . ' '
	let highlightstr = 'ctermfg=' . a:ctermfg . ' '
	let highlightstr = 'cterm=' . a:cterm . ' '

	execute histring
endfunction

```

This function simply the command we met before and in the end, execute it. So if, for example we want our comment text to be red, we'll call our function like `call Coloring("Comment","NONE",#ff0000,"NONE","NONE",9)` Cool! Is not it?

** Linking highlighs**

If you want some groups to have same hightlight you simply write `highlight link x y` when x copies the highlight of y.

** Get The Syntax Group**

An easy function I found [here](https://vimcasts.org/episodes/creating-colorschemes-for-vim) helps you get the syntax group of the word your curson is on. Just save the function on your .vimrc file, and press ctrl+shift+p on the word you want to check its syntax word.

```

nmap <C-S-P> :call <SID>SynStack()<CR>
function! <SID>SynStack()
	if !exists("*synstack")
		return
	endif
	echo map(synstack(line('.'), col('.')), 'synIDattr(v:val, "name")')
endfunc

```

That's it. Thanks for reading.
