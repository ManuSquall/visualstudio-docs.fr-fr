---
title: Quand le point d’arrêt est atteint, boîte de dialogue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.whenbreakpointishit
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
ms.assetid: 476e3d98-cf35-4338-b124-cd0f3010d854
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 53b19f4dd0d4b0cb97bb33e4895f36c4dc8f670c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72728146"
---
# <a name="when-breakpoint-is-hit-dialog-box"></a>Lorsque le point d'arrêt est atteint, boîte de dialogue
Cette boîte de dialogue vous permet de personnaliser l’action qui se produit lorsqu’un point d’arrêt est atteint.

## <a name="uielement-list"></a>Liste des éléments d’interface
 **Imprimer un message** Imprime un message à l’aide de la syntaxe DebuggerDisplay. Pour plus d’informations, consultez [utilisation de l’attribut DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md).

 Cette zone de texte prend également en charge les mots clés spéciaux (tels que $ADDRESS) qui peuvent être utilisés par eux-mêmes ou entre les accolades d’une expression DebuggerDisplay. Les mots clés disponibles sont répertoriés dans la boîte de dialogue.

 **Continuer l’exécution** Ce contrôle est activé uniquement lorsque l’option **imprimer un message** est sélectionnée. Une fois ce contrôle sélectionné, vous pouvez utiliser un point d’arrêt comme point de trace pour suivre l’exécution de votre programme, au lieu de l’arrêter lorsque l’emplacement est atteint.

## <a name="see-also"></a>Voir aussi
- [Utilisation des points d’arrêt](../debugger/using-breakpoints.md)
- [Utilisation de l’attribut DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)