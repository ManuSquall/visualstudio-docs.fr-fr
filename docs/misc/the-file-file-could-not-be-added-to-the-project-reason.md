---
title: "Le fichier &#39;fichier&#39; n’a pas pu &#234;tre ajout&#233; au projet. &lt;raison&gt; | Microsoft Docs"
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
  - "vs.tasklisterror.projfile_no_add_file"
ms.assetid: 8bd70556-596a-4e24-a71c-a340604ee93d
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Le fichier &#39;fichier&#39; n’a pas pu &#234;tre ajout&#233; au projet. &lt;raison&gt;
Un fichier lu dans le fichier .vbproj ou .csproj ne peut pas être ajouté au projet. Raisons possibles :  
  
-   Nom de fichier non valide.  
  
-   Fichier inclus dans un chemin. C’est le cas, par exemple, si vous avez un chemin relatif au projet Fichier1\\Fichier2.txt, mais qu’il existe également un dossier avec un chemin relatif Fichier1\\Fichier2.txt.  
  
-   L’élément existe déjà. Cela se produit quand un fichier est spécifié deux fois dans le fichier projet.  
  
-   Un lien existe déjà. La limitation suivante s’applique au système de projet [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] et [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] : il ne peut pas y avoir plusieurs liens portant le même nom dans le même projet. Cela signifie, par exemple, que vous ne pouvez pas spécifier un lien au fichier .vb à la fois dans le dossier A et le dossier B du projet.  
  
 Cette erreur est probablement due à une modification apportée manuellement au fichier projet.  
  
 Aucun fichier pour lequel ce diagnostic est affiché n’est ajouté au projet.  
  
## Voir aussi  
 [Fichiers projet](/visual-cpp/ide/project-files)   
 [NIB : Gestion des éléments dans les projets](http://msdn.microsoft.com/fr-fr/762e606b-7f44-4b66-97a1-e30a703654a0)