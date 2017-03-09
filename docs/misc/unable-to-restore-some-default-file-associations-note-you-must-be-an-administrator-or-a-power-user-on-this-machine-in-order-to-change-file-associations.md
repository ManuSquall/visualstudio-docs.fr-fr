---
title: "Impossible de restaurer certaines associations de fichiers par d&#233;faut. Remarque&#160;: Vous devez &#234;tre administrateur ou utilisateur avec pouvoir sur cet ordinateur pour &#234;tre autoris&#233; &#224; modifier les associations de fichiers. | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.Message.0x00006A85"
  - "VS_E_RESTOREFILEASSOCS"
ms.assetid: 449c5608-83e3-4ddd-91f1-1061916995b3
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Impossible de restaurer certaines associations de fichiers par d&#233;faut. Remarque&#160;: Vous devez &#234;tre administrateur ou utilisateur avec pouvoir sur cet ordinateur pour &#234;tre autoris&#233; &#224; modifier les associations de fichiers.
Cette erreur se produit quand le commutateur de ligne de commande devenv \/AssociateFiles est utilisé, mais que les droits d’utilisateur actuels ne permettent pas l’accès à la section HKEY\_CLASSES\_ROOT du Registre. Si vous exécutez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sur [!INCLUDE[wiprlhext](../misc/includes/wiprlhext_md.md)], vous devez exécuter devenv en tant qu’administrateur pour utiliser le commutateur \/AssociateFiles \(devenv.exe\).  
  
### Pour corriger cette erreur  
  
-   Connectez\-vous en tant qu’administrateur et réessayez.  
  
## Voir aussi  
 [User Rights and Visual Studio](http://msdn.microsoft.com/fr-fr/d5c55084-1e7b-4b61-b478-137db01c0fc0)   
 [Commutateurs de la ligne de commande de Devenv](../ide/reference/devenv-command-line-switches.md)