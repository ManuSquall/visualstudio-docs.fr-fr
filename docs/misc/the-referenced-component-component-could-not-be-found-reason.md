---
title: "The referenced component &#39;component&#39; could not be found. &lt;reason&gt; | Microsoft Docs"
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
  - "vs.tasklisterror.referencenotfound"
ms.assetid: 35491b4d-e3e4-4e7c-8ac1-3adb09c1ef58
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The referenced component &#39;component&#39; could not be found. &lt;reason&gt;
Le système de projet n'a pas pu résoudre une référence donnée.  Le fait de double\-cliquer sur cet élément de la liste des tâches donne le focus à l'Explorateur de solutions et sélectionne la référence qui n'a pas pu être résolue.  
  
 Modifiez la propriété [ReferencePaths](http://msdn.microsoft.com/fr-fr/8e549b39-7256-456a-8fd7-089b23facf9c) de sorte que les répertoires adéquats soient inclus dans le chemin d'accès.  
  
 Cette erreur peut se produire si vous déplacez un projet sur un autre ordinateur.  La propriété `ReferencePath` est stockée sous la forme d'un chemin d'accès absolu.  Si la référence R1 réside dans c:\\R\\R1.dll sur l'ordinateur A, le fichier .vbproj.user ou .csproj.user stockera c:\\R au sein de la propriété `ReferencePath`.  Si toutefois sur l'ordinateur B, R1 réside dans d:\\R\\R1.dll, le système de projet ne pourra pas trouver R1, car d:\\R ne figure pas dans le chemin d'accès de référence.  
  
 Le scénario de contrôle de code source est un scénario similaire.  En cas d'inscription dans un projet, le fichier .vbproj.user \(ou .csproj.user\) n'est pas copié sur votre ordinateur, car il n'est pas stocké dans le contrôle de code source.  Par conséquent, la valeur initiale de la propriété `ReferencePath` sera vide et les références s'appuyant sur `ReferencePath` pour la résolution ne seront pas résolues.  Pour plus d'informations, consultez Gestion des dépendances dans *Développement en équipe avec Visual Studio .NET et Visual SourceSafe*.  
  
 Cette erreur peut également se produire si un projet référencé ne se trouve pas dans la solution en cours.  
  
 Cette erreur indique que le projet risque de ne pas être généré.  
  
 Pour plus d'informations sur l'ajout de références, consultez [Dépannage de références rompues](../ide/troubleshooting-broken-references.md).  
  
## Voir aussi  
 [Gestion des références dans un projet](../ide/managing-references-in-a-project.md)