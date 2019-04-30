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
ms.openlocfilehash: 1423cbcfcae53948f7b9c9cd52eb90f57251bc24
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62851059"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>Erreur : Le débogage en mode mixte des processus x64 est pris en charge uniquement quand vous utilisez Microsoft .NET Framework 4 ou ultérieur
Pour déboguer du code natif et managé mixte dans un processus 64 bits, vous devez disposer du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] version 4. Le débogage en mode mixte de processus 64 bits avec les versions de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] antérieures à la version 4 n'est pas pris en charge.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Effectuez l’une des opérations suivantes :

  - Effectuez une mise à niveau du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] vers la version 4.

  - Générez une version 32 bits de votre application pour le débogage.

## <a name="see-also"></a>Voir aussi
- [Remote Debugging](../debugger/remote-debugging.md)