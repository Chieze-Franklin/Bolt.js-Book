# tags

Tags are labels with which apps can be searched.

`tags` is simply an array of strings, where each string is a tag\/label applied to your app.

`tags: [ "settings", "my-app", "www.my-company.com" ]`

You can later find all apps belonging to `my-company` by sending a `GET` request to \(assuming Bolt is running on port 400\):

`localhost:400/api/apps?tags=www.my-company.com`

This will return an array of all apps that have `www.my-company.com` as one of their tags.

### note

Don't forget to URL-encode your tags.

