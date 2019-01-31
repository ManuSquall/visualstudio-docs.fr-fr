---
title: 'Erreur : Débogage en mode mixte pour les processus IA64 non pris en charge | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.interop_unsupported_ia64
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3edd65cdb9f86d47f6c39965ba6c17ec5de3f7be
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54981631"
---
# <a name="error-mixed-mode-debugging-for-ia64-processes-is-unsupported"></a>Erreur : Le débogage en mode mixte des processus IA64 n’est pas pris en charge
Le débogueur de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ne prend pas en charge le code natif et managé mixte de débogage dans un processus basé sur Itanium.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Générez une version 32 bits de votre application pour le débogage.  
  
## <a name="see-also"></a>Voir aussi  
 [Remote Debugging](../debugger/remote-debugging.md)