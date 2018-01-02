# ansible-deps

Checks to see if dependency roles are at their latest released versions

## Dependencies

### Gems
* `term-ansicolor`

### Commandline Tools
* `git`

### Dependency files
Your meta or requirements files need to use the `tag` key for every single
role. Since `tag` is unused by Ansible (at least for now), there shouldn't
be any issue with doing this.

Here's an example:
```yaml
- name: conn.accounts
  src: https://github.com/conn/ansible-role-accounts
  tag: v1.0.0
  version: bc9d56b36e451b52e4e68728cce981970df63e74

- name: conn.box
  src: https://github.com/conn/ansible-role-box
  tag: v1.0.6
  version: fea4cdec527a2fce81bf173d2a5bcb39cc173fdc
```

Why not just put the tag in `version`? ansible-galaxy currently does
not check for tag signatures. For now, explicitly specifying a
commit hash is as good as a signature, though not as pretty.

## Usage
* `ansible-deps some-directory-with-roles-or-requirements/`
* `ansible-deps some-playbook/roles/requirements.yml`
* `ansible-deps some-role/meta/main.yml`
