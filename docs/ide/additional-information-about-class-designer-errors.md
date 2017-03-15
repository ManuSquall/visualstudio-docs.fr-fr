---
title: "Additional Information About Class Designer Errors | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.classdesigner.CPlusPlusViewInDiagramNoTypeFound"
  - "vs.classdesigner.CPlusPlusNoTypeFound"
  - "vs.classdesigner.CannotShowBaseType"
  - "vs.classdesigner.MatchOrphanTypesAtLoad"
  - "vs.classdesigner.CannotShowType"
  - "vs.classdesigner.AssociationTypeNotFoundError"
  - "vs.classdesigner.ViewInDiagramNoTypesFound"
  - "vs.classdesigner.CannotImplementInterface"
  - "vs.classdesigner.CannotShowImplementedInterface"
  - "vs.classdesigner.ViewInDiagramUnparsableTypeFound"
  - "vs.classdesigner.AssociationTypeNotFound"
  - "vs.classdesigner.CPlusPlusTypeCannotBeAdded"
helpviewer_keywords: 
  - "errors, class diagrams"
  - "errors, Class Designer"
  - "error messages, Class Designer"
  - "Class Designer [Visual Studio], errors"
  - "error messages, class diagrams"
  - "class diagrams, errors"
ms.assetid: 79d70e70-704c-4255-ab68-c10d6949470e
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# Additional Information About Class Designer Errors
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le Concepteur de classes n'effectue pas le suivi de l'emplacement de vos fichiers sources ; par conséquent, si vous modifiez votre structure de projet ou si vous déplacez des fichiers sources dans votre projet, le Concepteur de classes peut perdre la trace du type \(surtout le type de source d'un typedef, de classes de base ou de types d'associations\).  Vous pouvez recevoir une erreur telle que **Class Designer is unable to display this type**.  Dans ce cas, refaites glisser le code source modifié ou déplacé vers le diagramme de classes pour le réafficher.  
  
 Vous pouvez obtenir de l'aide sur d'autres erreurs et avertissements dans les ressources suivantes :  
  
 [Working with Visual C\+\+ Code \(Class Designer\)](../ide/working-with-visual-cpp-code-class-designer.md)  
 Inclut des informations de dépannage sur l'affichage de C\+\+ dans un diagramme de classes.  
  
 [Forum du Concepteur de classes Visual Studio](http://go.microsoft.com/fwlink/?LinkId=160754)  
 Propose un forum de questions relatives au Concepteur de classes.  
  
## Voir aussi  
 [Designing and Viewing Classes and Types](../ide/designing-and-viewing-classes-and-types.md)