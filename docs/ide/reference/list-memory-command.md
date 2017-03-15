---
title: "Afficher la m&#233;moire, commande | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.listmemory"
helpviewer_keywords: 
  - "Debug.ListMemory (commande)"
  - "Afficher la mémoire (commande)"
  - "ListMemory (commande)"
ms.assetid: a84de361-a6a6-4f6d-96aa-a0d4a424371e
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Afficher la m&#233;moire, commande
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Affiche le contenu de la plage mémoire spécifiée.  
  
## Syntaxe  
  
```  
Debug.ListMemory [/ANSI|Unicode] [/Count:number] [/Format:formattype]  
[/Hex|Signed|Unsigned] [expression]  
```  
  
## Arguments  
 `expression`  
 Facultatif.  Adresse mémoire à partir de laquelle la mémoire doit être affichée.  
  
## Commutateurs  
 \/ANSI&#124;Unicode  
 Facultatif.  Affiche la mémoire sous la forme de caractères ANSI ou Unicode correspondant aux octets de mémoire.  
  
 \/Count:`number`  
 Facultatif.  Détermine le nombre d'octets à afficher, à partir de l'adresse mémoire spécifiée avec l'argument `expression`.  
  
 \/Format:`formattype`  
 Facultatif.  Type du format selon lequel les informations sur la mémoire sont affichées dans la fenêtre **Mémoire** ; le format peut être OneByte, TwoBytes, FourBytes, EightBytes, Float \(32\-bit\) ou Double \(64\-bit\).  Si le format OneByte est utilisé, le commutateur `/Unicode` n'est pas disponible.  
  
 \/Hex&#124;Signed&#124;Unsigned  
 Facultatif.  Spécifie le format d'affichage des nombres : signé \(Signed\), non signé \(Unsigned\) ou hexadécimal \(Hex\).  
  
## Notes  
 Au lieu d'écrire une commande **Debug.ListMemory** complète avec tous ses commutateurs, vous pouvez appeler la commande à l'aide d'alias préparamétrés avec certains commutateurs prédéfinis à des valeurs spécifiées.  Par exemple, au lieu d'entrer :  
  
```  
>Debug.ListMemory /Format:float /Count:30 /Unicode  
```  
  
 vous pouvez écrire :  
  
```  
>df /Count:30 /Unicode  
```  
  
 Voici une liste des alias disponibles pour la commande **Debug.ListMemory** :  
  
|Alias|Commande et commutateurs|  
|-----------|------------------------------|  
|**d**|Debug.ListMemory|  
|**da**|Debug.ListMemory \/Ansi|  
|**db**|Debug.ListMemory \/Format:OneByte|  
|**dc**|Debug.ListMemory \/Format:FourBytes \/Ansi|  
|**dd**|Debug.ListMemory \/Format:FourBytes|  
|**df**|Debug.ListMemory \/Format:Float|  
|**dq**|Debug.ListMemory \/Format:EightBytes|  
|**du**|Debug.ListMemory \/Unicode|  
  
## Exemple  
  
```  
>Debug.ListMemory /Format:float /Count:30 /Unicode  
```  
  
## Voir aussi  
 [Afficher la pile d'appels, commande](../../ide/reference/list-call-stack-command.md)   
 [Afficher les threads, commande](../../ide/reference/list-threads-command.md)   
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Commande, fenêtre](../../ide/reference/command-window.md)   
 [Zone Rechercher\/Commande](../../ide/find-command-box.md)   
 [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)