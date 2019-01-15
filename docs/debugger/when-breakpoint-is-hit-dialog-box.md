---
title: Lorsque le point d’arrêt est boîte de dialogue de positionnement | Microsoft Docs
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 560a79892ee50f3d151971f46bcc2c2b7f205d3f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53845614"
---
# <a name="when-breakpoint-is-hit-dialog-box"></a>Lorsque le point d'arrêt est atteint, boîte de dialogue
Avec cette boîte de dialogue, vous pouvez personnaliser l’action qui se produit lorsqu’un point d’arrêt est atteint.  
  
## <a name="uielement-list"></a>Liste des éléments d’interface  
 **Imprimer un message**  
 Imprime un message, à l’aide de la syntaxe DebuggerDisplay. Pour plus d’informations, consultez [à l’aide de l’attribut DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md).  
  
 Cette zone de texte prend également en charge les mots clés spéciaux (tels que $ADDRESS) qui peuvent être utilisés par eux-mêmes ou entre les accolades d’une expression DebuggerDisplay. Les mots clés disponibles sont répertoriés dans la boîte de dialogue.  
  
 **Continuer l’exécution**  
 Ce contrôle est activé uniquement lorsque **imprimer un Message** est sélectionné. Ce contrôle est sélectionné, vous pouvez utiliser un point d’arrêt comme un point de trace pour effectuer le suivi de l’exécution de votre programme, au lieu d’arrêt lorsque l’emplacement est atteint.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des points d’arrêt](../debugger/using-breakpoints.md)   
 [Utilisation de l’attribut DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)