---
title: 'Erreur : En mode mixte de débogage pour x64 processus est pris en charge uniquement lorsque vous utilisez Microsoft .NET Framework 4 ou version ultérieure | Microsoft Docs'
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
ms.openlocfilehash: 9ef0daf5fd28bd829edcdce412839b03ed8347bf
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66745441"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>Erreur : Le débogage en mode mixte des processus x64 est pris en charge uniquement quand vous utilisez Microsoft .NET Framework 4 ou ultérieur
Pour déboguer du code natif et managé mixte dans un processus 64 bits, vous devez disposer de .NET Framework version 4. Le débogage en mode mixte des processus 64 bits avec les versions du .NET Framework antérieures à 4 n’est pas pris en charge.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Effectuez l’une des opérations suivantes :

  - Mettre à niveau votre version .NET Framework version 4.

  - Générez une version 32 bits de votre application pour le débogage.

## <a name="see-also"></a>Voir aussi
- [Remote Debugging](../debugger/remote-debugging.md)