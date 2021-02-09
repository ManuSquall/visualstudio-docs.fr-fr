---
title: Le débogage en mode mixte pour les processus IA64 n’est pas pris en charge | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.interop_unsupported_ia64
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 22fa1b7f332d6a9f6481c513a3c2024a3551c7a5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871583"
---
# <a name="error-mixed-mode-debugging-for-ia64-processes-is-unsupported"></a>Erreur : Le débogage en mode mixte des processus IA64 n'est pas pris en charge
Le débogueur de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ne prend pas en charge le code natif et managé mixte de débogage dans un processus basé sur Itanium.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Générez une version 32 bits de votre application pour le débogage.

## <a name="see-also"></a>Voir aussi
- [Débogage à distance](../debugger/remote-debugging.md)