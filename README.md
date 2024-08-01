# ordinal poc

## preamble

This is a [Next.js](https://nextjs.org/) project bootstrapped with [`create-next-app`](https://github.com/vercel/next.js/tree/canary/packages/create-next-app). All the default options were selected which result in following: App Router, Tailwind CSS, TypeScript

### Customizations

While this project has been boostrapped with nextjs create-next-app, there have been some alterations made.

#### tsconfig

Additions:

- allowUnreachableCode: false
- declaration: true
- forceConsistentCasingInFileNames: true
- noFallthroughCasesInSwitch: true
- noImplicitAny: true
- noImplicitReturns: true
- pretty: true
- sourceMap: true

### Prettier

Prettier has been added to the project along with:

- eslint-config-prettier plugin ('prettier' in eslintrc extends array)
- .prettierrc config file in root directory
- .prettierignore config file in root directory

### .gitignore

Additions:

- yarn.lock
- package-lock.json

### Husky

Husky has been added to perform some checks on code:

- Prettier
- ESLint
- TypeScript compilation
- build script

Husky has some required modification to scripts within package.json:

- check-types
  - TypeScript check
- check-format
  - Prettier check
- format
  - Prettier format
- validate
  - runs all of the above in one script including the default `lint` script
- validate-and-build
  - runs all of the above in once script and finishes by running the build script
- vab
  - functions as an alias for the `validate-and-build` script

Additionally, the default Husky pre-commit script has been altered. A preset from an [online guide](https://blog.jarrodwatts.com/nextjs-eslint-prettier-husky) was used with some slight tweaks. The pre-commit hook will run the equivalent of the validate-and-build script with some helpful messaging added.

### Commitlint

Commitlint was added during the `npx -husky-init` script that starts the Husky setup process (see last section).

package additions:

- @commitlint/cli
- @commitlint/config-conventional

vscode workspace extension to add support for displaying commitlint messages within the vscode git commit window/input

### `create-next-app` Code

instances of `{' '}` have been replaced with `&nbsp;`

### GitHub Repository

"Always suggest updating pull request branches Loading" has been enabled.
A "classic" GitHub "Branch protection rule" has been added to protect the "main" branch. The following protection rules exist for "main" after these modifications:

- Require a pull request before merging
  - Require approvals (1)
- Dismiss stale pull request approvals when new commits are pushed
- Require conversation resolution before merging
- Require linear history

### .env.local

As this proof-of-concept (POC) repository is an API interaction one, a `.env.local.example` has been provided to serve as a template for provisioning sensitive information to the application at build time.

Additionally, the "Dotenv Official +Vault" vscode extension has been added to the projects Workspace Recommendations.

### packages

The following packages have been added to the project:

- react-spinners: "A collection of react loading spinners"

## Project Structure

This project has been bootstrapped with `create-next-app` with the app router configuration so, much of the structure is preordained. On top of this default structure the following changes have been made.

The addition of the following directories:

- app/api/

  In here are API routes or other API related files.

- app/components/

  The eternal resting place of all components. All components found here are designed to be later used as a design library and thus, are all loosely coupled, dumb components.

- app/utils/

  Globally required utility functions live in here.

## Guidelines

There are some design principles being followed throughout this projects code. A notable one that is difficult to enforce with utilities such as ESLint and Prettier is CSS naming semantics.

This project adheres to [BEM](https://getbem.com/introduction/) naming conventions for element class names. While Tailwind CSS has been opted into as part of the bootstrap `creat-next-app` script, all new components are designed with new CSS to reduce any external factors breaking the component library appearances. While uncommon, large design libraries publish updates with breaking changes which can create large and mandatory development efforts to be performed to unblock work once started.

## Getting Started

Install node packages and setup your IDE default formatter (vscode specific) to use "Prettier - Code formatter".

First, run the development server:

```bash
npm run dev
# or
yarn dev
# or
pnpm dev
# or
bun dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

You can start editing the page by modifying `app/page.tsx`. The page auto-updates as you edit the file.

This project uses [`next/font`](https://nextjs.org/docs/basic-features/font-optimization) to automatically optimize and load Inter, a custom Google Font.

## Learn More

To learn more about Next.js, take a look at the following resources:

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API.
- [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.

You can check out [the Next.js GitHub repository](https://github.com/vercel/next.js/) - your feedback and contributions are welcome!

## Deploy on Vercel

The easiest way to deploy your Next.js app is to use the [Vercel Platform](https://vercel.com/new?utm_medium=default-template&filter=next.js&utm_source=create-next-app&utm_campaign=create-next-app-readme) from the creators of Next.js.

Check out our [Next.js deployment documentation](https://nextjs.org/docs/deployment) for more details.
