# How To View Markdown In Ubuntu

---

# Simple Markdown viewer for Ubuntu (standalone program, not something that requires usage of an internet browser)

---

- ReText:
  [ReText](https://github.com/retext-project/retext "https://github.com/retext-project/retext") is GUI program runs on Python3 with PyQt5
	  - runs locally on Linux: Yes (also on Windows and Mac)
	  - normal program, not a browser addon: Yes, Written in Python, easy to deal with
	  - simple and lightweight: Yes. On its own, it comes with the basic - and you can add more (like support for specific Markdown dialects as [Markdown Extra](michelf.ca/projects/php-markdown/extra/ "michelf.ca/projects/php-markdown/extra/") or [MathJax](www.mathjax.org "www.mathjax.org") if you need.)
	  - open source: Yes (using GPLv2)

- Grip:
  [Grip](https://github.com/joeyespo/grip "https://github.com/joeyespo/grip") is command line markdown render-er.
	  - Markdown? [Github Flavored](https://guides.github.com/features/mastering-markdown "https://guides.github.com/features/mastering-markdown")
		- Linux - Yes
		- Normal - Yes (command line tool)
		- Offline - No (There's also a [work-in-progress](https://github.com/joeyespo/grip/tree/offline-renderer "https://github.com/joeyespo/grip/tree/offline-renderer") brance to provide offline rendering.)
		- Simple/Lightweight - Yes (command line tool)
		- Open Source - Yes
		- Bonus:
		  - **Export** to PDF/HTML
			- **Host** locally as a webpage/wiki
- Atom
  [Atom](https://atom.io "https://atom.io") works nicely out of the box - just open the Markdown file and hit **Ctrl+Shift+M** to toggle the Markdown preview panel next to it. It handles HTML and images also. Though note that performance of Atom is ridiculously poor and that development of the software appears to be stopping - see [On Github](https://github.com/atom/atom/graphs/contributors "https://github.com/atom/atom/graphs/contributors") (probably as it makes no sense to Microsoft to maintain two text editors in the same niche) **Note:** [Markdown Plugin for Atom](https://atom.io/packages/markdown-preview-enhanced "https://atom.io/packages/markdown-preview-enhanced") is an excellent, full feature markdown addition that includes themes and link resolution, which the default markdown-preview does not currently support.
- Haroopad
  [Haroopad](pad.haroopress.com/user.html "pad.haroopress.com/user.html") is more feature-filled than Remarkable, and looks like a dev tool. (The dev version of this app is also coming soon.)
- Springseed
  [Springseed](https://github.com/byhestia/springseed "https://github.com/byhestia/springseed") If you need a note taker than this one does the job Beautifully.
- ghostwriter
  In Ubuntu 20.04, install from the bundled apt repos:
	```
	sudo apt install ghostwriter
	```
	- bundled in official Ubuntu repos
	- binary executable rather than a script
	- [actively maintained](https://github.com/wereturtle/ghostwriter "https://github.com/wereturtle/ghostwriter")
- Glow
  [Glow](https://github.com/charmbracelet/glow/releases "https://github.com/charmbracelet/glow/releases") is absolutely lightweight. You don't even need to leave the terminal. Works on Linux, Mac and Windows.
	Usages: glow file_name.md
- Okular
  [Okular](https://okular.kde.org "https://okular.kde.org") has a [Markdown backend](https://docks.kde.org/trunk5/en/kdegraphics/okular/configure-backends.html#config-markdown "https://docs.kde.org/trunk5/en/kdegraphics/okular/configure-backends.html#config-markdown"), which allows it to dispaly Markdown-formated text. On Debian-based systems (like Ubuntu) you might have to install the [okular-extra-backends](https://packages.debian.org/buster/okular-extra-backends "https://packages.debian.org/buster/okular-extra-backends") package to use it. The nice thing about Okular is taht it is just a plain viewer. You can use your text editor of choice, and as soon as you save the Markdown document, Okular reloads the document.
- mdless
  If you're using Ubuntu:
	```
	sudo apt install ruby
	sudo gem install mdless
	```
	[Ruby Markdown Renderer in Terminal](https://brettterpstra.com/2015/08/21/mdless-better-markdown-in-terminal/ "https://brettterpstra.com/2015/08/21/mdless-better-markdown-in-terminal/"): Old resource for mdless terminal markdown renderer
