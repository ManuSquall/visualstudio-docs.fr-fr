---
title: "Le type de projet n&#39;est pas pris en charge par cette installation. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.projectflavornotavailable"
ms.assetid: 50e92aff-3ce9-4600-94af-4a16e9dffc90
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Le type de projet n&#39;est pas pris en charge par cette installation.
Cette erreur se produit lorsque vous essayez d'ouvrir un type de projet qui requiert un Kit de développement logiciel \(SDK\) qui n'est pas installé avec Visual Studio.  Par exemple, cette erreur se produit si vous ouvrez Visual Studio sur un ordinateur qui n'a pas le Kit de développement Visual Studio installé puis que vous essayez d'ouvrir un fichier projet pour ce SDK, tel qu'un projet VSIX. \(Pour plus d'informations sur le Kit de développement Visual Studio, consultez [Extending Visual Studio](http://go.microsoft.com/fwlink/?LinkID=64968).\)  
  
## Solution possible  
 Vous devez vérifier que le Kit de développement logiciel adapté au type de projet que vous essayez d'ouvrir est installé.  
  
#### Pour vérifier si le Kit de développement logiciel est déjà installé  
  
1.  Dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet**.  
  
2.  Dans la boîte de dialogue **Nouveau projet**, développez le nœud **Installés**, puis le nœud **Modèles**. Enfin choisissez le nœud **Autres types de projet**.  
  
3.  Examinez les types de projets disponibles pour déterminer si le projet que vous essayez d'ouvrir l'est.  
  
 Si vous ne trouvez pas le type de projet que vous essayez d'ouvrir, vous n'avez pas installé le Kit de développement logiciel associé.  Vous devez rechercher et installer le Kit de développement logiciel associé pour ouvrir le type de projet.  
  
## Voir aussi  
 [Nouveautés de Visual Studio 2015](../ide/what-s-new-in-visual-studio-2015.md)   
 [Portage, migration et mise à niveau des projets Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)