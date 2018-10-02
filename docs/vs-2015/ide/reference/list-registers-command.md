---
title: Afficher les registres, commande | Microsoft Docs
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
- debug.listregisters
helpviewer_keywords:
- list registers command
- Debug.ListRegisters command
- ListRegisters command
ms.assetid: 19a9d789-f6c9-46b3-b1f6-4934fc33e055
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c9ff1287bb4c92d074c0a0e123d48ddb7e61cc90
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47503605"
---
# <a name="list-registers-command"></a>Afficher les registres, commande
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [afficher les registres, commande](https://docs.microsoft.com/visualstudio/ide/reference/list-registers-command).  
  
  
Affiche la valeur des registres sélectionnés et vous permet de modifier la liste de registres à afficher.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Debug.ListRegisters [/Display [{register|registerGroup}...]] [/List]  
[/Watch [{register|registerGroup}...]]  
[/Unwatch [{register|registerGroup}...]]  
```  
  
## <a name="switches"></a>Commutateurs  
 /Display [{`register`&#124;`registerGroup`}...]  
 Affiche les valeurs du `register` ou `registerGroup` spécifié. Si aucun `register` ni `registerGroup` n’est spécifié, la liste par défaut de registres est affichée. Si aucun commutateur n’est spécifié, le comportement est le même. Exemple :  
  
 `Debug.ListRegisters /Display eax`  
  
 est équivalent à  
  
 `Debug.ListRegisters eax`  
  
 /List  
 Affiche tous les groupes de registres dans la liste.  
  
 /Watch [{`register`&#124;`registerGroup`}...]  
 Ajoute une ou plusieurs valeurs de `register` ou `registerGroup` dans la liste.  
  
 /Unwatch [{`register`&#124;`registerGroup`}...]  
 Supprime une ou plusieurs valeurs de `register` ou `registerGroup` de la liste.  
  
## <a name="remarks"></a>Notes  
 L’alias `r` peut être utilisé à la place de `Debug.ListRegisters`.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise l’alias `Debug.ListRegisters` `r` pour afficher les valeurs du groupe de registres `Flags`.  
  
```  
r /Display Flags  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Concepts de base du débogage : fenêtre Registres](../../debugger/debugging-basics-registers-window.md)   
 [Guide pratique pour utiliser la fenêtre Registres](../../debugger/how-to-use-the-registers-window.md)



