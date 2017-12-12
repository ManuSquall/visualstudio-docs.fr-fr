---
title: Afficher les threads, commande | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: debug.listthreads
helpviewer_keywords:
- ListThreads command
- list threads command
- Debug.ListThreads command
ms.assetid: 34b665c0-d46f-4c1a-a066-b678eba5ac54
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: fa71ec1c6eb8ac50d957782dda02a2c3fb59a3c2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="list-threads-command"></a>Afficher les threads, commande
Affiche une liste des threads du programme en cours.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Debug.ListThreads [index]  
```  
  
## <a name="arguments"></a>Arguments  
 `index`  
 Facultatif. Sélectionne un thread par son index pour en faire le thread actuel.  
  
## <a name="remarks"></a>Remarques  
 Une fois spécifié, l’argument `index` marque le thread indiqué comme étant le thread actuel. Un astérisque (*) est affiché dans la liste en regard du thread actuel.  
  
## <a name="example"></a>Exemple  
  
```  
>Debug.ListThreads   
```  
  
## <a name="see-also"></a>Voir aussi  
 [Afficher la pile d’appels, commande](../../ide/reference/list-call-stack-command.md)   
 [Afficher le code machine, commande](../../ide/reference/list-disassembly-command.md)   
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Fenêtre Commande](../../ide/reference/command-window.md)   
 [Zone Rechercher/Commande](../../ide/find-command-box.md)   
 [Alias de commande Visual Studio](../../ide/reference/visual-studio-command-aliases.md)