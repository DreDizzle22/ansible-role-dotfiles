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
The folder path of your dotfiles

`dotfiles_folder_path: "$HOME/dotfiles"`

The git repository containing your dotfiles (`https://github.com/user/repo.git`)

`dotfiles_git_repo: ""`


The location of your .bashrc file

`bashrc_path: "~/.bashrc"`

Your alias for git

`dotfiles_cmd_alias_name: "dotfiles"`

Your commands would look like this
```
dotfiles status
dotfiles pull
dotfiles add .bashrc
dotfiles commit -m "added ~/.bashrc"
dotfiles push
```
Note: If the `dotfiles_cmd_alias_name` variable is empty, then the role will set it to `dotfiles`

The location of your git binary

`git_binary_path: "usr/bin/git"`

Your desired git work tree path (note: this is where your dotfiles will exist)

`git_work_tree_path: "$HOME"`

Dependencies
------------

None

Example Playbook
----------------

    - hosts: localhost
      name: "Setting Up Your Dotfiles Workspace!"
      roles:
        - role: dotfiles
          dotfiles_git_repo: "https://github.com/DreDizzle22/dotfiles.git"
          dotfiles_cmd_alias_name: "dot"
