# SSH (Secure Shell)
SSH, or Secure Shell, is a remote administration protocol that allows users to control and modify their remote servers over the Internet. The service was created as a secure replacement for the unencrypted Telnet and uses cryptographic techniques to ensure that all communication to and from the remote server happens in an encrypted manner. It provides a mechanism for authenticating a remote user, transferring inputs from the client to the host, and relaying the output back to the client.

The SSH protocol uses encryption to secure the connection between a client and a server. All user authentication, commands, output, and file transfers are encrypted to protect against attacks in the network. For details of how the SSH protocol works, see the [protocol page](https://www.ssh.com/ssh/protocol/). To understand the SSH File Transfer Protocol, see the [SFTP](https://www.ssh.com/ssh/sftp) page.

![SSH_simplified_protocol_diagram](../../assets/SSH_simplified_protocol_diagram-2.jpg)

The SSH command consists of 3 distinct parts:
```bash 
ssh {user}@{host}
```
The SSH key command instructs your system that you want to open an encrypted Secure Shell Connection. {user} represents the account you want to access. For example, you may want to access the root user, which is basically synonymous for system administrator with complete rights to modify anything on the system. {host} refers to the computer you want to access. This can be an IP Address (e.g. 244.235.23.19) or a domain name (e.g. www.xyzdomain.com).

## Sources
- [ssh.com](https://www.ssh.com/academy/ssh/protocol)
- [hostinger blog](https://www.hostinger.com/tutorials/ssh-tutorial-how-does-ssh-work)