---
title: Imprimer, commande | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: e518b3c6ffc3520b408e7c1bfb1fd1703e40a8de
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47496286"
---
# <a name="print-command"></a>Imprimer, commande
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [commande Imprimer](https://docs.microsoft.com/visualstudio/ide/reference/print-command).  
  
  
Évalue une expression ou affiche le texte spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Debug.Print text  
```  
  
## <a name="arguments"></a>Arguments  
 `text`  
 Obligatoire. Expression à évaluer ou texte à afficher.  
  
## <a name="remarks"></a>Notes  
 Vous pouvez utiliser le point d’interrogation (?) comme alias pour cette commande. Ainsi, la commande  
  
```  
>Debug.Print expA  
```  
  
 peut également être écrite  
  
```  
>? expA  
```  
  
 Les deux versions de cette commande retournent la valeur courante de l’expression `expA`.  
  
## <a name="example"></a>Exemple  
  
```  
>Debug.Print varA  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Évaluer l’instruction, commande](../../ide/reference/evaluate-statement-command.md)   
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Fenêtre Commande](../../ide/reference/command-window.md)   
 [Zone Rechercher/Commande](../../ide/find-command-box.md)   
 [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)



