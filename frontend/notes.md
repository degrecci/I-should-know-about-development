# Front-end

Front-end development is resposable to create user interfaces of a website, working close to back-end developers to ensure the communication between web application and server, also works with designers and product managers to ensure a good usability and a product that attends the client's demands.

## How the browser works

### Navigation

The first step when loading a web page, occurs when an user request a page by entering a URL into the address bar, clicking a link or submiting a form.

#### DNS Lookup

Thw first step is your browser make a requests for a DNS lookup, with us fuekded by a name server and return a response with an IP address. After this requests, the IP will be cached for a type. The DNS lookups ussually only need to be done once per hostname for a page Load.

#### TCP Handshake

Once we know the IP address, the browser set up a connection via TCP three-way handshake. So that way the browser and the web server can communicate.

#### TLS Negotiation (HTTPS)

This handshake determines which cypher will be user to encrypt the communications, verifies the server, and establishes that a secure connection is in place before beginning the actual transfer of data.

!["navigation example"](./navigation.jpg)

### Response

Once the connection is established, the browser sends the an initial HTTP (Get) request on behalf of the user. Once the server receives the requests, it will reply with relevant response headers and the contents of the HTML.

## REST Principles

Representation State Transfer is a group of software architecture that bring efficient, reliable and scalable systems.

To an API be considered RESTful, must be:

- Server/Client with http requests
- Stateless comunication between client/server, requests are splitted and desconected
- Store data in cache to optmize
- Informations must have a standart format.
- A system with layers that organizze types of servers.

## Web components

Suite of technologies that allows to create reusable custom elements. encapsulating away from the rest of the code.

https://developer.mozilla.org/en-US/docs/Web/API/Web_components

### Custom elements

Set of Javascript API that allows to define custom elements and behavior.

#### Types

- Customized built-in elements, from standart HTML like `HTMLImageElement` of `HTMLParagraphElement`.
- Autonomous custom elements, from the base `HTMLElement`. We can implement from scratch.

#### Example of custom element

```js
class MyCustomElement extends HTMLElement {
  static observedAttributes = ["color", "size"];

  constructor() {
    // Always call super first in constructor
    super();
  }

  connectedCallback() {
    console.log("Custom element added to page.");
  }

  disconnectedCallback() {
    console.log("Custom element removed from page.");
  }

  adoptedCallback() {
    console.log("Custom element moved to new page.");
  }

  attributeChangedCallback(name, oldValue, newValue) {
    console.log(`Attribute ${name} has changed.`);
  }
}

customElements.define("my-custom-element", MyCustomElement);
```

### Shadow-dom

Set of Javascript API to attach and encapsulate shadow DOM tree to an element. Thisd is rendered separately to the main DOM

!["Representation of shadow dom"](./shadow-dom.jpg)

#### Example

A `<video>` element, with the default browser controls exposed. All you see in the DOM is the `<video>` element, but it contains a series of buttons and other controls inside its shadow DOM. The shadow DOM spec enables you to manipulate the shadow DOM of your own custom elements.

#### "mode" Option

When, we pass an argument { mode: "open" } to attachShadow(). With mode set to "open", the JavaScript in the page is able to access the internals of your shadow DOM through the shadowRoot property of the shadow host.

#### Shadow-dom and custom elements

- Without the encapsulation provided by shadow DOM, custom elements would be impossibly fragile. It would be too easy for a page to accidentally break a custom element's behavior or layout by running some page JavaScript or CSS.
- Typically, the custom element itself is a shadow host, and the element creates multiple elements under that root, to provide the internal implementation of the element.

## SEO

## SSR

## Micro frontends pros and cons

## Accessibility

## Web Security Knowledge

### CORS

### HTTPS

### Content Security Policy

### OWASP Security Risks
