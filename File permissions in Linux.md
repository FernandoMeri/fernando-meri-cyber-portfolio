# File permissions in Linux

## Project description

In this project, I assume the role of a security professional in a large organization, focused on ensuring appropriate access permissions for the research team. My task is to audit file and directory permissions on a Linux system, identifying and correcting any discrepancies with authorization policies. Using specific Linux commands, I will adjust these permissions to ensure that only authorized users have the necessary access, thereby strengthening the security of the file system.

## Check file and directory details

I’ll use the command `ls -la` to check all file and directory permissions, including hidden ones.

`-rw-rw-rw- 1 researcher2 research 0 May 10 08:00 project_k.txt -rw-r----- 1 researcher2 research 0 May 10 08:00 project_m.txt -rw-rw-r-- 1 researcher2 research 0 May 10 08:00 project_r.txt -rw-rw-r-- 1 researcher2 research 0 May 10 08:00 project_t.txt -rw--w---- 1 researcher2 research 0 May 10 08:00 .project_x.txt drwxr-x--- 2 researcher2 research 0 May 10 08:00 drafts/`

## Describe the permissions string

Using this permission string `project_k.txt` (`-rw-rw-rw-`) The 10-character string that heads each entry in the output of the `ls -la` command represents the access permissions for the file or directory. The first character indicates the type of entry (`-` for a regular file, `d` for a directory). The remaining nine characters are divided into three blocks of three, corresponding to the permissions of the owner (user), the group to which it belongs, and other users, respectively. Each character within these blocks means: r for read, `w` for write, `x` for execute (or access for directories), and `-` if the permission is not granted.

For example, the permission string `-rw-rw-rw-` for `project_k.txt t`ells us that it is a regular file (`-`). Both the owner (`rw-`), the group (`rw-`), and other users (`rw-`) have read and write permissions on this file.

## Change file permissions

The organization's policy dictates that 'other' users should not have write access to any files. Upon reviewing the initial permissions, `project_k.txt` was identified as violating this policy, as it currently has read and write permissions for 'others' (`-rw-rw-rw-`).

To correct this, I used the `chmod` command to change the permissions to `664` (`rw-rw-r--`). This grants read and write access to the file owner and group, but only read access to others.

`Bash`

`chmod 664 project_k.txt`

After applying the command, I verified the change:

`Bash`

`ls -l project_k.txt`

`-rw-rw-r-- 1 researcher2 research 0 May 10 08:00 project_k.txt`

The permissions for `project_k.txt` have now been updated to prevent write access for 'others', aligning with organizational policy.

## Change file permissions on a hidden file

The hidden file `.project_x.txt` is an archived document that requires specific permission adjustments. Organizational policy dictates that this file should not have write permissions for any user. Currently, it has `rw-` for the owner and `w-` for the group, which violates this policy. However, the owner and group should retain read access to the file.

To implement the required permissions (`r--r-----`, octal `440`), which grant read access only to the owner and group while removing all write permissions, I used the `chmod` command:

`Bash`  
`chmod 440 .project_x.txt`

After applying the command, I verified the updated permissions:

`Bash`  
`ls -la .project_x.txt`

`-r--r----- 1 researcher2 research 0 May 10 08:00 .project_x.txt`

The permissions for `.project_x.txt` now correctly prevent any write access, while allowing read access for the owner and group, aligning with the archive policy.

## Change directory permissions

The organization's security policy states that only the owner user (`researcher2`) should have access to the `drafts` directory and its contents. The current permissions for the `drafts` directory are `drwxr-x---`, which allows execute access to the group.

To align the directory with this policy and ensure that only the owner has read, write, and execute permissions, I used the `chmod` command with the octal notation `700`:

`Bash`

`chmod 700 drafts`

After applying the command, I verified the updated permissions for the directory:

`Bash`

`ls -ld drafts`

`drwx------ 2 researcher2 research 0 May 10 08:00 drafts/`

Now, `drafts` has `drwx------` permissions, ensuring that only the owner (`researcher2`) can access and manage its contents, which strengthens the security of access to the directory.

## Summary

In this project, as a security professional, I audited and adjusted file and directory permissions in a Linux environment for the research team. I used `ls -la` commands to identify current permissions and `chmod` to modify access, ensuring that only authorized users had the appropriate privileges. This practical exercise demonstrates my ability to implement effective access controls and strengthen file system security, which is critical in a large organization.  
