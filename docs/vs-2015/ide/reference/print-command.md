---
title: Imprimer, commande | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 65d78387c6d60d0b432db9aab175fbfe8dc2869b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68203567"
---
# <a name="print-command"></a>Imprimer, commande
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Évalue une expression ou affiche le texte spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Debug.Print text  
```  
  
## <a name="arguments"></a>Arguments  
 `text`  
 Obligatoire. Expression à évaluer ou texte à afficher.  
  
## <a name="remarks"></a>Remarques  
 Vous pouvez utiliser le point d’interrogation (?) comme alias pour cette commande. Ainsi, la commande  
  
```  
>Debug.Print expA  
```  
  
 peut également être écrite  
  
```  
>? expA  
```  
  
 Les deux versions de cette commande retournent la valeur courante de l’expression `expA`.  
  
## <a name="example"></a>Exemples  
  
```  
>Debug.Print varA  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Évaluer l’instruction, commande](../../ide/reference/evaluate-statement-command.md)   
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Fenêtre Commande](../../ide/reference/command-window.md)   
 [Zone Rechercher/Commande](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
