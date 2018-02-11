# Luakit

<<<<<<< HEAD
luakit is a fast, light and simple to use micro-browser framework extensible by
Lua using the WebKit web content engine and the GTK+ toolkit.
=======
luakit is a fast, light and simple to use micro-browser framework extensible
by Lua using the WebKit web content engine and the GTK+ toolkit.
>>>>>>> upstream/develop

## Don't Panic!

You don't have to be a developer to use luakit on a daily basis. If you are
familiar with vimperator, pentadactyl, jumanji, uzbl & etc you will find luakit
behaves similarly out of the box.

## Requirements

 * GTK+ 3
 * Lua 5.1 or LuaJIT 2
 * lfs (lua file system)
 * webkit2gtk
 * sqlite3

## Compiling

To compile the stock luakit run:

    make

To link against LuaJIT (if you have LuaJIT installed) run:

    make USE_LUAJIT=1

To build with a custom compiler run:

    make CC=clang

Note to packagers: you may wish to build luakit with:

    make DEVELOPMENT_PATHS=0

To prevent luakit searching in relative paths (`./config` & `./lib`) for user
configs.

The `USE_LUAJIT=1`, `PREFIX=/path`, `DEVELOPMENT_PATHS=0`, `CC=clang`
build options do not conflict. You can use whichever you desire.

## Installing

To install luakit run:

    sudo make install

The luakit binary will be installed at:

    /usr/local/bin/luakit

And configs to:

    /etc/xdg/luakit/

And the luakit libraries to:

    /usr/local/share/luakit/lib/

To change the install prefix you will need to re-compile luakit (after a `make
clean`) with the following option:

    make PREFIX=/usr
    sudo make PREFIX=/usr install

## Use Luakit

Just run:

    luakit [URI..]

Or to see the full list of luakit launch options run:

    luakit -h

## Configuration

<<<<<<< HEAD
The entire browsing experience is controlled by the configs in
`/etc/xdg/luakit`. Most of it is fine out of the box.

It is common to fork the configs from `/etc/xdg/luakit` into your home directory
to make your customizations. It is not necessary to copy and or edit all of the
files.

Do:

    mkdir -p $XDG_CONFIG_HOME
    cp -v /etc/xdg/luakit $XDG_CONFIG_HOME

Or:

    mkdir -p ~/.config
    cp -v /etc/xdg/luakit ~/.config

The several files of interest are explained below.

### `rc.lua`

This is the main config file which dictates which and in which order different
parts of the browser are loaded.

### `binds.lua`

Defines every action the browser takes when you press a button or combination of
buttons (even mouse buttons, direction key, etc) and the browser commands (I.e.
`:quit`, `:restart`, `:open`, `:lua <code>`, etc).

### `theme.lua`

Change fonts and colours used by the interface widgets.

### `window.lua`

Is responsible for building the luakit browser window and defining several
helper methods (I.e. `w:new_tab(uri)`, `w:close_tab()`, `w:close_win()`, etc).

### `webview.lua`

Is a wrapper around the webview widget object and is responsible for watching
webview signals (I.e. "key-press", "load-status", "resource-request-starting",
etc). This file also provides several window methods which operate on the
current webview tab (I.e. `w:reload()`, `w:eval_js("code here..")`, `w:back()`,
`w:forward()`).

### `modes.lua`

Manages the modal aspect of the browser and the actions that occur when
switching modes.

### `globals.lua`

Change global options like scroll/zoom step, default window size, useragent,
search engines, etc.
=======
The configuration options are endless, the entire browser is constructed by
the config files present in `/etc/xdg/luakit`

There are several files of interest:

 * rc.lua      -- is the main config file which dictates which and in what
                  order different parts of the browser are loaded.
 * theme.lua   -- change fonts and colours used by the interface widgets.

Just copy the files you wish to change (and the rc.lua) into
`$XDG_CONFIG_HOME/luakit` (defaults to `~/.config/luakit/`) and luakit will
use those files when you next launch it.
>>>>>>> upstream/develop

The following files used to be configuration files, but are not anymore:

 * binds.lua      -- is now a built-in module providing the default bindings.
                     Bindings should be changed with the `modes` APIs.
 * modes.lua      -- is now a built-in module providing built-in modes, as well
                     as providing APIs to manage bindings within those modes.
 * window.lua     -- is now a built-in module.
 * webview.lua    -- is now a built-in module.
 * webview_wm.lua -- is now a built-in module.
 * globals.lua    -- global settings have been moved to other modules.

These files will be silently ignored on startup so as to prevent errors; users
wishing to override the built-in modules should change `package.path`.

## HiDPI Monitor Configuration

If you have a HiDPI monitor (> 1920x1080) and find that web pages are too small,
you can change the `webview.zoom_level` on the settings page (luakit://settings/)
to 150 or 200 as per your taste.

## Uninstall

To delete luakit from your system run:

    sudo make uninstall

If you installed with a custom prefix remember to add the identical prefix
here also, example:

    sudo make PREFIX=/usr uninstall

## Reporting Bugs

Please use the bug tracker at:

  https://github.com/luakit/luakit/issues

## IRC

Join us in `#luakit` on the `irc.oftc.net` network.
