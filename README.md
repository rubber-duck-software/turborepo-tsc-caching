This repo demos a subtlety with turborepo configuration with tsc

Currently this project is configured to run all tsc tasks in parallel (`"dependsOn": []`).

After running `pnpm i` to initialize this project, Start by running `pnpm tsc`.

Now replace line 2 in `add/index.ts` with

> return String(num1 + num2);

Run `pnpm tsc` again.
Observed that all tsc tasks succeed because they use a cached result. Desired behavior is that we would not get a cached result but instead
all tests would fail. Workaround for this is discussed in [#2855](https://github.com/vercel/turbo/issues/2855)
