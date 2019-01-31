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
ms.openlocfilehash: 61c92460976ec9b95163b83744ee0b01b6ebc572
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54986083"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>Erreur : Le débogage en mode mixte des processus x64 est pris en charge uniquement quand vous utilisez Microsoft .NET Framework 4 ou ultérieur
Pour déboguer du code natif et managé mixte dans un processus 64 bits, vous devez disposer du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] version 4. Le débogage en mode mixte de processus 64 bits avec les versions de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] antérieures à la version 4 n'est pas pris en charge.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Effectuez l’une des opérations suivantes :  
  
  - Effectuez une mise à niveau du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] vers la version 4.  
  
  - Générez une version 32 bits de votre application pour le débogage.  
  
## <a name="see-also"></a>Voir aussi  
 [Remote Debugging](../debugger/remote-debugging.md)