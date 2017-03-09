---
title: "System.CLSCompliantAttribute ne peut pas &#234;tre appliqu&#233; &#224; la propri&#233;t&#233; &#39;Get&#39; ou &#39;Set&#39; | Microsoft Docs"
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
  - "vbc40043"
  - "BC40043"
helpviewer_keywords: 
  - "BC40043"
ms.assetid: 2ff45c09-32be-4ca9-b42a-63ce2536db7d
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# System.CLSCompliantAttribute ne peut pas &#234;tre appliqu&#233; &#224; la propri&#233;t&#233; &#39;Get&#39; ou &#39;Set&#39;
Une définition de propriété applique l’attribut <xref:System.CLSCompliantAttribute> à son instruction `Get` ou `Set`.  
  
 Pour qu’une propriété soit conforme au [Indépendance du langage et composants indépendants du langage](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\), la propriété entière doit être marquée comme `<CLSCompliant(True)>`. Vous devez appliquer <xref:System.CLSCompliantAttribute> à [Property Statement](/dotnet/visual-basic/language-reference/statements/property-statement), et non à l’instruction `Get` ou `Set`.  
  
 Quand vous appliquez <xref:System.CLSCompliantAttribute> à un élément de programmation, vous affectez au paramètre `isCompliant` de l’attribut la valeur `True` ou `False` pour indiquer la conformité ou la non\-conformité. Comme il n’existe pas de valeur par défaut pour ce paramètre, vous devez fournir une valeur.  
  
 Si vous n’appliquez pas <xref:System.CLSCompliantAttribute> à un élément, il est considéré comme étant non conforme.  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuration d'avertissements en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID d’erreur :** BC40043  
  
### Pour corriger cette erreur  
  
-   Supprimez <xref:System.CLSCompliantAttribute> à de l’instruction `Get` ou `Set`.  
  
-   Si la propriété doit être conforme CLS, marquez l’instruction `Property` comme étant `<CLSCompliant(True)>`.  
  
## Voir aussi  
 [\<PAVE OVER\> Écriture de code conforme CLS](http://msdn.microsoft.com/fr-fr/4c705105-69a2-4e5e-b24e-0633bc32c7f3)   
 [Get Statement](/dotnet/visual-basic/language-reference/statements/get-statement)   
 [Set Statement](/dotnet/visual-basic/language-reference/statements/set-statement)