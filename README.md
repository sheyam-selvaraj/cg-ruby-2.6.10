Steps Followed
melange keygen
melange build --arch amd64 ruby-3.0.yaml --signing-key melange.rsa --debug
apko build apko.yaml apko-ruby:latest apko-ruby.tar -k melange.rsa.pub --arch amd64
docker load < apko-ruby.tar
docker run -it --user root --entrypoint /bin/sh apko-ruby:latest-amd64


docker exec -it --user root ee3122f7a177 /bin/sh
/ # id
uid=0(root) gid=0(root) groups=0(root),1(bin),2(daemon),3(sys),4(adm),6(disk),10(wheel),11(floppy),20(dialout),26(tape),27(video)
/ # ruby -v
ruby 2.6.10p210 (2022-04-12 revision 67958) [x86_64-linux-gnu]
