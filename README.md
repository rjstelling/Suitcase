# Suitcase

A flexible command line tool for instantly deploying user interfaces for simple commands and scripts. 

## Command-Line Utility

### Usage

	OVERVIEW: A flexible command line tool for instantly deploying user interfaces
	for simple commands and scripts.

	USAGE: Suitcase <subcommand>

	OPTIONS:
	  --version               Show the version.
	  -h, --help              Show help information.

	SUBCOMMANDS:
	  basic                   Launch a basic Suitcase process, that has a main menu
							  and an icon in the Dock when running.
	  utility                 Launch a utility Suitcase process, without a Dock
							  icon or main menu.

#### Suitcase basic

	OVERVIEW: Launch a basic Suitcase process, that has a main menu and an icon in
	the Dock when running.

	USAGE: Suitcase basic <options>

	OPTIONS:
	  --name <name>           The name of the currently running Suitcase. 
			The name is used in several places to refer to the running process. It
			should be treated like the name of an application, should but
			descriptive. This is also used as the main window title if
			--window-title is not set.
	  --icon <path>           A file system path to an image file. 
			An image file (JPEG, PNG) used as the process icon. Only basic Suitcase
			processes show in the Dock and Application Switcher.
	  -E, --copy-environment-variable <variable>
							  The name of an environment variable 
			The value of the environment variable is copied and exposed using the
			same key to all of actions.
	  --window-title <title>  A string used as the main window title. 
			Optional. If not set the value of --name is used. Even if the window
			title is hidden it is advised to set the window title to improve
			acessability.
	  --window-floating       The main window floats above all others. 
			If set the main window float above every other window on the system.
	  --window-width <pixels> Initial window width. (default: 400)
			The integer width in pixels of the main window on its first run. This
			is overidden if the user changes the window size.
	  --window-height <pixels>
							  Initial window height. (default: 320)
			The integer height in pixels of the main window on its first run. This
			is overidden if the user changes the window size.
	  --drop-working-directory
							  Main window accepts dropped directories. 
			Enable setting the working directory by dropping a directory on the
			main window.
	  --working-directory <path>
							  A file system path to a directory. 
			Sets the working directory for all Actions before they are execuited.
			This can be overridden is the --drop-working-directory option is also
			used.
	  --control-type <type>   The type of control. 
			Required. The following keys are valid controls; label, button, text,
			text-field, working-directory-label and error-text.
				- label, short text used to discribe a region or group of controls.
				- text, an area of text that can scroll.
				- text-field, editable text field. Actions can be attached to
			text-fields and are triggered when the return button is pressed.
				- button, a control that can trigger an action when pressed.
				- working-directory-label, a speical case label that shows the
			currently set working directory (see: --drop-working-directory and
			--working-directory).
	  --control-title <title> The title or content of a control. 
			Required. The inital value of a controls title or content. An action
			can change the if the control has an identifier and the action
			specifies an action destination (see: --control-identifier and
			--control-action-destination).
	  --control-identifier <identifier>
							  A string to uniquly identify the control. 
			Optional. An identfier can be any string but it is strongly advised to
			use reverse domain name notation. Control identifiers are used by
			action destinations to output the their results. Actions can also refer
			to identifiers in action parameters (see: --control-action-destination
			and --control-action-parameter). The value/title of a control is also
			available as an enviroment variable when executing actions (see
			--copy-environment-variable).
	  --control-action <action>
							  A command line string. 
			Optional. Action strings can refer to any command or script installed
			on the machine. Commands and scripts need to be referenced with
			absolute file paths or releitive to the working directory (see:
			--drop-working-directory and --working-directory). Multiple actions can
			be performed by seperating them with an & (ampersand). Output from one
			command can be piped to a second using | (pipe). Arguments can be
			decalred inline, in the control action string or by using
			--control-action-parameter.
	  --control-action-parameter <parameter>
							  A list of parameters. 
			Optional. A comma seperated list of parameters passed to an action. If
			a parameter matches an environment variable it is subsituted for the
			value before being passed to the action (see
			--copy-environment-variable and --control-identifier).
	  --control-action-destination <identifier>
							  A string to identify a control. 
			Optional. The output of an action is used to set the tile or content of
			the contole matching the identifier (see: --control-identifier).
	  --control-group-identifier <identifier>
							  A string to uniquly identify a group of controls. 
			Optional. An identfier can be any string but it is strongly advised to
			use reverse domain name notation. Group identifiers are used to
			spacialy group contols on screen. The first control in the group
			determines the on screen order of the group.
	  --menu-title <title>    The path of the menu item. 
			Required. Menu titles accept a hierarchical path to the menu, seperated
			by >. This can be used to create sub-menus of any depth (although 3 is
			considered a maximum). To add items to the Suitcase menu set a path of,
			Application>Sub menu>Menu Item.
	  --menu-action <action>  A command line string. 
			Optional. Action strings can refer to any command or script installed
			on the machine. Commands and scripts need to be referenced with
			absolute file paths or releitive to the working directory (see:
			--drop-working-directory and --working-directory). Multiple actions can
			be performed by seperating them with an & (ampersand). Output from one
			command can be piped to a second using | (pipe). 
	  --menu-shortcut <shortcut>
							  The keyboard shortcut string. 
			Optional. A single character used as the keyboard shortcut. Lowercase
			character will be shown as ⌘Y uppercase characters are shown as ⇧⌘Y.
			Shortcuts *do not* support other modifiers. (Please file a bug if this
			is important to you).
	  --menu-action-destination <identifier>
							  A string to identify a control. 
			Optional. The output of an action is used to set the tile or content of
			the contole matching the identifier (see: --control-identifier).
	  --version               Show the version.
	  -h, --help              Show help information.

#### Suitcase utility

	OVERVIEW: Launch a utility Suitcase process, without a Dock icon or main menu.

	USAGE: Suitcase utility <options>

	OPTIONS:
	  --name <name>           The name of the currently running Suitcase. 
			The name is used in several places to refer to the running process. It
			should be treated like the name of an application, should but
			descriptive. This is also used as the main window title if
			--window-title is not set.
	  --icon <path>           A file system path to an image file. 
			An image file (JPEG, PNG) used as the process icon. Only basic Suitcase
			processes show in the Dock and Application Switcher.
	  -E, --copy-environment-variable <variable>
							  The name of an environment variable 
			The value of the environment variable is copied and exposed using the
			same key to all of actions.
	  --window-title <title>  A string used as the main window title. 
			Optional. If not set the value of --name is used. Even if the window
			title is hidden it is advised to set the window title to improve
			acessability.
	  --window-floating       The main window floats above all others. 
			If set the main window float above every other window on the system.
	  --window-width <pixels> Initial window width. (default: 400)
			The integer width in pixels of the main window on its first run. This
			is overidden if the user changes the window size.
	  --window-height <pixels>
							  Initial window height. (default: 320)
			The integer height in pixels of the main window on its first run. This
			is overidden if the user changes the window size.
	  --drop-working-directory
							  Main window accepts dropped directories. 
			Enable setting the working directory by dropping a directory on the
			main window.
	  --working-directory <path>
							  A file system path to a directory. 
			Sets the working directory for all Actions before they are execuited.
			This can be overridden is the --drop-working-directory option is also
			used.
	  --control-type <type>   The type of control. 
			Required. The following keys are valid controls; label, button, text,
			text-field, working-directory-label and error-text.
				- label, short text used to discribe a region or group of controls.
				- text, an area of text that can scroll.
				- text-field, editable text field. Actions can be attached to
			text-fields and are triggered when the return button is pressed.
				- button, a control that can trigger an action when pressed.
				- working-directory-label, a speical case label that shows the
			currently set working directory (see: --drop-working-directory and
			--working-directory).
	  --control-title <title> The title or content of a control. 
			Required. The inital value of a controls title or content. An action
			can change the if the control has an identifier and the action
			specifies an action destination (see: --control-identifier and
			--control-action-destination).
	  --control-identifier <identifier>
							  A string to uniquly identify the control. 
			Optional. An identfier can be any string but it is strongly advised to
			use reverse domain name notation. Control identifiers are used by
			action destinations to output the their results. Actions can also refer
			to identifiers in action parameters (see: --control-action-destination
			and --control-action-parameter). The value/title of a control is also
			available as an enviroment variable when executing actions (see
			--copy-environment-variable).
	  --control-action <action>
							  A command line string. 
			Optional. Action strings can refer to any command or script installed
			on the machine. Commands and scripts need to be referenced with
			absolute file paths or releitive to the working directory (see:
			--drop-working-directory and --working-directory). Multiple actions can
			be performed by seperating them with an & (ampersand). Output from one
			command can be piped to a second using | (pipe). Arguments can be
			decalred inline, in the control action string or by using
			--control-action-parameter.
	  --control-action-parameter <parameter>
							  A list of parameters. 
			Optional. A comma seperated list of parameters passed to an action. If
			a parameter matches an environment variable it is subsituted for the
			value before being passed to the action (see
			--copy-environment-variable and --control-identifier).
	  --control-action-destination <identifier>
							  A string to identify a control. 
			Optional. The output of an action is used to set the tile or content of
			the contole matching the identifier (see: --control-identifier).
	  --control-group-identifier <identifier>
							  A string to uniquly identify a group of controls. 
			Optional. An identfier can be any string but it is strongly advised to
			use reverse domain name notation. Group identifiers are used to
			spacialy group contols on screen. The first control in the group
			determines the on screen order of the group.
	  --version               Show the version.
	  -h, --help              Show help information.

### Examples

#### Hello World

![Hello World](./Resources/hello-world.gif)

#### Menus

![Menus](./Resources/menus.gif)

	Suitcase --name="Demo App" --window-title="Menus" \
		--control-title="UUID" \
			--control-type="label" --control-identifier="com.label.uuid" \
		--menu-title="Action>Generate>UUID" \
			--menu-action="/usr/bin/uuidgen" \
				--menu-action-destination="com.label.uuid" \
		--menu-title="Action>Copy UUID" \
		--menu-shortcut="k" \
		--menu-action="/usr/bin/printenv com.label.uuid | /usr/bin/pbcopy"

#### Hidden Files & Folders

![Hidden Files & Folders](./Resources/hidden-files-abridged.gif)

	Suitcase --name="Hidden Finder Settings" \
	--control-title="Hidden Files & Folders:" \
		--control-group-identifier="com.finder.hidden" \
		--control-type="label" \
	--control-title="unknown" \
		--control-group-identifier="com.finder.hidden" \
		--control-type="label" \
		--control-identifier="com.label.hidden.state" \
	--control-title="Refresh" \
		--control-group-identifier="com.finder.hidden" \
		--control-type="button" \
		--control-action="/usr/bin/defaults read com.apple.finder AppleShowAllFiles | /usr/bin/sed s/1/Visible/g;s/0/Hidden/g" \
		--control-action-destination="com.label.hidden.state" \
	--control-title="Enable" \
		--control-type="button" \
		--control-group-identifier="com.finder.hidden.buttons" \
		--control-action="/usr/bin/defaults write com.apple.finder AppleShowAllFiles -bool TRUE & /usr/bin/killall Finder" \
	--control-title="Disable" \
		--control-type="button" \
		--control-group-identifier="com.finder.hidden.buttons" \
		--control-action="/usr/bin/defaults write com.apple.finder AppleShowAllFiles -bool FALSE & /usr/bin/killall Finder"

## Bug Reports & Feature Requests

Please [create an issue](https://github.com/Impedimenta/Suitcase/issues).

## Contributing

Open a PR.

## Contact

Richard Stelling ([@rjstelling](https://twitter.com/rjstelling))