---
title: Quand le point d’arrêt est atteint, boîte de dialogue | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9a7cd140a22c435df0875c089a69476d3e1e61cf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149406"
---
# <a name="when-breakpoint-is-hit-dialog-box"></a>Lorsque le point d'arrêt est atteint, boîte de dialogue
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette boîte de dialogue vous permet de personnaliser l’action qui se produit lorsqu’un point d’arrêt est atteint.  
  
## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur  
 **Imprimer un message**  
 Imprime un message à l’aide de la syntaxe DebuggerDisplay. Pour plus d’informations, consultez [utilisation de l’attribut DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md).  
  
 Cette zone de texte prend également en charge les mots clés spéciaux (tels que $ADDRESS) qui peuvent être utilisés par eux-mêmes ou entre les accolades d’une expression DebuggerDisplay. Les mots clés disponibles sont répertoriés dans la boîte de dialogue.  
  
 **Continuer l’exécution**  
 Ce contrôle est activé uniquement lorsque l’option **imprimer un message** est sélectionnée. Une fois ce contrôle sélectionné, vous pouvez utiliser un point d’arrêt comme point de trace pour suivre l’exécution de votre programme, au lieu de l’arrêter lorsque l’emplacement est atteint.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des points d’arrêt](../debugger/using-breakpoints.md)   
 [Utilisation de l’attribut DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)
