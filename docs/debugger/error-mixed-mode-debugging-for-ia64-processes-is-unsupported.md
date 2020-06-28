---
title: 'Erreur : le débogage en mode mixte des processus IA64 n’est pas pris en charge | Microsoft Docs'
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 850698edc53e810bbb4dcd2bfd45e31eedcecb2a
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85460662"
---
# <a name="error-mixed-mode-debugging-for-ia64-processes-is-unsupported"></a>Erreur : Le débogage en mode mixte des processus IA64 n'est pas pris en charge
Le débogueur de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ne prend pas en charge le code natif et managé mixte de débogage dans un processus basé sur Itanium.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Générez une version 32 bits de votre application pour le débogage.

## <a name="see-also"></a>Voir aussi
- [Débogage à distance](../debugger/remote-debugging.md)