dkms-gentoo
-----

Призван автоматизировать сборку/обновление сторонних модулей ядра. Например nvidia/ati/virtualbox...

Как это работает
-----

При загрузке проверяется наличие всех сторонних модулей из базы пакетов для текущего ядра.
Если модуль отсутствует или имеет версию отличную от версии модуля из базы установленных пакетов,
то пакет, содержащий этот модуль, будет пересобран для текущего ядра.

Так же есть возможность проверить наличие/соответствие_версий модулей для ядер по версии ядра или по пути до исходников ядра.
Можно просто пересобрать все модули под указанное ядро. Что-то типа module-rebuild.

Модули и соответствующие им пакеты хранятся в собственной базе, которая создаётся при установке (из ебилда),
при ручном запуске dkms-gentoo --db или при выключении.
При обновлении собственной базы, вновь обрабатываются только те части базы установленных пакетов,
что изменились после последнего изменения базы dkms-gentoo.
Если пакет со сторонними модулями был удалён, то он и его модули будут удалены из базы при проверке или пересоздании базы.

Установка
-----
<pre>
layman -a stuff
emerge -avD sys-apps/dkms-gentoo
</pre>