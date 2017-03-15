---
title: "Could not bind to dependency &#39;assembly&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cantbinddependency"
ms.assetid: 0f76190d-d57e-4e0e-bec4-532aec978d08
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Could not bind to dependency &#39;assembly&#39;
Une des références de votre projet contient elle\-même une référence d'assembly \(dépendance\) qui a été localisée, mais qui ne constitue pas un assembly valide.  Cette erreur n'empêche pas la génération du projet.  Une erreur d'exécution peut cependant se produire.  
  
 La situation implique que les trois conditions suivantes se vérifient :  
  
-   Plusieurs fichiers sur votre disque portent le même nom.  
  
-   Un des fichiers n'est pas un assembly, mais l'autre l'est.  
  
-   Votre chemin aux références recherche en premier lieu dans le répertoire qui contient le fichier ne constituant pas un assembly.  
  
 **Pour corriger cette erreur**  
  
-   Modifiez l'ordre dans lequel votre projet effectue les recherches dans les répertoires, lors de la recherche des références.  Pour plus d'informations, consultez [NIB: Reference Paths Dialog Box \(Visual Basic\)](http://msdn.microsoft.com/fr-fr/8e549b39-7256-456a-8fd7-089b23facf9c).  
  
## Voir aussi  
 [Dépannage de références rompues](../ide/troubleshooting-broken-references.md)   
 [Comment : ajouter ou supprimer des références à l'aide de la boîte de dialogue Ajouter une référence](http://msdn.microsoft.com/fr-fr/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Assemblies in the Common Language Runtime](http://msdn.microsoft.com/fr-fr/33a0bc6a-6bb3-44c7-ada7-4a046e8c0945)