# Best developer experience (DevX)

A curated list of the best developer experience and what makes it so great.

# Table of contents

- [What makes DevX great](#what-makes-devx-great)
- [Hall of fame](#hall-of-fame)
- [Best Practices](#best-practices)

## What makes DevX great
- **Stability**: The tool is reliable and works when needed. If bugs occur, they are fixed as fast as possible.
- **Ease of Use**: The tool can be used intuitively, you can find all necessary information and there are smart defaults.
- **Clarity**: The tool displays all necessary information in an understandable way and provides full visibility of the consequences of any action.
- **Integrability**: The tool works with other tools in a meaningful way and provides necessary interfaces for this.


## Hall of fame
- [Clerk](https://clerk.com/) - Authentication ([Go](#clerk))
- [Supabase](https://supabase.com/) - Database, authentication, realtime ([Go](#supabase))
- [Railway](https://railway.app/) - Deployment ([Go](#railway))
- [Next.js](https://nextjs.org/) - Framework ([Go](#nextjs))
- [Tailwind CSS](https://tailwindcss.com/) - Styling ([Go](#tailwind-css))
- [Shadcn](https://ui.shadcn.com/) - UI ([Go](#shadcn))
- [NextUI](https://nextui.org/) - UI ([Go](#nextui))
- [Vercel](https://vercel.com/) - Deployment and hosting ([Go](#vercel))
- [Trigger.dev](https://trigger.dev/) - Workflow automation ([Go](#triggerdev))
- [Upstash](https://upstash.com/) - Serverless data platform ([Go](#upstash))
- [OpenPanel](https://openpanel.dev/) - Analytics ([Go](#openpanel))
- [Resend](https://resend.com/) - Email service ([Go](#resend))
- [Novu](https://novu.co/) - Notification infrastructure ([Go](#novu))
- [Expo](https://expo.dev/) - React Native framework ([Go](#expo))
- [v0](https://v0.dev/) - AI UI generator ([Go](#v0))
- [Cursor](https://cursor.so/) - Code editor ([Go](#cursor))
- [AppKit](https://appkit-lab.reown.com/) - Onchain UI kit ([Go](#appkit))
- [Wagmi](https://wagmi.sh/) - Onchain React library ([Go](#wagmi))
- [Privy](https://www.privy.io/) - Wallet authentication ([Go](#privy))

Add to the list by writing a PR. Include the tool, a short description and why it is great.


## Best Practices
Case studies and best practices on how to make DevX great.

### [Clerk](https://clerk.com/)
Clerk is a developer experience platform for authentication.
#### Ease of use
Clerk creates pixel-perfect UI for authentication and allows to easily customize it.

The `<ClerkProvider>` component is the entry point of Clerk into an app. It wraps an app and provides the Clerk context to all components within the app.

#### Sample props for `<ClerkProvider>`

| Prop                          | Type                                      | Description                                                                                       |
|-------------------------------|-------------------------------------------|---------------------------------------------------------------------------------------------------|
| afterMultiSessionSingleSignOutUrl | string                                    | The full URL or path to navigate to after signing out from a currently active account in a multi-session app. |
| afterSignOutUrl               | string                                    | The full URL or path to navigate to after a successful sign-out.                                  |
| appearance?                   | Appearance \| undefined                   | Optional object to style your components.                                                         |
| clerkJSUrl?                   | string                                    | Define the URL that @clerk/clerk-react should hot-load @clerk/clerk-js from.                      |
| clerkJSVariant?               | string                                    | If your web application only uses Control components, you can set this value to headless and load a minimal ClerkJS bundle for optimal page performance. |
| publishableKey                | string                                    | The Clerk publishable key for your instance.                                                      |
| routerPush?                   | (to: string) => Promise<unknown> \| void  | A function which takes the destination path as an argument and performs a "push" navigation.      |
| signInUrl                     | string                                    | This URL will be used for any redirects that might happen and needs to point to your primary application on the client-side. |
| signUpUrl                     | string                                    | This URL will be used for any redirects that might happen and needs to point to your primary application on the client-side. |
| supportEmail?                 | string                                    | Optional support email for display in authentication screens.                                     |
| telemetry?                    | false \| { disabled?: boolean; debug?: boolean } \| undefined | Controls whether or not Clerk will collect telemetry data.                                        |
| nonce?                        | string                                    | This nonce value will be passed through to the @clerk/clerk-js script tag.                        |
| sdkMetadata?                  | { name: string; version: string; environment?: string } | Contains information about the SDK that the host application is using.                            |
| standardBrowser?              | boolean                                   | By default, ClerkJS is loaded with the assumption that cookies can be set (browser setup).        |
| selectInitialSession?         | (client: ClientResource) => ActiveSessionResource \| null | By default, the last active session is used during client initialization. This option allows you to override that behavior. |
| touchSession?                 | boolean                                   | By default, the Clerk Frontend API touch endpoint is called during page focus to keep the last active session alive. This option allows you to disable this behavior. |
| initialState?                 | InitialState                              | Provide an initial state of the Clerk client during server-side rendering.  

The `<SignIn />` component renders a UI for signing in users. The functionality of the `<SignIn />` component is controlled by the instance settings you specify in your Clerk Dashboard.

#### Sample props for `<SignIn>`

| Prop                          | Type                                      | Description                                                                                       |
|-------------------------------|-------------------------------------------|---------------------------------------------------------------------------------------------------|
| appearance?                   | undefined                   | Optional object to style your components.                                                         |
| routing                       | 'hash' \| 'path' \| 'virtual'            | The routing strategy for your pages. Defaults to 'path' in Next.js and Remix applications. Defaults to 'hash' for all other SDKs. |
| path                          | string                                    | The path where the component is mounted on when routing is set to path. Ignored in hash- and virtual-based routing. For example: /sign-in. |
| forceRedirectUrl?             | string                                    | If provided, this URL will always be redirected to after the user signs in. Takes priority over deprecated props such as afterSignInUrl and redirectUrl. |
| transferable?                 | boolean                                   | Indicates whether or not sign in attempts are transferable to the sign up flow. Defaults to true. When set to false, prevents opaque sign ups when a user attempts to sign in via OAuth with an email that doesn't exist. |

#### Appearance
Clerk provides a way to customize the appearance of its components using the appearance prop.

The appearance prop can be applied to <ClerkProvider> to share styles across every component, or individually to any of the Clerk components.

#### Sample `appearance` props

| Prop        | Type                | Description                                                                                       |
|-------------|---------------------|---------------------------------------------------------------------------------------------------|
| baseTheme?  | BaseTheme \| BaseTheme[] | A theme used as the base theme for the components. For more information, see Themes.              |
| layout?     | Layout              | Configuration options that affect the layout of the components, allowing customizations that are hard to implement with just CSS. For more information, see Layout. |
| variables?  | Variables           | General theme overrides. These styles will be merged with our base theme. Can override global styles like colors, fonts, etc. For more information, see Variables. |
| elements?   | Elements            | Fine-grained theme overrides. Useful when you want to style specific elements or elements that are under a specific state. For more information, see the Customize elements of a Clerk component section. |

Clerk also provides pre-built [themes](https://clerk.com/docs/customization/themes). You can use them by installing `npm install @clerk/themes`.

And you can use a theme by passing it to the `appearance` prop:
``` import { ClerkProvider } from '@clerk/nextjs'
import { dark } from '@clerk/themes'

export default function RootLayout({ children }: { children: React.ReactNode }) {
  return (
    <ClerkProvider
      appearance={{
        baseTheme: dark,
      }}
    >
      <html lang="en">
        <body>{children}</body>
      </html>
    </ClerkProvider>
  )
}
```



