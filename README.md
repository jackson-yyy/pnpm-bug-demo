# vue-demi-bug-demo

## how to reproduce

1. run `pnpm install`
2. check `node_modules/lib/v3/index.cjs`, it is correct.
3. run `pnpm switch:vue2`
4. check `node_modules/lib/v3/index.cjs`, it becomes the source code of v2

i think it's the problem of pnpm. It use symbol link to link file.

i try to delete files under lib (`fs.unlinkSync(dest)`) before `fs.writeFileSync(dest, content, 'utf-8')`

it works perfectly now.
