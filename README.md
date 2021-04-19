# k8s-home-server

Home server based on k0s.

## Pre-tasks

### Server

```sh
useradd --create-home --user-group --shell /bin/bash --comment "Ansible user" deploy > /dev/null
mkdir /home/deploy/.ssh > /dev/null && chmod 0700 /home/deploy/.ssh
cat << EOF > /home/deploy/.ssh/authorized_keys
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAACAQCjM3H6yUjOFntS8i74/nbMhtBjMBIWslCudkhgPnz0gs9KOa4odgKAYG6B9JA5M78Cs/B3yVeM1lgSu22VGQH/fH/D609UAhKEzTwhYKOmESi2oY6aJoOXL+U782GtFVyNd53Wh6sRqC2X/VujdWCTuFFiiJnK2+mM5hZ4r0M+HcwpRi0CPyQY0XgZucwcE8uwjJXxCxHcNGp/VwYCdfbjbR7RA6jhB/lnK8znOhDjNekYeCtFJ3sO0ecXH/Zr7ciJOIYa9wprr0bYDYK4YV/Lk0HorLv6/OOEq5e9VA+bgqEGvpwFrd4amHaX23scrfSeERmrRpK1BXdQitvhVJMo3aF9nVMCdgHtuoSI0Nq5kVMUgE/BfscFVxbDB11pQr/FGf4ObEXYAA7UdOpfI8qw72r9KGHGP/t3wxSEabNq8I+YuoM3OK1d8GPUAXpWu2vubVhXqCY7n4NHMZ2ypaazSfnjUwzozAO/3WgxGLCcXPDXS4XDdnXZOfHGYtpDcHVxmPszvPeqEksCVJGBLzgvcwEGAX/OloVhqg0wV+m8IihHvYNVSLZ8PVjUx4KV4aMSRlL2SFjFJ5hWqTq7CK7yy9D12AvIWfLmKbeXnvLDLwbmtYaQzvjpdvCAVXfSJygEb8QnceHBSwOAL9EXfn11CfPwg9Mj8ZZL5IsAsSojUw== bfrank@Brads-MacBookPro13.local on 2021-02-13T11:16-05:00
EOF
chown -R deploy:deploy /home/deploy/.ssh

cat << EOF > /etc/sudoers.d/00-deploy
deploy ALL=(ALL) NOPASSWD: ALL
EOF
```

### Local

```sh
ansible-galaxy collection install -r requirements.yml
ssh-add -K ~/.ssh/ansible
```
