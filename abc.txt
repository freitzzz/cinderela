# github-upsert

Upserts file into a GitHub repo

![npm version](https://badgen.net/npm/v/@web-pacotes/github-upsert) ![npm total downloads](https://badgen.net/npm/dt/@web-pacotes/github-upsert) ![bundlephobia bundle size](https://badgen.net/bundlephobia/min/@web-pacotes/github-upsert)

---

## How to use

To use this package, you will need a Personal Access Token (PAT) with read/write permissions for the repository you want to upload files in. Create one by going to: `Settings > Developer Settings > Personal Access Tokens`.

```typescript
import { default as upsert, GitHubRepository } from 'github-upsert';

// You can grab your personal access token in: Settings > Developer Settings > Personal Access Tokens
const repo = <GitHubRepository>{
	name: 'your-github-repo',
	owner: 'your-github-username',
	pat: 'your-github-pat'
};

const data = new TextEncoder().encode('Hello world!');
const path = 'README.md';

// Upload it
const result = await upsert(repo, data, path);

// Hoooraaaay! It should print the SHA checksum of your file!
console.log(result);
```

Additionally, you can upsert files within the CLI. Execute the following command for more info:

```bash
github-upsert --help
```

## Features

- Uploads/updates a file in a GitHub repository
- Uses native fetch lib for HTTP requests

## Missing features

- Support for web/lib fetch

---

## Scripts

- `npm run build` to transpile and bundle files in `.cjs`, `.js`, `.d.ts` and respective source-maps
- `npm run start` to run the example project with `swc` compilation

- `npm run test` to run the unit tests
- `npm run lint` to analyze and lint the project
- `npm run format` to format the project based on lint feedback

- `npm run docs` to generate docs site
- `npm run docs:publish` to generate docs site and publish it to GitHub Pages

- `npm run release` to create the temporary changesets file
- `npm run publish` to publish the package to NPM

## Hooks

This repository is configured with client-side Git hooks that automatically format + lint the codebase before each push. You can install it by running the following command:

```bash
./hooks/INSTALL
```

## Automatically Publishing to NPM

To automatically publish the package to NPM, you will need to grab a token of the publisher account for CI usage, and set it as a repository secret in GitHub under the `NPM_TOKEN` identifier.

---

### Bugs and Contributions

Found any bug (including typos) in the package? Do you have any suggestion
or feature to include for future releases? Please create an issue via
GitHub in order to track each contribution. Also, pull requests are very
welcome!
