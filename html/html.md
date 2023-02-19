# HTML and CSS

HTML and CSS are two of the fundamental languages used to create and style web pages. HTML stands for Hypertext Markup Language, and CSS stands for Cascading Style Sheets.

### HTML

HTML is used to structure the content of a web page. It consists of a series of tags and elements that define the different parts of the page. For example, the <html> tag marks the beginning and end of the HTML document, the <head> tag contains information about the page that isn't displayed on the page itself (such as the page title), and the <body> tag contains the main content of the page.

Here's an example of a basic HTML document:

```html
<!DOCTYPE html>
<html>
  <head>
    <title>My Web Page</title>
  </head>
  <body>
    <h1>Welcome to my web page</h1>
    <p>This is some example text.</p>
  </body>
</html>
```

In this example, the `<!DOCTYPE html>` tag tells the web browser that the document is an HTML document. The `<html>` tag marks the beginning of the HTML document, and the `<head>` and `<body>` tags define the different parts of the page. The `<title>` tag sets the title of the page, which appears in the browser's title bar.

The `<h1>` tag defines a heading, and the `<p>` tag defines a paragraph. There are many other HTML tags that can be used to structure a web page, including lists, tables, forms, and more.

### CSS

CSS is used to style the content of a web page. It allows you to control the appearance of HTML elements, such as the color, font, and layout. CSS uses a series of rules that define how different elements should be styled.

Here's an example of a basic CSS rule:

```css
h1 {
  color: blue;
  font-size: 24px;
}
```

In this example, the h1 selector targets all `<h1>` tags on the page. The color property sets the color of the text to blue, and the `font-size` property sets the font size to 24 pixels. There are many other CSS properties that can be used to style HTML elements, including background color, border, padding, and more.

### Importing css

To import a CSS file into an HTML document, you can use the `<link>` tag. The `<link>` tag is a self-closing tag that should be placed in the `<head>` section of your HTML document. Here's an example of how to link to a CSS file:

```html
<!DOCTYPE html>
<html>
  <head>
    <title>My Web Page</title>
    <link rel="stylesheet" type="text/css" href="styles.css" />
  </head>
  <body>
    <h1>Welcome to my web page</h1>
    <p>This is some example text.</p>
  </body>
</html>
```

In this example, the `<link>` tag is used to link to a CSS file named `styles.css`. The `rel` attribute specifies the relationship between the HTML document and the linked resource (in this case, a stylesheet), and the `type` attribute specifies the MIME type of the linked resource. The `href` attribute specifies the location of the linked resource (in this case, the filename of the CSS file).

By linking to an external CSS file, you can keep your HTML and CSS code separate and more organized. This also allows you to reuse the same stylesheet across multiple pages of your website, making it easier to maintain a consistent design throughout your site.

### HTML DOM

The Document Object Model (DOM) is a programming interface for HTML and XML documents. It represents the structure of a web page as a tree-like structure, where each node in the tree represents an element, attribute, or text node in the document. The DOM allows scripts to access and manipulate the content and structure of a web page in a dynamic way.

When a web page is loaded into a web browser, the browser creates a DOM tree representing the page's content. This tree consists of a series of nodes, each of which represents an element, attribute, or text node in the document. The nodes are organized into a hierarchical structure, with the <html> element at the root of the tree, and child nodes representing the various elements and content of the page.

Scripts can use the DOM API to interact with this tree, and manipulate the content and structure of the web page. For example, you can use the DOM to:

- Access and modify the content of an element
- Create new elements and add them to the page
- Remove elements from the page
- Modify the style and layout of elements
- Respond to user interactions, such as clicks and key presses

The DOM is a key component of modern web development, and is used extensively in client-side scripting languages such as JavaScript. By using the DOM to manipulate the content and structure of a web page, you can create dynamic, interactive web applications that respond to user input and provide a rich, engaging user experience.

Here's an example of a simple web page, and how it might be represented as a DOM tree:

```html
<!DOCTYPE html>
<html>
  <head>
    <title>My Web Page</title>
  </head>
  <body>
    <h1>Welcome to my web page</h1>
    <p>This is some example text.</p>
    <img src="myimage.jpg" alt="My Image" />
    <button onclick="alert('Hello, world!')">Click me</button>
  </body>
</html>
```

In this example, the root of the DOM tree is the `<html>` element. This element has two child nodes: the `<head>` element, and the `<body>` element.

The `<head>` element contains a `<title>` element, which represents the title of the web page. The `<body>` element contains several child elements, including an `<h1>` element, a <p> element, an `<img>` element, and a `<button>` element.

Each of these elements, and their attributes and content, are represented as nodes in the DOM tree. For example, the text "Welcome to my web page" is represented as a text node, while the `src` and `alt` attributes of the `<img>` element are represented as attribute nodes.

Scripts can use the DOM API to access and manipulate these nodes. For example, you could use JavaScript to change the text of the `<h1>` element:

```javaScript
document.querySelector('h1').textContent = 'Hello, world!';
```

In this example, we use the `document.querySelector` method to find the first `<h1>` element on the page, and then set its `textContent` property to "Hello, world!". This will update the text displayed on the page to say "Hello, world!" instead of "Welcome to my web page".

By using the DOM API, we can make dynamic changes to the content and structure of the web page, creating interactive and engaging user experiences.
