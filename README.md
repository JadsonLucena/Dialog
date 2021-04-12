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
): Dialog
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
shadowRootMode(arg?: ('open' | 'closed') = 'open')

delegatesFocus(arg?: boolean = false)

style(arg?: string = '')
```

```javascript
// Methods
alert(
    content: string | HTMLElement,
    callback: (flag: boolean, main: HTMLElement) => boolean | void,
    {
        title?: string,
        style?: string,
        script?: (main: HTMLElement) => void,
        persistent?: boolean = false,
        textResolve?: string = 'Ok'
    }?
): number

close(key?: number): boolean | null // If a key is not inserted, the most recent dialog will be removed from the stacks

confirm(
    content: string | HTMLElement,
    callback: (flag: boolean, main: HTMLElement) => boolean | void,
    {
        title?: string,
        style?: string,
        script?: (main: HTMLElement) => void,
        persistent?: boolean = false,
        textResolve?: string = 'Ok',
        textReject?: string = 'No'
    }?
): number

notify(
    content: string | HTMLElement,
    {
        title?: string,
        footer?: string,
        style?: string,
        script?: (main: HTMLElement, footer: HTMLElement) => void,
        persistent?: boolean = false,
        discreet?: boolean = true, // If true, the dialog will appear in the lower right corner, otherwise, in the upper central part
        duration?: number // If a time is not provided, it will be calculated based on the total number of characters, although the minimum time is 3000ms
    }?
): number

popUp(
    content: string | HTMLElement,
    {
        title?: string,
        footer?: string,
        style?: string,
        script?: (main: HTMLElement, footer: HTMLElement) => void,
        persistent?: boolean = false, // if true, the dialog does not close on the click outside or on the press of the esc
        fullScreen?: boolean = false // If true, the dialog will fill the entire window and the close button will change
    }?
): number

show(
    content: string | HTMLElement,
    {
        title?: string,
        footer?: string,
        style?: string,
        script?: (main: HTMLElement, footer: HTMLElement) => void,
        persistent?: boolean = false,
        fullScreen?: boolean = false // If true, the dialog will fill the entire window
    }?
): number
```