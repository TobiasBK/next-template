This is a [Next.js](https://nextjs.org/) project bootstrapped with [`create-next-app`](https://github.com/vercel/next.js/tree/canary/packages/create-next-app).

## Getting Started

First, run the development server:

```bash
npm run dev
# or
yarn dev
# or
pnpm dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

You can start editing the page by modifying `pages/index.tsx`. The page auto-updates as you edit the file.

[API routes](https://nextjs.org/docs/api-routes/introduction) can be accessed on [http://localhost:3000/api/hello](http://localhost:3000/api/hello). This endpoint can be edited in `pages/api/hello.ts`.

The `pages/api` directory is mapped to `/api/*`. Files in this directory are treated as [API routes](https://nextjs.org/docs/api-routes/introduction) instead of React pages.

This project uses [`next/font`](https://nextjs.org/docs/basic-features/font-optimization) to automatically optimize and load Inter, a custom Google Font.

## Learn More

To learn more about Next.js, take a look at the following resources:

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API.
- [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.

You can check out [the Next.js GitHub repository](https://github.com/vercel/next.js/) - your feedback and contributions are welcome!

## Deploy on Vercel

The easiest way to deploy your Next.js app is to use the [Vercel Platform](https://vercel.com/new?utm_medium=default-template&filter=next.js&utm_source=create-next-app&utm_campaign=create-next-app-readme) from the creators of Next.js.

Check out our [Next.js deployment documentation](https://nextjs.org/docs/deployment) for more details.

# Dev setup notes

### Engine locking

- .nvmrc - which version of Node is used
- .npmrc - which package manager is used

### Code format

- eslint - For best practices on coding standard

- prettier - For auto formatting of code files

To add prettier:

`yarn add -D prettier`

Then create two files in the root directory:

- .prettierrc
- .prettierignore

Then add `"prettier": "prettier --write ."` script to `package.json`.

Now run `yarn prettier`.

### Git hooks

Use Husky:

`yarn add -D husky`

`npx husky install`

Then add this to package.json scripts:

`"prepare": "husky install"`

To create a hook, run:

`npx husky add .husky/pre-commit "yarn lint"`

This says for our commit to succeed, the yarn lint script must first run and work.

Another hook:

`npx husky add .husky/pre-push "yarn build"`

### Add linter to commit messages

`yarn add -D @commitlint/config-conventional @commitlint/cli`

Then setup this:

`commitlint.config.js`

Then enable commitlint with Husky:

`npx husky add .husky/commit-msg 'npx --no -- commitlint --edit "$1"`

Sometimes that command doesn't work. Try other commands, like:
`npx husky add .husky/commit-msg \"npx --no -- commitlint --edit '$1'\"`

or

`npx husky add .husky/commit-msg "npx --no -- commitlint --edit $1"`

### VS code setup

Create a `.vscode` directory in the root. Add a file to the directory called `settings.json`.

List values you want to override defualt VS code settings. This allows these settings to only apply to this project.

### Debugging

Add a `launch.json` file to the `vscode` directory.
Here setup debugging environment.

### Environment variables

To manage environment variables across different environmets, install cross-env.

`yarn add -D cross-env`

### Storybook

Finally, storybook can be added depending on the type of project.

Storybook setup problems with are common. Reference [this thread](https://github.com/storybookjs/storybook/issues/18319).
