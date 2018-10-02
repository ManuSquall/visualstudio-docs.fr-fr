---
title: Lorsque le point d’arrêt est boîte de dialogue de positionnement | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.whenbreakpointishit
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- SQL
- VB
- CSharp
- C++
ms.assetid: 476e3d98-cf35-4338-b124-cd0f3010d854
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 650e390abde6f3ad99e5a0c30591c8d1530df692
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47502490"
---
# <a name="when-breakpoint-is-hit-dialog-box"></a>Lorsque le point d'arrêt est atteint, boîte de dialogue
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [lors de point d’arrêt est atteint boîte de dialogue](https://docs.microsoft.com/visualstudio/debugger/when-breakpoint-is-hit-dialog-box).  
  
Avec cette boîte de dialogue, vous pouvez personnaliser l’action qui se produit lorsqu’un point d’arrêt est atteint.  
  
## <a name="uielement-list"></a>Liste des éléments d’interface  
 **Imprimer un Message**  
 Imprime un message, à l’aide de la syntaxe DebuggerDisplay. Pour plus d’informations, consultez [à l’aide de l’attribut DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md).  
  
 Cette zone de texte prend également en charge les mots clés spéciaux (tels que $ADDRESS) qui peuvent être utilisés par eux-mêmes ou entre les accolades d’une expression DebuggerDisplay. Les mots clés disponibles sont répertoriés dans la boîte de dialogue.  
  
 **Continuer l’exécution**  
 Ce contrôle est activé uniquement lorsque **imprimer un Message** est sélectionné. Ce contrôle est sélectionné, vous pouvez utiliser un point d’arrêt comme un point de trace pour effectuer le suivi de l’exécution de votre programme, au lieu d’arrêt lorsque l’emplacement est atteint.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de points d’arrêt](../debugger/using-breakpoints.md)   
 [Utilisation de l’attribut DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)



