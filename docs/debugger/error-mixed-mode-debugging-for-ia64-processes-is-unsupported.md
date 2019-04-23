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
ms.openlocfilehash: 5c4414651249aa7622e7f7be59e6150a4925f1b8
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60089339"
---
# <a name="error-mixed-mode-debugging-for-ia64-processes-is-unsupported"></a>Erreur : Le débogage en mode mixte des processus IA64 n’est pas pris en charge
Le débogueur de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ne prend pas en charge le code natif et managé mixte de débogage dans un processus basé sur Itanium.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Générez une version 32 bits de votre application pour le débogage.

## <a name="see-also"></a>Voir aussi
- [Remote Debugging](../debugger/remote-debugging.md)