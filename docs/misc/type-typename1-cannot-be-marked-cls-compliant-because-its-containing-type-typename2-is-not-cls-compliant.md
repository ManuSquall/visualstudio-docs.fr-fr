---
title: "Le type &#39;&lt;nom_type1&gt;&#39; ne peut pas &#234;tre marqu&#233; comme conforme CLS, car son type conteneur &#39;&lt;nom_type2&gt;&#39; n’est pas conforme CLS | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc40030"
  - "bc40030"
helpviewer_keywords: 
  - "BC40030"
ms.assetid: f1cfcf04-2a99-46ef-ac87-34cc2099125c
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le type &#39;&lt;nom_type1&gt;&#39; ne peut pas &#234;tre marqu&#233; comme conforme CLS, car son type conteneur &#39;&lt;nom_type2&gt;&#39; n’est pas conforme CLS
Une classe ou une interface est marquée comme `<CLSCompliant(True)>` quand elle est imbriquée dans un type qui est marqué comme `<CLSCompliant(False)>` ou qui n’est pas marqué.  
  
 Pour qu’une classe ou une interface soit conforme CLS \([Indépendance du langage et composants indépendants du langage](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)\), l’intégralité de sa hiérarchie de contenance doit être conforme. Cela signifie que chaque type dans lequel elle est imbriquée doit être conforme.  
  
 Quand vous appliquez l’attribut <xref:System.CLSCompliantAttribute> à un élément de programmation, vous affectez au paramètre `isCompliant` de l’attribut la valeur `True` ou `False` pour indiquer la conformité ou la non\-conformité. Il n’existe pas de valeur par défaut pour ce paramètre et vous devez fournir une valeur.  
  
 Si vous n’appliquez pas <xref:System.CLSCompliantAttribute> à un élément, il est considéré comme étant non conforme.  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuration d'avertissements en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID d’erreur :** BC40030  
  
### Pour corriger cette erreur  
  
-   Si la conformité CLS est requise, définissez ce type dans une autre hiérarchie de contenance.  
  
-   Si ce type doit rester au sein de sa hiérarchie de contenance actuelle, supprimez <xref:System.CLSCompliantAttribute> de sa définition ou marquez\-le comme `<CLSCompliant(False)>`.  
  
## Voir aussi  
 [\<PAVE OVER\> Écriture d’un code conforme CLS](http://msdn.microsoft.com/fr-fr/4c705105-69a2-4e5e-b24e-0633bc32c7f3)