# Managing User Accounts

!!! example ""
    [PhotoPrism® Plus](https://www.photoprism.app/editions#compare) includes a web user interface for account and session management, in addition to the [command-line interface](cli.md) available in all editions.

You can add, edit and delete user accounts by navigating to *Settings > Users* as an [Admin](roles.md#admin):

![Screenshot](img/users.jpg){ class="shadow" }

## Adding a New User

![Screenshot](img/users-add.jpg){ class="shadow" }

## Editing User Details

![Screenshot](img/users-edit.jpg){ class="shadow" }

Only [super admins](roles.md#admin) can [change the authentication provider](cli.md#command-options) of an account through the web interface, except for their own account, so that they do not accidentally lock themselves out e.g. by setting it to "none".

## Changing Passwords

Super admins can reset a user's password, while regular admins can change passwords only if they know the current password.

![Screenshot](img/users-change-pw.jpg){ class="shadow" }

## Deleting a User

![Screenshot](img/users-delete.jpg){ class="shadow" }
