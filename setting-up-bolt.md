# Setting Up Bolt

To get Bolt you need to download the compressed files, pull or clone it from its [GitHub repository](https://github.com/Chieze-Franklin/Bolt.js).

After that, navigate to the root folder \(the folder containing _bolt.js_\) and run `npm install` to install dependencies.

Download the appropriate MongoDB files into the appropriate folder in _\/sys\/bins\/mongodb_.

Ensure the path _\/sys\/data\/mongodb_ exists.

Configure Bolt as required in \/_sys\/server\/config.json_.

Run `node bolt`.

On your browser, navigate to `{{config-host}}:{{config-port}}` to start working in the Bolt environment. Using the default config values, that should be `localhost:400`.

And that's all there is to it.

