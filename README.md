Anisble Role for Dotfiles
=========

This role is for setting up an environment that allows you to back up, restore, and sync your dotfiles via git.

Requirements
------------

This role requires the following prerequisites:
- Ansible 2.8 or later
- A git repo that contains your dotfiles.

Role Variables
--------------
#
##### Default Variables
#

The path for your home directory. This will be your $HOME directory by default.
```dotfiles_home_path: "{{ lookup('env', 'HOME') }}"```

The folder path of your dotfiles git bare repo
```dotfiles_git_repo_path: "{{ dotfiles_home_path }}/dotfiles"```

The git repository containing your dotfiles (`https://github.com/user/repo.git`)
```dotfiles_git_repo_url: ""```

The location of your .bashrc file
```dotfiles_bashrc_file_path: "{{ dotfiles_home_path }}/.bashrc"```

Your alias for git
```dotfiles_alias: "dot"```

Your commands would look like this
```
dot status
dot pull
dot add .bashrc
dot commit -m "added ~/.bashrc"
dot push
```
Note: If the `dotfiles_alias` variable is empty, then the role will set it to `dot`

##### Install independently
```ansible-pull -U https://github.com/dredizzle22/ansible-role-dotfiles.git --extra-vars "dotfiles_git_repo_url=https://github.com/DreDizzle22/dotfiles.git"```

##### Include in playbook
```
roles:
 - dredizzle22.dotfiles
```

Role Dependencies
------------
none

Example Playbook
----------------

    - hosts: localhost
      name: "Setting Up Your Dotfiles Workspace!"
      roles:
        - role: dotfiles
          dotfiles_git_repo_url: "https://github.com/DreDizzle22/dotfiles.git"
          dotfiles_alias: "dotfiles" # optional
