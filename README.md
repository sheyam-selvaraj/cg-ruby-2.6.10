**This README provides a clear step-by-step guide for anyone who wants to replicate your process. You can customize it further based on your specific needs.
**

**# Ruby 2.6 Docker Image with Melange and apko**

This repository contains steps to build a Docker image for Ruby 3.0 using Melange and apko, targeting the `amd64` architecture.

**## Prerequisites**

- Melange
- apko
- Docker

**## Steps Followed

### 1. Generate a Melange Key Pair

Generate the signing key using the following command:**

```bash
melange keygen
```

**Build the Ruby 2.6 Package
Use Melange to build the Ruby 2.6 package:**
```
melange build --arch amd64 melange.yaml --signing-key melange.rsa --debug
```
**Build the Docker Image with apko
**Build the Docker image using the apko.yaml configuration file:

```
apko build apko.yaml apko-ruby:latest apko-ruby.tar -k melange.rsa.pub --arch amd64
```
**Load the generated Docker image into your local Docker daemon:**
```
docker load < apko-ruby.tar
```
**Run the Docker Container
**
```
docker run -it --user root --entrypoint /bin/sh apko-ruby:latest-amd64
```
**Verify Ruby Installation**
To verify that Ruby is correctly installed, execute the following commands inside the running container:

Start a new shell session in the running container:
```
docker exec -it --user root <container_id> /bin/sh
```
Check the user ID:
```
id
```
uid=0(root) gid=0(root) groups=0(root),1(bin),2(daemon),3(sys),4(adm),6(disk),10(wheel),11(floppy),20(dialout),26(tape),27(video)

Verify the Ruby version:
```
ruby -v
```
ruby 2.6.10p210 (2022-04-12 revision 67958) [x86_64-linux-gnu]



