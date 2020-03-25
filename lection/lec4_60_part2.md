* Все функции, связанные с обеспечением работы сети, блочных (дисковых) устройств, эмуляции видеоадаптеров и прочих устройств вынесены за пределы гипервизора. Большинство таких устройств состоит из двух частей: драйверы в domU и программы в dom0. Драйвер (чаще всего встроенный в ядро ОС или загружающийся в виде модуля) реализует минимальный объём работы, фактически, транслируя запросы от ОС в программу в dom0. Программа в dom0 выполняет основную часть работы. При этом программа чаще всего запускается в виде отдельного процесса для каждого обслуживаемого устройства. Сбой в такой программе ведёт к сбою только одного устройства (блочного, сетевого) и не затрагивает работу других копий программы (то есть не затрагивает сетевые/блочные устройства остальных доменов, или даже другие устройства того же самого домена).