5.1. Введение в виртуализацию. Типы и функции гипервизоров. Обзор рынка вендоров и областей применения.

1. Опишите кратко, как вы поняли: в чем основное отличие полной (аппаратной) виртуализации, паравиртуализации и виртуализации на основе ОС.

- Аппаратная - основное отличие от паравиртуализации заключается в гипервизоре, он и есть та ОС которая взаимодействует с железом. Пример - популярный VMware.
- Паравиртуализация - для гипервизора необходима ОС. Пример ПК СВ Брест от Астра Линукс, сначала разварачиваем на сервере ОС Астра далее Брест (переделанная opennebula) гипервизор для управления ВМ.
- На основе ОС - нет гипервизора, изолированные ВМ поверх основной ОС.

