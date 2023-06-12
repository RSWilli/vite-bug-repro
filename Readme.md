# No loader configured for .glsl files

This repo serves as a bug reproduction repo for https://github.com/vitejs/vite/issues/13493

This repo contains 2 folders:

* `ui` represents the main sveltekit vite repo
* `package` represents a npm package that is included in the `ui` repo (via a local tgz install to "trick" npm)

After the following commands:

```bash
cd ui
npm i
npm run dev
```

The console should show an error similar to this:

```
  vite:deps new dependencies found: package +0ms
✘ [ERROR] No loader is configured for ".glsl" files: node_modules/package/dist/foo.glsl?raw

    node_modules/package/dist/private.js:1:17:
      1 │ import text from './foo.glsl?raw';
        ╵                  ~~~~~~~~~~~~~~~~

13:02:23 [vite] error while updating dependencies:
Error: Build failed with 1 error:
node_modules/package/dist/private.js:1:17: ERROR: No loader is configured for ".glsl" files: node_modules/package/dist/foo.glsl?raw
    at failureErrorWithLog (/home/willi/projects/vite-bug-repro/ui/node_modules/esbuild/lib/main.js:1636:15)
    at /home/willi/projects/vite-bug-repro/ui/node_modules/esbuild/lib/main.js:1048:25
    at /home/willi/projects/vite-bug-repro/ui/node_modules/esbuild/lib/main.js:1512:9
    at process.processTicksAndRejections (node:internal/process/task_queues:95:5)
  vite:optimize-deps load /home/willi/projects/vite-bug-repro/ui/node_modules/.vite/deps/package.js +530ms
```