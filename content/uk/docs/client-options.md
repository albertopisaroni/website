---
title: Клієнтські реалізації ACME
slug: client-options
top_graphic: 1
lastmod: 2020-12-18
---

{{< clientslastmod >}}

Let's Encrypt використовує протокол ACME для підтвердження того, що ви контролюєте дане доменне ім'я, а також для видачі вам сертифіката. Щоб отримати сертифікат Let's Encrypt, вам необхідно обрати для використання частину клієнтського програмного забезпечення ACME.

Наведені нижче клієнти ACME пропонуються третіми сторонами. Let's Encrypt не контролює та не перевіряє сторонніх клієнтів і не може дати ніяких гарантій щодо їх безпеки або надійності.

Існують деякі браузерні клієнти ACME, але ми не наводимо їх тут, оскільки вони заохочують ручний процес оновлення, що призводить до поганого досвіду користувача та збільшує ризик виникнення пропущених оновлень.

# Рекомендуємо: Certbot

Ми рекомендуємо більшості людей починати з клієнта [Certbot](https://certbot.eff.org/). Це може просто принести вам сертифікат або допомогти в установці, в залежності від того, чому ви віддаєте перевагу. Він простий у використанні, працює на багатьох операційних системах та має відмінну документацію.

Якщо Certbot не задовольняє ваші потреби, або ви просто хочете спробувати щось інше, нижче представлено безліч інших клієнтів на вибір, згрупованих за мовою або середовищі, в якому вони працюють.

# Інші клієнтські варіанти

Всі наступні клієнти підтримують API ACMEv2 ([RFC 8555](https://tools.ietf.org/html/rfc8555)). Найближчим часом ми повністю [відмовимося від підтримки ACMEv1](https://community.letsencrypt.org/t/end-of-life-plan-for-acmev1/88430/). Якщо ви вже використовуєте один з перерахованих нижче клієнтів, обов'язково оновіть його до останньої версії. Якщо клієнт, який ви використовуєте, відсутній в списку нижче, можливо, він не підтримує ACMEv2, в цьому випадку ми рекомендуємо зв'язатися з супутнім проєктом або перейти на інший клієнт.

{{< clients libraries="Libraries" projects="Проєкти, що інтегруються з Let's Encrypt" >}}

Модуль Python [acme](https://github.com/certbot/certbot/tree/master/acme) є частиною Certbot, але також використовується низкою інших клієнтів та доступний як окремий пакет через [PyPI](https://pypi.python.org/pypi/acme), [Debian](https://packages.debian.org/search?keywords=python-acme), [Ubuntu](https://launchpad.net/ubuntu/+source/python-acme), [Fedora](https://bodhi.fedoraproject.org/updates/?packages=python-acme), а також інші дистрибутиви.

{{< /clients >}}

# Додавання клієнта/проєкту

Якщо вам відомий клієнт ACME або проєкт, інтегрований з API ACMEv2 компанії Let's Encrypt, який відсутній на вищевказаної сторінці, будь ласка, надішліть запит на включення змін в наш [website repository](https://github.com/letsencrypt/website/) на GitHub, оновивши файл `data/clients.json`.

Перед відправкою запиту на виправлення, будь ласка, переконайтеся, що:

1. Клієнт дотримується [політики торгової марки Let's Encrypt](/trademarks).
1. Клієнт не є браузерним та підтримує автоматичне оновлення.
1. Ваш коміт додає вашого клієнта в **кінець** відповідні розділи (Не забудьте про "acme_v2", якщо це доречно!).
1. Ваш коміт оновлює мітку дати `lastmod` у верхній частині `clients.json`.