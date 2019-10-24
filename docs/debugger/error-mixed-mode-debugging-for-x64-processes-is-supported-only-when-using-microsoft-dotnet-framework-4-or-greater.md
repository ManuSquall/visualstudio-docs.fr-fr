---
title: 'Erreur : le débogage en mode mixte pour les processus x64 est pris en charge uniquement lors de l’utilisation de Microsoft .NET Framework 4 ou version ultérieure | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.interop_unsupported_x64
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 67b9d1c737e4490195b209abca824b2d6d51176c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737599"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>Erreur : Le débogage en mode mixte des processus x64 est pris en charge uniquement lorsque vous utilisez Microsoft .NET Framework 4 ou version ultérieure
Pour déboguer du code natif et managé mixte dans un processus 64 bits, vous devez disposer de .NET Framework version 4. Le débogage en mode mixte des processus 64 bits avec des versions de .NET Framework antérieures à la version 4 n’est pas pris en charge.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Effectuez l’une des opérations suivantes :

  - Mettez à niveau votre .NET Framework vers la version 4.

  - Générez une version 32 bits de votre application pour le débogage.

## <a name="see-also"></a>Voir aussi
- [Remote Debugging](../debugger/remote-debugging.md)