# Visual Assets centralization for Pryv.io 

This repository contains visual assets for the Open Pryv platform. 

The file `index.json` is exposed to various applications and libraries by the [Service Information](https://api.pryv.com/reference/#service-info) API call under the `assets.definitions` property.

This structure is a proposal that can and should be extended depending on the needs of each Pryv.io deployment. 

## Usage

For the Open Pryv.io platform, we deploy the assets using github gh-pages.

The URL of the file `index.json` is declared in the Service Information configuration part of **Pryv.io**'s platform settings. 

Example: https://reg.pryv.me/service/infos

```json
{
  ...
  "assets": {
  	"definitions": "https://pryv.github.io/assets-pryv.me/index.json"
	}
}
```



## Default structure 

### index.json

- `baseUrl` should be used to resolve all relative ressources path (if not starting with `http(s)://`). If `undefined` or set to `null`, `baseUrl` should be treated as the location of the `index.json` file. The logic is similar to `base href` attribute in HTML pages.
- `favicon` should have at least a `default` property exposing an `.ico` file.
- `css` should have at least a `default` property exposing a `.css` file.
- `{app-name}` exposes customs assets per application.
- `lib-js`: [./lib-js](lib-js) as example of App specific definitions
- `app-web-auth3`:  [./app-web-auth3](app-web-auth3) as example of App specific definitions

```json
{ 
  "baseUrl": null,
  "favicon": {
    "default": "favicon.ico"
  },
  "css": {
    "default": "default.css"
  },
  "lib-js": {
    "buttonSignIn": {
      "css": "lib-js/buttonSignIn.css",
      "html": "lib-js/buttonSignIn.html",
      "messages": "lib-js/buttonSignInMessages.json"
    }
  }
}
```
