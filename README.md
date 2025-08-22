# Your Project's Title...
Your project's description...

## Environments
- Preview: https://main--{repo}--{owner}.aem.page/
- Live: https://main--{repo}--{owner}.aem.live/

## Documentation

Before using the aem-boilerplate, we recommand you to go through the documentation on https://www.aem.live/docs/ and more specifically:
1. [Developer Tutorial](https://www.aem.live/developer/tutorial)
2. [The Anatomy of a Project](https://www.aem.live/developer/anatomy-of-a-project)
3. [Web Performance](https://www.aem.live/developer/keeping-it-100)
4. [Markup, Sections, Blocks, and Auto Blocking](https://www.aem.live/developer/markup-sections-blocks)

## Installation

```sh
npm i
```

## Configuration Setup

This project uses external APIs that require configuration. Follow these steps to set up your configuration:

1. **Copy the configuration template:**
   ```sh
   cp config.template.js config.js
   ```

2. **Update the configuration:**
   Open `config.js` and replace the placeholder values with your actual API keys:
   
   - **Google Maps API Key**: Get your API key from the [Google Cloud Console](https://console.cloud.google.com/apis/credentials)
     - Create a new project or select an existing one
     - Enable the Maps JavaScript API
     - Create credentials (API Key)
     - **Important**: Restrict your API key to your domain for security

3. **Verify the setup:**
   The `config.js` file is gitignored to prevent committing sensitive data to version control.

## Linting

```sh
npm run lint
```

## Local development

1. Create a new repository based on the `aem-boilerplate` template and add a mountpoint in the `fstab.yaml`
1. Add the [AEM Code Sync GitHub App](https://github.com/apps/aem-code-sync) to the repository
1. Install the [AEM CLI](https://github.com/adobe/helix-cli): `npm install -g @adobe/aem-cli`
1. Start AEM Proxy: `aem up` (opens your browser at `http://localhost:3000`)
1. Open the `{repo}` directory in your favorite IDE and start coding :)