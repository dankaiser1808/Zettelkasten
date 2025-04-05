#docker #linux 

The docker daemon always runs on the system as the root user. This is the reason why we have to use the sudo command every time we execute a docker command.
To enable other users to execute docker commands, we need to create a user group named docker and specify the privileged users.

[[Create a Unix User Group]]
[[Add Unix User To Group]]
[[Switch Unix Group in Current Terminal Session]]
[[Switch Unix User in Current Terminal Session]]
