# Pre-built Client

This directory should contain the built client files.

## For Users

If you cloned the repository and this folder is empty:

1. Go to the [Releases page](https://github.com/databricks-solutions/project-0xfffff/releases)
2. Download `client-build.tar.gz` from the latest release
3. Extract it here:
   ```bash
   tar -xzf client-build.tar.gz -C client/build/
   ```

## For Developers

Build the client from source:

```bash
cd client
npm install
npm run build
```

The build output will be placed in this directory.

