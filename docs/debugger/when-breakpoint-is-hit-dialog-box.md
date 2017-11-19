---
title: "Lorsque le point d’arrêt est boîte de dialogue d’accès | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.whenbreakpointishit
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
ms.assetid: 476e3d98-cf35-4338-b124-cd0f3010d854
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2e91841f1146d23305577cc00059f0bf9d505a90
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="when-breakpoint-is-hit-dialog-box"></a>Lorsque le point d'arrêt est atteint, boîte de dialogue
Avec cette boîte de dialogue, vous pouvez personnaliser l’action qui se produit lorsqu’un point d’arrêt est atteint.  
  
## <a name="uielement-list"></a>Liste UIElement  
 **Impression d’un Message**  
 Imprime un message, à l’aide de la syntaxe DebuggerDisplay. Pour plus d’informations, consultez [à l’aide de l’attribut DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md).  
  
 Cette zone de texte prend également en charge les mots clés spéciaux (tels que $ADDRESS) qui peuvent être utilisés par eux-mêmes, ou entre les accolades d’une expression DebuggerDisplay. Les mots clés disponibles sont répertoriés dans la boîte de dialogue.  
  
 **Poursuivre l’exécution**  
 Ce contrôle est activé uniquement lorsque **imprimer un Message** est sélectionnée. Ce contrôle est sélectionné, vous pouvez utiliser un point d’arrêt comme un point de trace pour tracer l’exécution de votre programme, au lieu d’arrêt lorsque l’emplacement est atteint.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de points d’arrêt](../debugger/using-breakpoints.md)   
 [Utilisation de l’attribut DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)