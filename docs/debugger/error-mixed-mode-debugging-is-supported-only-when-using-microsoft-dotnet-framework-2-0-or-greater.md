---
title: 'Erreur : Débogage en mode mixte est pris en charge seulement quand vous utilisez Microsoft .NET Framework 2.0 ou supérieur | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.interop_unsupported_to_old
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
ms.openlocfilehash: 2fb4d0dfaeb944700757c9ceec222dbd62dab9dd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62850684"
---
# <a name="error-mixed-mode-debugging-is-supported-only-when-using-microsoft-net-framework-20-or-greater"></a>Erreur : Le débogage en mode mixte est pris en charge seulement quand vous utilisez Microsoft .NET Framework 2.0 ou ultérieur
Pour déboguer du code natif et managé mixte, vous devez disposer de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] version 2.0, 3.0, 3.5 ou 4. Le débogage en mode mixte avec les versions précédentes du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] n’est pas pris en charge.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Mettez le [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] à niveau avec la version 2.0, 3.0, 3.5 ou 4.

## <a name="see-also"></a>Voir aussi
- [Remote Debugging](../debugger/remote-debugging.md)