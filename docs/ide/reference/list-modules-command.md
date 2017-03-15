---
title: "Afficher les modules, commande | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.listmodules"
helpviewer_keywords: 
  - "Debug.ListModules (commande)"
  - "Afficher les modules (commande)"
  - "ListModules (commande)"
ms.assetid: 3cb73774-6ac0-43b2-b781-75ed47175bfd
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# Afficher les modules, commande
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Répertorie les modules pour le processus en cours.  
  
## Syntaxe  
  
```  
Debug.ListModules [/Address:yes|no] [/Name:yes|no] [/Order:yes|no]  
[/Path:yes|no] [/Process:yes|no] [/SymbolFile:yes|no]  
[/SymbolStatus:yes|no] [/Timestamp:yes|no] [/Version:yes|no]  
```  
  
#### Paramètres  
 \/Address:`yes|no`  
 Facultatif.  Spécifie s'il faut afficher les adresses mémoire des modules.  La valeur par défaut est `yes`  
  
 \/Name:`yes|no`  
 Facultatif.  Spécifie s'il faut afficher les noms des modules.  La valeur par défaut est `yes`  
  
 \/Order:`yes|no`  
 Facultatif.  Spécifie s'il faut afficher l'ordre des modules.  La valeur par défaut est `no`  
  
 \/Path:`yes|no`  
 Facultatif.  Spécifie s'il faut afficher les chemins des modules.  La valeur par défaut est `yes`  
  
 \/Process:`yes|no`  
 Facultatif.  Spécifie s'il faut afficher les processus des modules.  La valeur par défaut est `no`  
  
 \/SymbolFile:`yes|no`  
 Facultatif.  Spécifie s'il faut afficher les fichiers de symboles des modules.  La valeur par défaut est `no`  
  
 \/SymbolStatus:`yes|no`  
 Facultatif.  Spécifie s'il faut afficher les statuts de symboles des modules.  La valeur par défaut est `yes`  
  
 \/Timestamp:`yes|no`  
 Facultatif.  Spécifie s'il faut afficher les horodateurs des modules.  La valeur par défaut est `no`  
  
 \/Version:`yes|no`  
 Facultatif.  Spécifie s'il faut afficher les versions des modules.  La valeur par défaut est `no`  
  
## Notes  
  
## Exemple  
 Cet exemple répertorie les noms du module, adresses et horodatages pour le processus actuel.  
  
```  
Debug.ListModules /Address:yes /Name:yes /Order:no /Path:no /Process:no /SymbolFile:no /SymbolStatus:no /Timestamp:yes /Version:no  
```  
  
## Voir aussi  
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Commande, fenêtre](../../ide/reference/command-window.md)   
 [Comment : utiliser la fenêtre Modules](../../debugger/how-to-use-the-modules-window.md)