# Dialog
Get all the main dialog boxes dynamically and responsively


## Which is?
It is a responsive and cross-browser dialog system that facilitates the creation of modals that define a new section of independent content on a page.


## Interfaces
```javascript
// Constructor
Dialog(
    shadowRootMode?: ('open' | 'closed') = 'open', // A string specifying the encapsulation mode for the shadow DOM tree
    delegatesFocus?: boolean = false, // When a non-focusable part of the shadow DOM is clicked, the first focusable part is given focus
    style?: string = ''
)
```

```javascript
// Getters
dialogs(): string[] // List reverted of created dialog ID's

shadowRootMode(): 'open' | 'closed'

delegatesFocus(): boolean

style(): string
```

```javascript
// Setters
shadowRootMode(arg?: ('open' | 'closed') = 'open'): void

delegatesFocus(arg?: boolean = false): viod

style(arg?: string = ''): viod
```

```javascript
// Methods
alert(
    content: string | HTMLElement,
    callback: (flag: boolean, main: HTMLElement) => boolean | void,
    {
        title = '',
        style = '',
        script = () => {},
        persistent = false, // If true, the dialog does not close on the click outside or on the press of the Escape, Enter and Space
        textResolve = 'Ok',
        onClose = () => {}
    }: {
        title?: string,
        style?: string,
        script?: (main: HTMLElement) => void,
        persistent?: boolean,
        textResolve?: string,
        onClose?: (key: string) => void
    } = {}
): string

close(key?: (string | null) = null): boolean | null // If a key is not inserted, the most recent dialog will be removed from the stacks

confirm(
    content: string | HTMLElement,
    callback: (flag: boolean, main: HTMLElement) => boolean | void,
    {
        title = '',
        style = '',
        script = () => {},
        persistent = false, // If true, the dialog does not close on the click outside or on the press of the Escape, Enter and Space
        textResolve = 'Ok',
        textReject = 'No',
        onClose = () => {}
    }: {
        title?: string,
        style?: string,
        script?: (main: HTMLElement) => void,
        persistent?: boolean,
        textResolve?: string,
        textReject?: string,
        onClose?: (key: string) => void
    } = {}
): string

notify(
    content: string | HTMLElement,
    {
        title = '',
        footer = '',
        style = '',
        script = () => {},
        persistent = false,
        discreet = true, // If true, the dialog will appear in the lower right corner, otherwise, in the upper central part
        duration = null, // If a time is not provided, it will be calculated based on the total number of characters, although the minimum time is 3000ms
        onClose = () => {}
    }: {
        title?: string,
        footer?: string,
        style?: string,
        script?: (main: HTMLElement, footer: HTMLElement) => void,
        persistent?: boolean,
        discreet?: boolean,
        duration?: number,
        onClose?: (key: string) => void
    } = {}
): string

popUp(
    content: string | HTMLElement,
    {
        title = '',
        footer = '',
        style = '',
        script = () => {},
        persistent = false, // If true, the dialog does not close on the click outside or on the press of the Escape
        fullScreen = false, // If true, the dialog will fill the entire window and the close button will change
        onClose = () => {}
    }: {
        title?: string,
        footer?: string,
        style?: string,
        script?: (main: HTMLElement, footer: HTMLElement) => void,
        persistent?: boolean,
        fullScreen?: boolean,
        onClose?: (key: string) => void
    } = {}
): string

show(
    content: string | HTMLElement,
    {
        title = '',
        footer = '',
        style = '',
        script = () => {},
        persistent = false, // If true, the dialog does not close on the click outside or on the press of the Escape
        fullScreen = false, // If true, the dialog will fill the entire window
        onClose = () => {}
    }: {
        title?: string,
        footer?: string,
        style?: string,
        script?: (main: HTMLElement, footer: HTMLElement) => void,
        persistent?: boolean,
        fullScreen?: boolean,
        onClose?: (key: string) => void
    } = {}
): string
```

## How to use
```javascript
var dialog = new Dialog();

var popUpKey = dialog.popUp(
    '<h1>Here will be the content to be displayed</h1>',
    {
        title: 'popUp example',
        footer: '<a href="https://github.com/JadsonLucena/Dialog" target="_blank">Dialog</a>',
        style: 'a { text-decoration: none; }',
        script: (main, footer) => {

            main.querySelector('h1').onclick = () => {

                let notifyKey = dialog.notify('Here will be the content to be displayed', {
                    duration: 5000
                });

            };

        },
        fullScreen: true
    }
);

var confirmKey = dialog.confirm(
    '<label><input type="checkbox"> select to proceed</label>',
    (value, main) => {

        if (value && !main.querySelector('input').checked)
            return false;

    },
    {
        persistent: true,
        textResolve: 'Next',
        textReject: 'Cancel'
    }
);

setTimeout(() => {

    dialog.dialogs.forEach(key => dialog.close(key));

}, 20000);
```

> Every method returns the key for the modal created\
> If the close method returns null, then the dialog was not found
