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

### Importing CSS

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

### Conclusion

HTML and CSS are essential tools for creating and styling web pages. HTML is used to structure the content of the page, while CSS is used to control the appearance of the content. By learning HTML and CSS, you can create beautiful and functional websites that engage and inform your audience.
