---
title: Afficher la pile des appels, commande | Microsoft Docs
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
- debug.listcallstack
helpviewer_keywords:
- list call stack command
- Debug.ListCallStack command
ms.assetid: a8b20bf2-81d2-4069-aea8-23e6b15b4347
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c4fafa521bb515169bd7fd694b08faf3707d4907
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47505077"
---
# <a name="list-call-stack-command"></a>Afficher la pile des appels, commande
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [pile, appelez liste commande](https://docs.microsoft.com/visualstudio/ide/reference/list-call-stack-command).  
  
  
Affiche la pile des appels actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Debug.ListCallStack [/Count:number] [/ShowTypes:yes|no]  
[/ShowNames:yes|no] [/ShowValues:yes|no] [/ShowModule:yes|no]  
[/ShowLineOffset:yes|no] [/ShowByteOffset:yes|no]  
[/ShowLanguage:yes|no] [/IncludeCallsAcrossThreads:yes|no]  
[/ShowExternalCode:yes|no] [Thread:n] [index]  
```  
  
## <a name="arguments"></a>Arguments  
 `index`  
 Facultatif. Définit le frame de pile actuel et n’affiche aucune sortie.  
  
## <a name="switches"></a>Commutateurs  
 Chaque commutateur peut être appelé à l’aide de sa forme complète ou abrégée.  
  
 /Count:`number` [ou] /C:`number`  
 Facultatif. Nombre maximal des piles d’appels à afficher. Par défaut, ce nombre est illimité.  
  
 /ShowTypes:`yes`&#124;`no` [ou] /T:`yes`&#124;`no`  
 Facultatif. Spécifie si les types de paramètre doivent être affichés. La valeur par défaut est `yes`.  
  
 /ShowNames:`yes`&#124;`no` [ou] /N:`yes`&#124;`no`  
 Facultatif. Spécifie si les noms de paramètres doivent être affichés. La valeur par défaut est `yes`.  
  
 /ShowValues:`yes`&#124;`no` [ou] /V:`yes`&#124;`no`  
 Facultatif. Spécifie si les valeurs de paramètre doivent être affichées. La valeur par défaut est `yes`.  
  
 /ShowModule:`yes`&#124;`no` [ou] /M:`yes`&#124;`no`  
 Facultatif. Spécifie si le nom du module doit être affiché. La valeur par défaut est `yes`.  
  
 /ShowLineOffset:`yes`&#124;`no` [ou] /#:`yes`&#124;`no`  
 Facultatif. Spécifie si l’offset de ligne doit être affiché. La valeur par défaut est `no`.  
  
 /ShowByteOffset:`yes`&#124;`no` [ou] /B:`yes`&#124;`no`  
 Facultatif. Spécifie si l’offset d’octet doit être affiché. La valeur par défaut est `no`.  
  
 /ShowLanguage:`yes`&#124;`no` [ou] /L:`yes`&#124;`no`  
 Facultatif. Spécifie si le langage doit être affiché. La valeur par défaut est `no`.  
  
 /IncludeCallsAcrossThreads:`yes`&#124;`no` [ou] /I:`yes`&#124;`no`  
 Facultatif. Spécifie si les appels à destination ou en provenance d’autres threads doivent être inclus. La valeur par défaut est `no`.  
  
 /ShowExternalCode:`yes`&#124;`no`  
 Facultatif. Spécifie s’il faut afficher Uniquement mon code pour la pile des appels. Quand Uniquement mon code est désactivé, tout le code non-utilisateur est affiché. Quand Uniquement mon code est activé, le code non-utilisateur est affiché comme `[external]` dans la sortie de la pile des appels.  
  
 Thread:`n`  
 Facultatif. Affiche la pile des appels pour le thread `n`. Si aucun thread n’est spécifié, affiche la pile des appels pour le thread actuel.  
  
## <a name="remarks"></a>Notes  
 Les modifications apportées aux arguments ou aux commutateurs s’appliquent aux futurs appels de cette commande. Exécutée seule, la commande Debug.ListCallStackby affiche toute la pile des appels. Si vous spécifiez un index, par exemple,  
  
```  
Debug.ListCallStack 2  
```  
  
 le frame de pile actuel est défini sur ce frame (dans le cas présent, le deuxième).  
  
 Vous pouvez également écrire cette commande en utilisant son alias prédéfini, kb. Par exemple, vous pouvez entrer  
  
```  
kb 2  
```  
  
 pour définir le frame de pile actuel sur le deuxième frame.  
  
## <a name="example"></a>Exemple  
  
```  
>Debug.CallStack /Count:4 /ShowTypes:yes  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Afficher le code machine, commande](../../ide/reference/list-disassembly-command.md)   
 [Afficher les threads, commande](../../ide/reference/list-threads-command.md)   
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Fenêtre Commande](../../ide/reference/command-window.md)   
 [Zone Rechercher/Commande](../../ide/find-command-box.md)   
 [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)



