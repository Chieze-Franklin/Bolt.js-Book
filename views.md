# Views

A view is simply a UI page that responds to a request of format `/:view`. Bolt comes packaged with certain views \(called _native views_\) but allows apps to add new views as well as provide new UI for existing views via plugins.

## Native Views

Native views allow Bolt to handle some common\/expected endpoints \(like `/home`\) without having a full-feature app installed for that. Of the few native views that come with Bolt, some can be overriden while others can't. Some of the views that **can not** be overriden are:

### login

The login view shows up when a request is sent to [\/login](/ui endpoints#login).

This view serves to help a user get logged in.

As logging a user in is a sensitive operation, Bolt does not allow apps to extend this view. Also, requests from non-system apps to this endpoint will be rejected.

\#\#\# logout

The logout view shows up when a request is sent to \['\/logout'\]\(api-ui\#get-logout\).

This view serves to help a user get logged out.

\#\#\# setup

The setup view shows up when a request is sent to \['\/setup'\]\(api-ui\#get-setup\).

This is a pretty special view that shows up only on first run. If Bolt detects that this is the first run \(for instance if there is no registered user in the database\) then it shows the setup view.

The setup view performs the following tasks:

\* Creates a user with the supplied user name and password.

\* Creates a role named "admin", giving it administrative privileges.

\* Associates the earlier-created user with the admin role, making the user an admin.

\* Logs the user in.

\* Redirects to \`'\/settings'\` view.

\#\# Overridable Native Views

These are native views that are simply placeholders that show up only if no app has been installed to handle a particular view endpoint. A good number of times they simply serve to direct you to download the appropriate app for that endpoint. Examples include:

\* 404

\* error

\* home

\* idle

\* launcher

\# Resolving Views

This describes how Bolt knows what to show when a user navigates to a view \`'\/{view}'\`.

For views that cannot be overriden \(like \`'\/setup'\`, \`'\/login'\`\), the process is straight-forward as Bolt already knows what to show.

For views that can be overriden, when you navigate to \`'\/{view}'\`:

\* Bolt will check its database for the default app \(and endpoint\) for that view. On finding it, Bolt will launch that app \(and point to the appropriate endpoint\).

\* If such an app is not found Bolt will look for a \[native view\]\(\#native-views\) for the specified view.

\* If no native view is found Bolt will redirect to \`'\/404\`', and the entire view-resollution process will happen again, this time for \`'404'\`.

