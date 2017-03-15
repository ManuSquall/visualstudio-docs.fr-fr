---
title: "Hi&#233;rarchies des classes de base virtuelles | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "classes (C++), les classes de base virtuelles"
  - "hiérarchies de classes, classes de base virtuelles"
  - "classes dérivées, considérations sur la hiérarchie (classe)"
  - "fonctions virtuelles, dans les hiérarchies de classe de base virtuelle"
  - "classes de base virtuelles"
  - "classes de base virtuelles, les hiérarchies"
  - "hiérarchies de classes de base virtuelles"
ms.assetid: d24fda17-f829-48d6-84ec-8100f26bc5cf
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Hi&#233;rarchies des classes de base virtuelles
Certaines hiérarchies de classes sont larges mais ont beaucoup de choses en commun. Le code commun est implémenté dans une classe de base, tandis que le code spécifique est dans les classes dérivées.  
  
 Il est important que les classes de base établissent un protocole par lequel les classes dérivées peuvent atteindre une fonctionnalité maximale. Ces fournisseurs sont généralement implémentées à l'aide de fonctions virtuelles. Parfois, la classe de base fournit une implémentation par défaut pour ces fonctions. Dans une hiérarchie de classes comme la hiérarchie `Document` dans la figure Exemple de graphique acyclique dirigé \(consultez [Héritage unique](/visual-cpp/cpp/single-inheritance)\), `Identify` et `WhereIs` sont deux fonctions utiles.  
  
 Lorsqu'elle est appelée, la fonction `Identify` retourne une identification correcte correspondant au type de document. Pour `Book`, un appel de fonction comme `doc->Identify()` doit retourner le nombre ISBN. En revanche, pour `HelpFile`, un nom de produit et un numéro de révision sont probablement plus appropriés. De même, `WhereIs` doit retourner une rangée et une étagère pour `Book`, mais pour `HelpFile` elle doit retourner un emplacement sur disque, tel qu'un répertoire et un nom de fichier.  
  
 Il est important que toutes les implémentations des fonctions `Identify` et `WhereIs` retournent le même type d'information. Dans ce cas, une chaîne de caractères est appropriée.  
  
 Ces fonctions sont implémentées comme fonctions virtuelles puis appelées à l'aide d'un pointeur vers une classe de base. La liaison au code réel se produit au moment de l'exécution, en sélectionnant la fonction `Identify` ou `WhereIs` correcte.  
  
## Voir aussi  
 [Vue d'ensemble des classes dérivées](../misc/overview-of-derived-classes.md)