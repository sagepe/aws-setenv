# aws-setenv - Obtain environment variables for AWS profiles

This script is designed to print out the statements required to configure your
environment for AWS. It's intended to be useful for people who regularly work
with more than one AWS account. It's inspired by a couple of examples I've seen
used internally. I needed something similar, so I wrote my own.

Usage is simple:

`aws-setenv <AWS profile name>`

It will examine your `config` and `credentials` files and print to the screen a
list of `export` and `unset` statements that you can then copy and execute.

If a profile contains a `role_arn` it will uses STS to try to assume the role
with the credentials from the associated `source_profile` and will also check
for `mfa_serial` and if it finds it prompt for a code.

It sets `AWS_DEFAULT_PROFILE` to the current profile as well. I find it useful
to include this in [my prompt](https://github.com/sagepe/liquidprompt/tree/feature/aws-default-profile) so I have a visual reminder. I don't have a default profile set and always use this tool to set-up my environment as
required.

## Set Up

Dependencies are limited and listed in the Gemfile included for
convenience.

## To Do
* Add an option to reset the entire environment.
