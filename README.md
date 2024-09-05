# Fetch API Usage Guide

This repository provides a comprehensive guide to using the Fetch API in modern web development. The Fetch API offers a powerful and flexible way to make HTTP requests from browsers.

## Table of Contents

- [Introduction](#introduction)
- [Basic Usage](#basic-usage)
- [Advanced Features](#advanced-features)
- [Error Handling](#error-handling)
- [Examples](#examples)
- [Browser Support](#browser-support)
- [Contributing](#contributing)
- [License](#license)

## Introduction

The Fetch API provides an interface for fetching resources (including across the network). It is a more powerful and flexible replacement for `XMLHttpRequest`.

## Basic Usage

Here's a simple example of using Fetch:

```javascript
fetch("https://api.example.com/data")
  .then((response) => response.json())
  .then((data) => console.log(data))
  .catch((error) => console.error("Error:", error));
```

## Advanced Features

### POST Request

```javascript
fetch("https://api.example.com/posts", {
  method: "POST",
  headers: {
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
    title: "foo",
    body: "bar",
    userId: 1,
  }),
})
  .then((response) => response.json())
  .then((data) => console.log(data));
```

### Handling Response

```javascript
fetch("https://api.example.com/data")
  .then((response) => {
    if (!response.ok) {
      throw new Error("Network response was not ok");
    }
    return response.json();
  })
  .then((data) => console.log(data))
  .catch((error) => console.error("Error:", error));
```

## Error Handling

It's important to handle errors properly when using Fetch:

```javascript
async function fetchData(url) {
  try {
    const response = await fetch(url);
    if (!response.ok) {
      throw new Error(`HTTP error! status: ${response.status}`);
    }
    const data = await response.json();
    return data;
  } catch (error) {
    console.error("There was a problem with the fetch operation:", error);
  }
}
```

## Examples

Check out our [examples directory](./examples) for more detailed usage scenarios.

## Browser Support

Fetch is supported in all modern browsers. For older browsers, you might need to use a polyfill.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details.
