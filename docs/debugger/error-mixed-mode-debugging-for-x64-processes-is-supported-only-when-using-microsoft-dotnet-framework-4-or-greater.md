---
title: Le débogage en mode mixte pour les processus x64 est pris en charge uniquement lors de l’utilisation de Microsoft .NET Framework 4 ou version ultérieure | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.interop_unsupported_x64
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 01f8bf0b018ed5dd91cedcc221a037f3502815e7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871492"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>Erreur : Le débogage en mode mixte des processus x64 est pris en charge uniquement lorsque vous utilisez Microsoft .NET Framework 4 ou version ultérieure
Pour déboguer du code natif et managé mixte dans un processus 64 bits, vous devez disposer de .NET Framework version 4. Le débogage en mode mixte des processus 64 bits avec des versions de .NET Framework antérieures à la version 4 n’est pas pris en charge.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Effectuez l’une des opérations suivantes :

  - Mettez à niveau votre .NET Framework vers la version 4.

  - Générez une version 32 bits de votre application pour le débogage.

## <a name="see-also"></a>Voir aussi
- [Débogage à distance](../debugger/remote-debugging.md)