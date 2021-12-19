# Домашнее задание к занятию "3.1. Работа в терминале, лекция 1" - Покутный Евгений

1. Установите средство виртуализации [Oracle VirtualBox](https://www.virtualbox.org/).
 Ответ:
 ```bash
 sudo apt install virtualbox  
 ```
3. Установите средство автоматизации [Hashicorp Vagrant](https://www.vagrantup.com/).
 Ответ:
 ```bash
 sudo apt install vagrant  
 ```
6. В вашем основном окружении подготовьте удобный для дальнейшей работы терминал. Можно предложить:
  
  Ответ: Раньше всегда работал в Gnome Terminal, сейчас решил попробовать выпадающий Yakuake  
```bash
sudo apt install yakuake  
```
   1. С помощью базового файла конфигурации запустите Ubuntu 20.04 в VirtualBox посредством Vagrant:

       * Создайте директорию, в которой будут храниться конфигурационные файлы Vagrant. В ней выполните `vagrant init`. Замените содержимое Vagrantfile по умолчанию следующим:

           ```bash
           Vagrant.configure("2") do |config|
               config.vm.box = "bento/ubuntu-20.04"
           end
           ```

       * Выполнение в этой директории `vagrant up` установит провайдер VirtualBox для Vagrant, скачает необходимый образ и запустит виртуальную машину.

       * `vagrant suspend` выключит виртуальную машину с сохранением ее состояния (т.е., при следующем `vagrant up` будут запущены все процессы внутри, которые работали на момент вызова suspend), `vagrant halt` выключит виртуальную машину штатным образом.

   Ответ:  
 ```bash
 mkdir ./Vagrant  
 cd ./Vagrant  
 vagrant init  
 A `Vagrantfile` has been placed in this directory. You are now  
 ready to `vagrant up` your first virtual environment! Please read  
 the comments in the Vagrantfile as well as documentation on  
 vagrantup.com` for more information on using Vagrant.  
 vim ./Vagrantfile
 cat ./Vagrantfile
 Vagrant.configure("2") do |config|
		config.vm.box = "bento/ubuntu-20.04"
 end  
 vagrant up
Bringing machine 'default' up with 'virtualbox' provider...
==> default: Box 'bento/ubuntu-20.04' could not be found. Attempting to find and install...
    default: Box Provider: virtualbox
    default: Box Version: >= 0
==> default: Loading metadata for box 'bento/ubuntu-20.04'
    default: URL: https://vagrantcloud.com/bento/ubuntu-20.04
==> default: Adding box 'bento/ubuntu-20.04' (v202107.28.0) for provider: virtualbox
    default: Downloading: https://vagrantcloud.com/bento/boxes/ubuntu-20.04/versions/202107.28.0/providers/virtualbox.box
    default: Download redirected to host: vagrantcloud-files-production.s3-accelerate.amazonaws.com
==> default: Successfully added box 'bento/ubuntu-20.04' (v202107.28.0) for 'virtualbox'!
==> default: Importing base box 'bento/ubuntu-20.04'...
==> default: Matching MAC address for NAT networking...
==> default: Checking if box 'bento/ubuntu-20.04' version '202107.28.0' is up to date...
==> default: Setting the name of the VM: Vagrant_default_1639822448540_49953
Vagrant is currently configured to create VirtualBox synced folders with
the `SharedFoldersEnableSymlinksCreate` option enabled. If the Vagrant                                                                                                                                                                    
guest is not trusted, you may want to disable this option. For more                                                                                                                                                                       
information on this option, please refer to the VirtualBox manual:                                                                                                                                                                        

  https://www.virtualbox.org/manual/ch04.html#sharedfolders                                                                                                                                                                               

This option can be disabled globally with an environment variable:

  VAGRANT_DISABLE_VBOXSYMLINKCREATE=1

or on a per folder basis within the Vagrantfile:

  config.vm.synced_folder '/host/path', '/guest/path', SharedFoldersEnableSymlinksCreate: false
==> default: Clearing any previously set network interfaces...
==> default: Preparing network interfaces based on configuration...
    default: Adapter 1: nat
==> default: Forwarding ports...
    default: 22 (guest) => 2222 (host) (adapter 1)
==> default: Booting VM...
==> default: Waiting for machine to boot. This may take a few minutes...
    default: SSH address: 127.0.0.1:2222
    default: SSH username: vagrant
    default: SSH auth method: private key
    default: 
    default: Vagrant insecure key detected. Vagrant will automatically replace
    default: this with a newly generated keypair for better security.
    default: 
    default: Inserting generated public key within guest...
    default: Removing insecure key from the guest if it's present...
    default: Key inserted! Disconnecting and reconnecting using new SSH key...
==> default: Machine booted and ready!
==> default: Checking for guest additions in VM...
==> default: Mounting shared folders...
    default: /vagrant => /home/mishaleyka/Vagrant
vagrant suspend
==> default: Saving VM state and suspending execution...
vagrant up
Bringing machine 'default' up with 'virtualbox' provider...
==> default: Checking if box 'bento/ubuntu-20.04' version '202107.28.0' is up to date...
==> default: Resuming suspended VM...
==> default: Booting VM...
==> default: Waiting for machine to boot. This may take a few minutes...
    default: SSH address: 127.0.0.1:2222
    default: SSH username: vagrant
    default: SSH auth method: private key
==> default: Machine booted and ready!
==> default: Machine already provisioned. Run `vagrant provision` or use the `--provision`
==> default: flag to force provisioning. Provisioners marked to run always will still run.
vagrant halt
==> default: Attempting graceful shutdown of VM...
```

7. Ознакомьтесь с графическим интерфейсом VirtualBox, посмотрите как выглядит виртуальная машина, которую создал для вас Vagrant, какие аппаратные ресурсы ей выделены. Какие ресурсы выделены по-умолчанию?  

 Ответ: Виртуальной машине выделено: оперативная память 1024 Мб, 2 процессора, видеопамять 4 Мб, дисковое пространство 64 Гб, один сетевой адаптер через NAT.  Это ресурсы по умолчанию, поскольку в конфигурационном файле мы ничего не прописывали  

9. Ознакомьтесь с возможностями конфигурации VirtualBox через Vagrantfile: [документация](https://www.vagrantup.com/docs/providers/virtualbox/configuration.html). Как добавить оперативной памяти или ресурсов процессора виртуальной машине?  

  Ответ: Редактированием файла Vagrantfile, изменяю имя виртуалки, количество памяти и видеопамяти, использование процессора, изменения конфигурации применятся при следющем запуске виртуалки.  
  ```bash
 vim ./Vagrantfile
 cat ./Vagrantfile
Vagrant.configure("2") do |config|
        config.vm.box = "bento/ubuntu-20.04"
        config.vm.provider "virtualbox" do |v|
               v.name = "vm_Ubuntu_1"
               v.memory = 2048
               v.customize ["modifyvm", :id, "--vram", 12]
               v.customize ["modifyvm", :id, "--cpuexecutioncap", "90"]
               end
               
 end
  vagrant up
Bringing machine 'default' up with 'virtualbox' provider...
==> default: Checking if box 'bento/ubuntu-20.04' version '202107.28.0' is up to date...
==> default: Clearing any previously set forwarded ports...
==> default: Clearing any previously set network interfaces...
==> default: Preparing network interfaces based on configuration...
    default: Adapter 1: nat
==> default: Forwarding ports...
    default: 22 (guest) => 2222 (host) (adapter 1)
==> default: Running 'pre-boot' VM customizations...
==> default: Booting VM...
==> default: Waiting for machine to boot. This may take a few minutes...
    default: SSH address: 127.0.0.1:2222
    default: SSH username: vagrant
    default: SSH auth method: private key
==> default: Machine booted and ready!
==> default: Checking for guest additions in VM...
==> default: Mounting shared folders...
    default: /vagrant => /home/mishaleyka/Vagrant
==> default: Machine already provisioned. Run `vagrant provision` or use the `--provision`
==> default: flag to force provisioning. Provisioners marked to run always will still run.
vagrant halt
==> default: Attempting graceful shutdown of VM...
 ```
10. Команда `vagrant ssh` из директории, в которой содержится Vagrantfile, позволит вам оказаться внутри виртуальной машины без каких-либо дополнительных настроек. Попрактикуйтесь в выполнении обсуждаемых команд в терминале Ubuntu.  
Ответ:  
  ```bash
vagrant ssh
Welcome to Ubuntu 20.04.2 LTS (GNU/Linux 5.4.0-80-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

  System information as of Sat 18 Dec 2021 12:03:35 PM UTC

  System load:  0.0               Processes:             116
  Usage of /:   2.3% of 61.31GB   Users logged in:       0
  Memory usage: 7%                IPv4 address for eth0: 10.0.2.15
  Swap usage:   0%


This system is built by the Bento project by Chef Software
More information can be found at https://github.com/chef/bento
vagrant@vagrant:~$ 11
-bash: 11: command not found
vagrant@vagrant:~$ ll
total 36
drwxr-xr-x 4 vagrant vagrant 4096 Jul 28 17:56 ./
drwxr-xr-x 3 root    root    4096 Jul 28 17:50 ../
-rw-r--r-- 1 vagrant vagrant  220 Jul 28 17:50 .bash_logout
-rw-r--r-- 1 vagrant vagrant 3771 Jul 28 17:50 .bashrc
drwx------ 2 vagrant vagrant 4096 Jul 28 17:51 .cache/
-rw-r--r-- 1 vagrant vagrant  807 Jul 28 17:50 .profile
drwx------ 2 vagrant root    4096 Dec 18 10:14 .ssh/
-rw-r--r-- 1 vagrant vagrant    0 Jul 28 17:51 .sudo_as_admin_successful
-rw-r--r-- 1 vagrant vagrant    6 Jul 28 17:51 .vbox_version
-rw-r--r-- 1 root    root     180 Jul 28 17:55 .wget-hsts
vagrant@vagrant:~$ df
Filesystem                 1K-blocks     Used Available Use% Mounted on
udev                          972456        0    972456   0% /dev
tmpfs                         203524      644    202880   1% /run
/dev/mapper/vgvagrant-root  64284292  1485616  59503444   3% /
tmpfs                        1017620        0   1017620   0% /dev/shm
tmpfs                           5120        0      5120   0% /run/lock
tmpfs                        1017620        0   1017620   0% /sys/fs/cgroup
/dev/sda1                     523248        4    523244   1% /boot/efi
tmpfs                         203524        0    203524   0% /run/user/1000
vagrant                    482169360 94590928 387578432  20% /vagrant
vagrant@vagrant:~$ du
8       ./.ssh
4       ./.cache
36      .
vagrant@vagrant:~$ du -h
8.0K    ./.ssh
4.0K    ./.cache
36K     .
vagrant@vagrant:~$ pwd
/home/vagrant
vagrant@vagrant:~$
vagrant@vagrant:~$ exit
logout
Connection to 127.0.0.1 closed.
  ```

12. Ознакомиться с разделами `man bash`, почитать о настройках самого bash:
     * какой переменной можно задать длину журнала `history`, и на какой строчке manual это описывается?
     * что делает директива `ignoreboth` в bash?  
  
Ответ:  
* длину журнала задается переменной HISTSIZE, описанной в строке 598  
```bash
       HISTSIZE
              The number of commands to remember in the command history (see HISTORY below).  If the value is 0, commands are not saved in the history list.  Numeric values less than zero result in every command being  saved  on
              the history list (there is no limit).  The shell sets the default value to 500 after reading any startup files.
```
* это значение переменной HISTCONTROL указывающая применять одноременно значения ignorespace — не сохранять строки начинающиеся с символа <пробел> и ignoredups — не сохранять строки, совпадающие с последней выполненной командой  
    
13. В каких сценариях использования применимы скобки `{}` и на какой строчке `man bash` это описано?  
Ответ: используются для сокращения длины команды, Brace Expansion строка 750  
```bash
   Brace Expansion  
       Brace expansion is a mechanism by which arbitrary strings may be generated.  This mechanism is similar to pathname expansion, but the filenames generated need not exist.  Patterns to be brace expanded take the form of  an
       optional  preamble,  followed  by either a series of comma-separated strings or a sequence expression between a pair of braces, followed by an optional postscript.  The preamble is prefixed to each string contained within
       the braces, and the postscript is then appended to each resulting string, expanding left to right.  
       Brace expansions may be nested.  The results of each expanded string are not sorted; left to right order is preserved.  For example, a{d,c,b}e expands into `ade ace abe'.
       
       A sequence expression takes the form {x..y[..incr]}, where x and y are either integers or single characters, and incr, an optional increment, is an integer.  When integers are supplied, the expression expands to each num‐
       ber  between  x and y, inclusive.  Supplied integers may be prefixed with 0 to force each term to have the same width.  When either x or y begins with a zero, the shell attempts to force all generated terms to contain the
       same number of digits, zero-padding where necessary.  When characters are supplied, the expression expands to each character lexicographically between x and y, inclusive, using the default C locale.  Note that both x  and
       y must be of the same type.  When the increment is supplied, it is used as the difference between each term.  The default increment is 1 or -1 as appropriate.

       Brace  expansion is performed before any other expansions, and any characters special to other expansions are preserved in the result.  It is strictly textual.  Bash does not apply any syntactic interpretation to the con‐
       text of the expansion or the text between the braces.

       A correctly-formed brace expansion must contain unquoted opening and closing braces, and at least one unquoted comma or a valid sequence expression.  Any incorrectly formed brace expansion is left unchanged.  A { or , may
       be  quoted with a backslash to prevent its being considered part of a brace expression.  To avoid conflicts with parameter expansion, the string ${ is not considered eligible for brace expansion, and inhibits brace expan‐
       sion until the closing }.

       This construct is typically used as shorthand when the common prefix of the strings to be generated is longer than in the above example:

              mkdir /usr/local/src/bash/{old,new,dist,bugs}
       or
              chown root /usr/{ucb/{ex,edit},lib/{ex?.?*,how_ex}}

       Brace expansion introduces a slight incompatibility with historical versions of sh.  sh does not treat opening or closing braces specially when they appear as part of a word, and preserves them in the  output.   Bash  re‐
       moves  braces  from words as a consequence of brace expansion.  For example, a word entered to sh as file{1,2} appears identically in the output.  The same word is output as file1 file2 after expansion by bash.  If strict
       compatibility with sh is desired, start bash with the +B option or disable brace expansion with the +B option to the set command (see SHELL BUILTIN COMMANDS below).
```
14. Основываясь на предыдущем вопросе, как создать однократным вызовом `touch` 100000 файлов? А получилось ли создать 300000? Если нет, то почему?  
Ответ: 
```bash
touch {1..100000}.txt
vagrant@vagrant:~$ touch {1..300000}.txt
-bash: /usr/bin/touch: Argument list too long
vagrant@vagrant:~$ ^C
vagrant@vagrant:~$ ^C
vagrant@vagrant:~$ getconf ARG_MAX
2097152
```  
Не получилось из-за ограничения на длину аргумента  

15. В man bash поищите по `/\[\[`. Что делает конструкция `[[ -d /tmp ]]`  
Ответ: Возвращает 1 или 0 в зависимости от выражния в скобках, [[ -d /tmp ]] - возвращает 1 если существут папка tmp  
  
16. Основываясь на знаниях о просмотре текущих (например, PATH) и установке новых переменных; командах, которые мы рассматривали, добейтесь в выводе type -a bash в виртуальной машине наличия первым пунктом в списке:

     ```bash
     bash is /tmp/new_path_directory/bash
     bash is /usr/local/bin/bash
     bash is /bin/bash
     ```

     (прочие строки могут отличаться содержимым и порядком)
     В качестве ответа приведите команды, которые позволили вам добиться указанного вывода или соответствующие скриншоты.
  

Ответ:  
```bash
mkdir /tmp/new_path_directory
vagrant@vagrant:~$ cp  /bin/bash /tmp/new_path_directory/
vagrant@vagrant:~$ PATH=/tmp/new_path_directory:$PATH
vagrant@vagrant:~$ type -a bash
bash is /tmp/new_path_directory/bash
bash is /usr/bin/bash
bash is /bin/bash
```

17. Чем отличается планирование команд с помощью `batch` и `at`?  
Ответ: `batch` - выполнянт заданную команду если загрузка системы становится меньше 0.8, `at` - выполняет заданную команду в указанное дату и время  


19. Завершите работу виртуальной машины чтобы не расходовать ресурсы компьютера и/или батарею ноутбука.  
Ответ:  
```bash
vagrant halt
==> default: Attempting graceful shutdown of VM...
```

 
 ---

## Как сдавать задания

Обязательными к выполнению являются задачи без указания звездочки. Их выполнение необходимо для получения зачета и диплома о профессиональной переподготовке.

Задачи со звездочкой (*) являются дополнительными задачами и/или задачами повышенной сложности. Они не являются обязательными к выполнению, но помогут вам глубже понять тему.

Домашнее задание выполните в файле readme.md в github репозитории. В личном кабинете отправьте на проверку ссылку на .md-файл в вашем репозитории.

Также вы можете выполнить задание в [Google Docs](https://docs.google.com/document/u/0/?tgif=d) и отправить в личном кабинете на проверку ссылку на ваш документ.
Название файла Google Docs должно содержать номер лекции и фамилию студента. Пример названия: "1.1. Введение в DevOps — Сусанна Алиева".

Если необходимо прикрепить дополнительные ссылки, просто добавьте их в свой Google Docs.

Перед тем как выслать ссылку, убедитесь, что ее содержимое не является приватным (открыто на комментирование всем, у кого есть ссылка), иначе преподаватель не сможет проверить работу. Чтобы это проверить, откройте ссылку в браузере в режиме инкогнито.

[Как предоставить доступ к файлам и папкам на Google Диске](https://support.google.com/docs/answer/2494822?hl=ru&co=GENIE.Platform%3DDesktop)

[Как запустить chrome в режиме инкогнито ](https://support.google.com/chrome/answer/95464?co=GENIE.Platform%3DDesktop&hl=ru)

[Как запустить  Safari в режиме инкогнито ](https://support.apple.com/ru-ru/guide/safari/ibrw1069/mac)

Любые вопросы по решению задач задавайте в чате Slack.

---
