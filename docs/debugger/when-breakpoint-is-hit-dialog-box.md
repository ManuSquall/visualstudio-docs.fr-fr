---
title: Lorsque le point d’arrêt est boîte de dialogue d’accès | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 2d2d0940764e64f9179eb8346c271afa6136b72f
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31475036"
---
# <a name="when-breakpoint-is-hit-dialog-box"></a>Lorsque le point d'arrêt est atteint, boîte de dialogue
Avec cette boîte de dialogue, vous pouvez personnaliser l’action qui se produit lorsqu’un point d’arrêt est atteint.  
  
## <a name="uielement-list"></a>Liste des éléments d’interface  
 **Impression d’un Message**  
 Imprime un message, à l’aide de la syntaxe DebuggerDisplay. Pour plus d’informations, consultez [à l’aide de l’attribut DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md).  
  
 Cette zone de texte prend également en charge les mots clés spéciaux (tels que $ADDRESS) qui peuvent être utilisés par eux-mêmes, ou entre les accolades d’une expression DebuggerDisplay. Les mots clés disponibles sont répertoriés dans la boîte de dialogue.  
  
 **Poursuivre l’exécution**  
 Ce contrôle est activé uniquement lorsque **imprimer un Message** est sélectionnée. Ce contrôle est sélectionné, vous pouvez utiliser un point d’arrêt comme un point de trace pour tracer l’exécution de votre programme, au lieu d’arrêt lorsque l’emplacement est atteint.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de points d’arrêt](../debugger/using-breakpoints.md)   
 [Utilisation de l’attribut DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)