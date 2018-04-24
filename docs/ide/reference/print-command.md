---
title: Imprimer, commande | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 66175f8aa1d371386793b892c0ead5b4dd1885b0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="print-command"></a>Imprimer, commande
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