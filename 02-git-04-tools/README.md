# Домашнее задание к занятию «2.4. Инструменты Git»
Для выполнения заданий в этом разделе давайте склонируем репозиторий с исходным кодом терраформа https://github.com/hashicorp/terraform  
 git clone https://github.com/hashicorp/terraform.git

# 1. Найдите полный хеш и комментарий коммита, хеш которого начинается на aefea.
Ответ: git show aefea
 commit aefead2207ef7e2aa5dc81a34aedf0cad4c32545  
 Author: Alisdair McDiarmid <alisdair@users.noreply.github.com>  
 Date:   Thu Jun 18 10:29:58 2020 -0400  
 комментарий: Update CHANGELOG.md  

# 2. Какому тегу соответствует коммит 85024d3?
Ответ: git show 85024d3  
 commit 85024d3100126de36331c6982bfaac02cdab9e76 (tag: v0.12.23)  
 Author: tf-release-bot <terraform@hashicorp.com>  
 Date:   Thu Mar 5 20:56:10 2020 +0000  
 tag: v0.12.23  

# 3. Сколько родителей у коммита b8d720? Напишите их хеши.
Ответ: git show b8d720  
 commit b8d720f8340221f2146e4e4870bf2ee0bc48f2d5  
 Merge: 56cd7859e 9ea88f22f  
 Author: Chris Griggs <cgriggs@hashicorp.com>  
 Date:   Tue Jan 21 17:45:48 2020 -0800  
 родителей: 2  
 хеш1: 56cd7859e  
 хеш2: 9ea88f22f  

# 4. Перечислите хеши и комментарии всех коммитов которые были сделаны между тегами v0.12.23 и v0.12.24.
Ответ: git log v0.12.23..v0.12.24 --oneline  
 b14b74c49 [Website] vmc provider links  
 3f235065b Update CHANGELOG.md  
 6ae64e247 registry: Fix panic when server is unreachable  
 5c619ca1b website: Remove links to the getting started guide's old location  
 06275647e Update CHANGELOG.md  
 d5f9411f5 command: Fix bug when using terraform login on Windows  
 4b6d06cc5 Update CHANGELOG.md  
 dd01a3507 Update CHANGELOG.md  
 225466bc3 Cleanup after v0.12.23 release  

# 5. Найдите коммит в котором была создана функция func providerSource, ее определение в коде выглядит так func providerSource(...) (вместо троеточего перечислены аргументы).
Ответ: ищем коммиты с функцией  
 git log -S"func providerSource" --oneline  
 5af1e6234 main: Honor explicit provider_installation CLI config when present  
 8c928e835 main: Consult local directories as potential mirrors of providers  
в выдаче два коммита с функцией  
 git show 5af1e6234  
 commit 5af1e6234ab6da412fb8637393c5a17a1b293663  
 Author: Martin Atkins <mart@degeneration.co.uk>  
 Date:   Tue Apr 21 16:28:59 2020 -0700  
 git show 8c928e835  
 commit 8c928e83589d90a031f811fae52a81be7153e82f  
 Author: Martin Atkins <mart@degeneration.co.uk>  
 Date:   Thu Apr 2 18:04:39 2020 -0700  
коммит 8c928e83589d90a031f811fae52a81be7153e82f старше, следовательно создана в нем.  

# 6.Найдите все коммиты в которых была изменена функция globalPluginDirs.
Ответ: ищем коммиты с функцией  
 git log -S'func globalPluginDirs' --oneline  
 8364383c3 Push plugin discovery down into command package  
 один коммит: 8364383c3

# 7. Кто автор функции synchronizedWriters?
Ответ: ищем коммиты с функцией  
 git log -S'func synchronizedWriters' --oneline  
 bdfea50cc remove unused  
 5ac311e2a main: synchronize writes to VT100-faker on Windows  
смотрим коммиты  
 git show bdfea50cc  
 commit bdfea50cc85161dea41be0fe3381fd98731ff786  
 Author: James Bardin <j.bardin@gmail.com>  
 Date:   Mon Nov 30 18:02:04 2020 -0500  
 git show 5ac311e2a  
 commit 5ac311e2a91e381e2f52234668b49ba670aa0fe5  
 Author: Martin Atkins <mart@degeneration.co.uk>  
 Date:   Wed May 3 16:25:41 2017 -0700  
коммит 5ac311e2a старше, следовательно автор - Martin Atkins <mart@degeneration.co.uk>  
