# Bolt Response Codes

This is a list and description of Bolt response codes.

Note that apart from when checking to see if the code is `0` \(no error\) or `1000` \(unknown error\), it may be better to check for a range than for an exact number. For instance, it may be better to check if the code is between `200` and `299` \(inclusive\) than to check if it is `201`.

## Code 0

This means no error occurred while processing the request.

## Code 1000

This means an unknown error occurred while processing the request.

## Codes 1-99

Reserved codes.

## Codes 100-199

Request Error.

Bolt found something wrong with the request.

| **Code** | **Meaning** |
| --- | --- |
| 100 | Endpoint not specified |
| 103 | Could not find endpoint |

## Codes 200-299

User Error.

| **Code** | **Meaning** |
| --- | --- |
| 200 | Username and\/or password missing |
| 201 | A user with the same username already exists |
| 202 | Could not save user to the database |
| 203 | Could not retrieve user from the database |
| 212 | Could not log user in |
| 213 | Could not get logged-in user |

## Codes 300-399

Access-Control Error.

| **Code** | **Meaning** |
| --- | --- |
| 300 | Role name missing |
| 301 | A role with the same name already exists |
| 302 | Could not save role to the database |
| 303 | Could not retrieve role from the database |
|  |  |
| 310 | Username and\/or role name missing |
| 311 | A user-role with the same user and role already exists. |
| 312 | Could not save user-role to the database |
| 313 | Could not retrieve user-role from the database |
|  |  |
| 320 | App name and\/or role name missing |
| 321 | An app-role with the same app and role already exists |
| 322 | Could not save app-role to database |
| 323 | Could not retrieve app-role from the database |

## Codes 400-499

App Error.

| **Code** | **Meaning** |
| --- | --- |
| 400 | App name missing |
| 401 | An app with the same name already exists |
| 402 | Could not save app to the database |
| 403 | Could not retrieve app from the database |
| 404 | Could not start app due to security concerns |
|  |  |
| 410 | App path missing |
|  |  |
| 420 | App port missing |
|  |  |
| 432 | Could not save plugin to the database |
| 433 | Could not retrieve plugin from the database |

## Codes 500-599

App Permission Error.

| **Code** | **Meaning** |
| --- | --- |
| 504 | This app is not a system app |

## Codes 600-699

File System Error.

| **Code** | **Meaning** |
| --- | --- |
| 600 | File name missing |
| 601 | A file with the same name already exists |
| 602 | Could not save file |
| 603 | Could not retrieve file |

## 

