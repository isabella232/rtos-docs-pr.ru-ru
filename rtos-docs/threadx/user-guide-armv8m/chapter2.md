---
title: Глава 2. Установка поддержки ThreadX для ARMv8-M
description: В этой главе содержатся сведения об установке и использовании исходного кода ThreadX для архитектуры ARMv8-M.
author: v-condav
ms.author: v-condav
ms.date: 03/04/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 303b83bcc92797314b764353b770965c0170fb99
ms.sourcegitcommit: d8edbb3207fe99f8afb431597dac063e73383e68
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/05/2021
ms.locfileid: "106377535"
---
#  <a name="chapter-2--installing-threadx-support-for-armv8-m"></a>Глава 2. Установка поддержки ThreadX для ARMv8-M

Существуют дополнительные файлы исходного кода ThreadX для поддержки архитектуры ARMv8-M.

Если ThreadX должен выполняться в безопасном режиме, эти дополнительные файлы и API-интерфейсы не требуются. Чтобы запустить ThreadX в безопасном режиме, укажите символ **TX_SECURE_EXECUTION** в начале файла **_tx_port.h_ *_ или в командной строке, или в параметрах проекта. Убедитесь, что _* TX_SECURE_EXECUTION** указан для всех файлов c и сборок. ThreadX и пользовательское приложение будут выполняться в безопасном режиме.

Чтобы запустить ThreadX и пользовательское приложение в небезопасном режиме и поддерживать небезопасные вызываемые функции, выполните следующие действия.

Добавьте файл ***tx_thread_secure_stack.c*** в безопасное приложение.

Добавьте перечисленные ниже файлы библиотеку ThreadX.

- ***tx_secure_interface.h***
- ***txe_thread_secure_stack_allocate.c***
- ***txe_thread_secure_stack_free.c***
- ***tx_thread_secure_stack_allocate.s***
- ***tx_thread_secure_stack_free.s***

Следующие два файла заменяют универсальные файлы в библиотеке ThreadX.

- ***tx_thread_stack_error_handler.c***
- ***tx_thread_stack_error_notify.c***

## <a name="additional-threadx-sources-for-armv8-m"></a>Дополнительные источники ThreadX для ARMv8-M

Ниже описаны дополнительные файлы ThreadX для расширения TrustZone для архитектуры ARMv8-M.

  | **Имя файла**                            | **Contents**                                                        |
  |------------------------------------------|---------------------------------------------------------------------|
  | ***tx_secure_interface.h***              | Включаемый файл, определяющий небезопасные вызываемые функции ThreadX. |
  | ***txe_thread_secure_stack_allocate.c*** |  Файл проверки ошибок для API выделения безопасного стека. |
  | ***txe_thread_secure_stack_free.c***     |  Файл проверки ошибок для API высвобождения безопасного стека. |
  | ***tx_thread_secure_stack_allocate.s***  |  Небезопасная оболочка для службы выделения безопасного стека. |
  | ***tx_thread_secure_stack_free.s***      |  Небезопасная оболочка для службы высвобождения безопасного стека. |
  | ***tx_thread_stack_error_handler.c***    |  Обработчик ошибок стека потоков. |
  | ***tx_thread_stack_error_notify.c***     |  Регистрация обратного вызова уведомлений для обработки ошибок стека потоков. |
