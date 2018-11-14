generate_kms_password
=====================

Generate a password, then encrypt that password using an encryption context and a KMS key.

## Assumptions/Requirements

* The AWS CLI is already installed on your machine.  See: [https://aws.amazon.com/cli/]
* You've configured your CLI to have KMS access to an AWS Account.  I like to use [vault_exec](https://github.com/kmanning/vault_exec), but use whatever works for you.
* This was written on OSX, but *should* work on a Unix-based system

## How to generate a password

#### Run the generate_password script

```
> ./bin/generate_password <encryption_context> <kms_key>
```

Example:

```
> ./bin/generate_password environment=dev,application=bookstore,username=admin alias/team_key
```

Files will be generated in your current directly.  The plain text password is available in: `password.plain_text` - do not share this.  The base64 encrypted password is in `password.plain_text.encrypted_base64` - use this to populate the KMS secret payload parameters.
