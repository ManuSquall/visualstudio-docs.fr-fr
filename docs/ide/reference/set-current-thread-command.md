---
title: "Définir le thread en cours, commande │ Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- debug.setcurrentthread
helpviewer_keywords:
- Set Current Thread command
- Debug.SetCurrentThread command
ms.assetid: 9917ed1d-6c30-4d94-b2f0-69acce74f1b2
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 24a3f7d50d90769fe64b3657a0327eb8c96b7b42
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="set-current-thread-command"></a>Définir le thread en cours, commande
Définit le thread spécifié comme thread actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Debug.SetCurrentThread index  
```  
  
## <a name="arguments"></a>Arguments  
 `index`  
 Obligatoire. Sélectionne un thread par son index.  
  
## <a name="example"></a>Exemple  
  
```  
>Debug.SetCurrentThread 1  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Fenêtre Commande](../../ide/reference/command-window.md)   
 [Zone Rechercher/Commande](../../ide/find-command-box.md)   
 [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)