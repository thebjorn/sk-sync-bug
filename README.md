The following message is printed (multiple times if using a monorepo):
> If bundling, conditions should include development or production. If not bundling, conditions or NODE_ENV should include development or production. See https://www.npmjs.com/package/esm-env for tips on setting conditions in popular bundlers and runtimes.

Normally you get this when running `pnpm build` (or `turbo build` in my case) in CI, but you can very simply reproduce it like so:
```bash
> sv create sk-sync-bug
┌  Welcome to the Svelte CLI! (v0.6.9)
│
◇  Which template would you like?
│  Svelte library
│
◇  Add type checking with Typescript?
│  Yes, using Typescript syntax
│
◆  Project created
│
◇  What would you like to add to your project? (use arrow keys / space bar)
│  none
│
◇  Which package manager do you want to install dependencies with?
│  pnpm
│
◆  Successfully installed dependencies
│
◇  Project next steps ─────────────────────────────────────────────────────╮
│                                                                          │
│  1: cd sk-sync-bug                                                       │
│  2: git init && git add -A && git commit -m "Initial commit" (optional)  │
│  3: pnpm dev --open                                                      │
│                                                                          │
│  To close the dev server, hit Ctrl-C                                     │
│                                                                          │
│  Stuck? Visit us at https://svelte.dev/chat                              │
│                                                                          │
├──────────────────────────────────────────────────────────────────────────╯
│
└  You're all set!

> cd sk-sync-bug
sk-sync-bug❱ pnpm up *                                                                    
 WARN  2 deprecated subdependencies found: glob@8.1.0, inflight@1.0.6
Already up to date
Progress: resolved 118, reused 77, downloaded 0, added 0, done
Done in 3s

sk-sync-bug❱ pnpm i                                                                       
 WARN  2 deprecated subdependencies found: glob@8.1.0, inflight@1.0.6
Packages: +8
++++++++
Progress: resolved 119, reused 77, downloaded 0, added 8, done
node_modules/.pnpm/@sveltejs+kit@2.15.0_@sveltejs+vite-plugin-svelte@5.0.3_svelte@5.15.0_vite@6.0.5__svelte@5.15.0_vite@node_modules/.pnpm/@sveltejs+kit@2.15.0_@sveltejs+vite-plugin-svelte@5.0.3_svelte@5.15.0_vite@6.0.5__svelte@5.15.0_vite@6.0.5/node_modules/@sveltejs/kit: Running postinstall script, done in 988ms

devDependencies:
- @sveltejs/vite-plugin-svelte 4.0.4
+ @sveltejs/vite-plugin-svelte 5.0.3
- vite 5.4.11
+ vite 6.0.5

Done in 2.4s
sk-sync-bug> pnpm svelte-kit sync                                                                         
If bundling, conditions should include development or production. If not bundling, conditions or NODE_ENV should include development or production. See https://www.npmjs.com/package/esm-env for tips on setting conditions in popular bundlers and runtimes.
```