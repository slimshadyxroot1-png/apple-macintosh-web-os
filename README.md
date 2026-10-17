# Mac System 1 Web OS

My attempt at recreating the original 1984 Macintosh desktop in the browser. It's plain HTML, CSS and JavaScript, with no frameworks and nothing to install.

I tried to stay close to how System 1 really looked: black and white only, the gray dither desktop, striped title bars, and menus that turn black when you open them. Where I couldn't match it exactly I went for something close.

## Running it

Open `index.html` in a browser and press Power On. That's it. If something doesn't load, try running it through a local server (the Live Server extension in VS Code works fine).

## What's in it

**Desktop**
- Backup Disk icon (opens the Finder) and a Trash icon, both draggable
- Windows you can drag, resize from the corner, zoom, and close
- Only the front window gets the striped title bar, like the real thing

**Apple menu** (these are the desk accessories System 1 shipped with)
- Alarm Clock: set a time and the menu bar flashes and beeps when it goes off. Open the clock to make it stop
- Calculator
- Control Panel: pick a desktop pattern and a font size, both are remembered
- Key Caps: an on-screen keyboard that lights up as you type
- Puzzle: the 15 sliding tiles game

**Other apps**
- Finder: a plain list of what's on the disk. Click to select, double-click to open
- MacPaint: pencil, line, rectangle, circle and fill, with undo, redo and clear
- Write: a text editor that saves to localStorage, so your text is still there after a refresh

**Menus**
- File: New Note, Open Backup Disk, Close Window
- Edit: Undo, Redo, Cut, Copy, Paste, Clear, Select All
- View: Clean Up Icons, Toggle Desktop Grid
- Special: Bring All to Front, Empty Trash, Restart, Shut Down

Toggle Desktop Grid makes icons snap to a grid when you drop them, and shows the grid lines while it's on.

## Notes on a few things

MacPaint starts with a 576 x 720 page, which is the size of the original. If you make the window bigger, the page grows to fill it. It never shrinks, so you won't lose anything you drew. Undo only restores the page at the size it had when you made the stroke.

The apps resize with their windows. Puzzle stays square, Key Caps rescales the keys, and the MacPaint tools move to a row across the top when the window gets narrow. This uses CSS container queries, so you need Chrome 105+, Firefox 110+ or Safari 16+.

## Font

The real Chicago font isn't free to bundle, so the CSS falls back to Geneva or Verdana. For a closer match, download ChicagoFLF.ttf and put it in `assets/fonts/`. The stylesheet already looks for it there.

## Files

```
index.html          all the windows and menus
styles.css          all the styling
assets/             apple-logo.png and the disk and trash icons
js/
  main.js           boot, menus, startup
  apps.js           the apps (paint, calculator, write, puzzle, clock, key caps)
  desktop.js        desktop icons
  window-manager.js dragging, resizing, stacking
```

## Not done yet

- Scrapbook, and the Note Pad with its eight pages
- Finder views by name, date and size, plus Get Info, rename and new folder
- Dragging things between windows

## Things that don't work like the real one

- There's no real file system. Everything is faked, apart from what's saved in localStorage
- Empty Trash doesn't do anything useful yet
- Windows have a zoom box on the right. System 1 didn't have one, but I wanted zoom to work

## Credits

Built by me, for fun. Apple owns the Macintosh and everything it came with. This is just a fan project.