---
title: 'Erreur : En mode mixte débogage pour x64 processus est pris en charge uniquement lorsque vous utilisez Microsoft .NET Framework 4 ou supérieur | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.interop_unsupported_x64
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 659420a34d020e4a2acab52fe606133af801fcc2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>Erreur : Le débogage en mode mixte des processus x64 est pris en charge uniquement lorsque vous utilisez Microsoft .NET Framework 4 ou version ultérieure
Pour déboguer du code natif et managé mixte dans un processus 64 bits, vous devez disposer du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] version 4. Le débogage en mode mixte de processus 64 bits avec les versions de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] antérieures à la version 4 n'est pas pris en charge.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Effectuez l’une des opérations suivantes :  
  
    -   Effectuez une mise à niveau du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] vers la version 4.  
  
    -   Générez une version 32 bits de votre application pour le débogage.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage à distance](../debugger/remote-debugging.md)