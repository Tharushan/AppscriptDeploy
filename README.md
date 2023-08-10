# Google Appscript Deploy

[![clasp](https://img.shields.io/badge/built%20with-clasp-4285f4.svg)](https://github.com/google/clasp)

A repo that automatically deploys to Google Appscript using clasp and Github Actions.

## Setup

1. Install [clasp](https://github.com/google/clasp) globally using npm:

```bash
npm install -g @google/clasp
```

2. Login to clasp:

```bash
clasp login
```

3. Create two new Google Appscripts project (so you can have one for development and one for production):

```bash
clasp create --type standalone --title "[DEV] Google Appscript Deploy" # This will create a new project and a .clasp.json file
mv .clasp.json .clasp.dev.json # Rename the .clasp.json file to .clasp.dev.json

# Repeat the above steps for production
clasp create --type standalone --title "[PROD] Google Appscript Deploy"
mv .clasp.json .clasp.prod.json
```

Don't forget to update `rootDir` in those .clasp files to point to the correct directory and file extension. (e.g. `rootDir: "src"` and `fileExtension: "ts"`)

-> See [clasp's Typescript doc](https://github.com/google/clasp/blob/master/docs/typescript.md) to see what can be done (for example, Google Appscript does not support ES modules.)

## Github Actions Setup :
- Copy content from `~/.clasprc.json` after using `clasp login` and add it to `CLASPRC` secret in github

## Usage

You can now start developing your Google Appscript project locally and use Github Actions to automatically deploy to Google Appscript.

If you want to deploy manually, you can use the following commands:

```bash
clasp push
# Then to open and execute the script in the browser:
clasp open
```

But you will need to have a `.clasp.json` file in your project root directory. (You can copy the `.clasp.dev.json` file that you generated and rename it to `.clasp.json` for example.)