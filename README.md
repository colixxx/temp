# Ansible users role

> * manages users
> * manages groups
> * manages user's and group's privileges
> * manages user's authorized keys

## Dependencies

* Ansible >= 2.4

## Variables

The definition of users comes from the group.
The main variable for creating a user or group is the *groups_for_create*. Use it to define a list of groups and users on your server or server group.

host_vars.yml
```yaml
groups_for_create:
  - group: front
    users:
      - front1

```
This role should also be used to deploy root users to servers. The list of root users is hardcoded in vars.

Each user can own an ssh-key. It must be defined by env `key:` in a file whose name matches the username. The file must be in `./files/users`. Keys for root users should also be in the files folder along with the rest.

## Privileges

Root users belong to the admins group. This group was created specifically so as not to make division by vendor. Privileges are set using `./templates`. They are divided into groups and users. If you don't need special privileges, don't create anything in templates.

## Changes and Releases

Use merge requests for changes.

1. Create your feature branch (`git checkout -b my-new-feature`)
2. Commit your changes (`git commit -am 'Add some feature'`)
3. Push to the branch (`git push origin my-new-feature`)
4. Create new Merge Request