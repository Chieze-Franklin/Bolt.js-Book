# Scoped Apps

[npm](https://npmjs.org) allows packages to be [scoped](https://docs.npmjs.com/misc/scope). The scope of a package serves as a form of namespace, and helps to avoid name conflicts amongs modules with popular names. The scope of the package is usually the name of the company that owns that package.

When Bolt downloads a scoped app it proceeds to _flattening_ out the app before actually installing it. For instance, if there is a scoped app named _@company/app_, the app will be downloaded into _node\_modules/@company/app_. Bolt cannot directly work with scoped apps, so it flattens it to _node\_modules/app@company_. The _`name`_ field of the _package.json_ also gets changed from _@company/app_ to _app@company_. After this flattening is done, Bolt then installs the app as usual.

Note that to download a scoped app, use its original name _@company/app_.

Currently Bolt cannot read the README file of scoped apps, and throws an error after installation \(even though the app installs properly\).

