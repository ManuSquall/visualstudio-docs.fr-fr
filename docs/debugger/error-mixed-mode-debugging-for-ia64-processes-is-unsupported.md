---
title: 'Erreur : Le débogage en mode mixte pour les processus IA64 non pris en charge | Microsoft Docs'
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
ms.openlocfilehash: f80cc0d38335679df413f104deadc8f9135ab765
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56715750"
---
# <a name="error-mixed-mode-debugging-for-ia64-processes-is-unsupported"></a>Erreur : Le débogage en mode mixte des processus IA64 n'est pas pris en charge
Le débogueur de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ne prend pas en charge le code natif et managé mixte de débogage dans un processus basé sur Itanium.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

-   Générez une version 32 bits de votre application pour le débogage.

## <a name="see-also"></a>Voir aussi
- [Remote Debugging](../debugger/remote-debugging.md)