# CAPTCHA Solver Web Application

## Summary

This static web application is designed to solve CAPTCHA images from a specific URL by utilizing advanced image processing techniques. It processes the image located at `https://yourdomain.com/image.png` and displays the interpreted text of the CAPTCHA. The application uses a default cached sample for demonstration purposes.

## Setup

To deploy this application on GitHub Pages, follow these steps:

1. **Fork the Repository**: Start by forking the repository containing this application to your own GitHub account.

2. **Clone the Repository**: Clone the forked repository to your local machine.
   ```bash
   git clone https://github.com/yourusername/captcha-solver.git
   ```

3. **Create a New Branch**: Navigate to your directory and create a new branch.
   ```bash
   cd captcha-solver
   git checkout -b gh-pages
   ```

4. **Push to GitHub**: Push the new branch to GitHub.
   ```bash
   git push -u origin gh-pages
   ```

5. **Activate GitHub Pages**: Go to your repository settings on GitHub, under the "Pages" section, choose the `gh-pages` branch as the source.

Once these steps are complete, your application will be accessible at `https://yourusername.github.io/captcha-solver`.

## Usage

### Accessing the Page

The web application can be accessed through the URL: `https://yourusername.github.io/captcha-solver`.

### Query Parameters

- You can specify a different image source via a query parameter: `?imageUrl=https://example.com/image.png`.

### Key Features

- **CAPTCHA Processing**: The application automatically processes the CAPTCHA image from the default URL or a specified URL via query parameter.
- **Text Display**: The interpreted CAPTCHA text is displayed on the webpage for user review.
  
To use an alternate image, use:
```
https://yourusername.github.io/captcha-solver?imageUrl=https://example.com/image.png
```

## Code Explanation

### Technical Overview

This application is structured using basic HTML and JavaScript. It includes a simple frontend script that fetches the image, processes it, and displays the solved text.

### Key Libraries

- **Tesseract.js**: This JavaScript library is used for optical character recognition (OCR), enabling the conversion of images to text.

### Important Algorithms

- **Image Fetching**: Utilizes `fetch` API to obtain the CAPTCHA image from a given URL.
- **OCR Processing**: Tesseract.js is employed to decode the textual content of the CAPTCHA from the image.

```html
<script src="https://cdn.jsdelivr.net/npm/tesseract.js"></script>
```

```javascript
fetch('https://yourdomain.com/image.png')
  .then(response => response.blob())
  .then(blob => {
    Tesseract.recognize(blob, 'eng', {
      logger: m => console.log(m)
    }).then(({ data: { text } }) => {
      document.getElementById('captcha-result').textContent = text;
    });
  });
```

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.