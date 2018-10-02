---
title: Afficher le code machine, commande | Microsoft Docs
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
- debug.listdisassembly
helpviewer_keywords:
- Debug.ListDisassembly command
- list disassembly command
ms.assetid: eb363e35-e86a-4121-966f-991210c27e2a
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6834bc8f6c9bc3aacb95ae3705195fde32c4d6cb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47505218"
---
# <a name="list-disassembly-command"></a>Afficher le code machine, commande
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [afficher le code machine, commande](https://docs.microsoft.com/visualstudio/ide/reference/list-disassembly-command).  
  
  
Commence le processus de débogage et permet de spécifier comment les erreurs sont gérées.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Debug.ListDisassembly [/count:number] [/endaddress:expression]  
[/codebytes:yes|no] [/source:yes|no] [/symbolnames:yes|no]  
[/linenumbers:yes|no]  
```  
  
## <a name="switches"></a>Commutateurs  
 Chaque commutateur peut être appelé à l’aide de sa forme complète ou abrégée.  
  
 /count: `number` [ou] /c: `number` [ou] /length: `number` [ou] /l: `number`  
 Facultatif. Nombre d’instructions à afficher. La valeur par défaut est 8.  
  
 /endaddress: `expression` [ou] /e: `expression`  
 Facultatif. Adresse à laquelle le code machine doit s’arrêter.  
  
 /codebytes:`yes`&#124;`no` [ou] /bytes:`yes`&#124;`no` [ou] /b:`yes`&#124;`no`  
 Facultatif. Spécifie si les octets de code doivent être affichés. La valeur par défaut est `no`.  
  
 /source:`yes`&#124;`no` [ou] /s:`yes`&#124;`no`  
 Facultatif. Spécifie si le code source doit être affiché. La valeur par défaut est `no`.  
  
 /symbolnames:`yes`&#124;`no` [ou] /names:`yes`&#124;`no` [ou] /n:`yes`&#124;`no`  
 Facultatif. Spécifie si les noms de symbole doivent être affichés. La valeur par défaut est `yes`.  
  
 [/linenumbers:`yes`&#124;`no`]  
 Facultatif. Active l’affichage des numéros de ligne associés au code source. Le commutateur /source doit avoir la valeur `yes` pour utiliser le commutateur /linenumbers.  
  
## <a name="example"></a>Exemple  
  
```  
>Debug.ListDisassembly  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Afficher la pile d’appels, commande](../../ide/reference/list-call-stack-command.md)   
 [Afficher les threads, commande](../../ide/reference/list-threads-command.md)   
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Fenêtre Commande](../../ide/reference/command-window.md)   
 [Zone Rechercher/Commande](../../ide/find-command-box.md)   
 [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)



