---
title: "Afficher le code machine, commande | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.listdisassembly"
helpviewer_keywords: 
  - "Debug.ListDisassembly (commande)"
  - "Afficher le code machine (commande)"
ms.assetid: eb363e35-e86a-4121-966f-991210c27e2a
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# Afficher le code machine, commande
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Démarre le processus de débogage et vous permet de spécifier comment les erreurs doivent être gérées.  
  
## Syntaxe  
  
```  
Debug.ListDisassembly [/count:number] [/endaddress:expression]  
[/codebytes:yes|no] [/source:yes|no] [/symbolnames:yes|no]  
[/linenumbers:yes|no]  
```  
  
## Commutateurs  
 Chaque commutateur peut être appelé en utilisant sa forme complète ou abrégée.  
  
 \/count: `number` \[ou\] \/c: `number` \[ou\] \/length: `number` \[ou\] \/l: `number`  
 Facultatif.  Nombre d'instructions à afficher.  La valeur par défaut est 8.  
  
 \/endaddress: `expression` \[ou\] \/e: `expression`  
 Facultatif.  Adresse à laquelle le code machine doit s'arrêter.  
  
 \/codebytes:`yes`&#124;`no` \[ou\] \/bytes:`yes`&#124;`no` \[ou\] \/b:`yes`&#124;`no`  
 Facultatif.  Spécifie si les octets de code doivent être affichés.  La valeur par défaut est `no`  
  
 \/source:`yes`&#124;`no` \[ou\] \/s:`yes`&#124;`no`  
 Facultatif.  Spécifie si le code source doit être affiché.  La valeur par défaut est `no`  
  
 \/symbolnames:`yes`&#124;`no` \[ou\] \/names:`yes`&#124;`no` \[ou\] \/n:`yes`&#124;`no`  
 Facultatif.  Spécifie si les noms de symbole doivent être affichés.  La valeur par défaut est `yes`  
  
 \[\/linenumbers:`yes`&#124;`no`\]  
 Facultatif.  Active l'affichage des numéros de ligne associés au code source.  Le commutateur \/source doit avoir la valeur `yes` pour utiliser le commutateur \/linenumbers.  
  
## Exemple  
  
```  
>Debug.ListDisassembly  
```  
  
## Voir aussi  
 [Afficher la pile d'appels, commande](../../ide/reference/list-call-stack-command.md)   
 [Afficher les threads, commande](../../ide/reference/list-threads-command.md)   
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Commande, fenêtre](../../ide/reference/command-window.md)   
 [Zone Rechercher\/Commande](../../ide/find-command-box.md)   
 [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)