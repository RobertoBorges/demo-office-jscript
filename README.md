# Office Addin without SSL requirement

This is a sample project that demonstrates how to create an Office Add-in that does not require SSL. This is useful for development and testing purposes.

On top of that this will not require elevated permissions to run the add-in.

For production, it is recommended to use SSL.

Specially change the followin session on your webpack.config.js file to allow the add-in to run wit SSL:

```javascript
    devServer: {
      headers: {
        "Access-Control-Allow-Origin": "*",
      },
      server: {
        type: "https",
        options: env.WEBPACK_BUILD || options.https !== undefined ? options.https : await getHttpsOptions(),
      },
      port: process.env.npm_package_config_dev_server_port || 3000,
    },
```
