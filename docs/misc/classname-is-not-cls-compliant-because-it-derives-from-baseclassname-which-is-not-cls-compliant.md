---
title: "&#39;&lt;nom_classe&gt;&#39; n’est pas conforme&#160;CLS, car il d&#233;rive de &#39;&lt;nom_classe_de_base&gt;&#39;, qui n’est pas conforme&#160;CLS | Microsoft Docs"
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
  - "vbc40026"
  - "bc40026"
helpviewer_keywords: 
  - "BC40026"
ms.assetid: debcd5e4-75e7-4b14-a6cc-18f1009fe52c
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nom_classe&gt;&#39; n’est pas conforme&#160;CLS, car il d&#233;rive de &#39;&lt;nom_classe_de_base&gt;&#39;, qui n’est pas conforme&#160;CLS
Une classe ou une interface est marquée comme `<CLSCompliant(True)>` quand elle est dérivée d’un type ou implémente un type qui est marqué comme `<CLSCompliant(False)>` ou qui n’est pas marqué.  
  
 Pour qu’une classe ou une interface soit conforme CLS \([Indépendance du langage et composants indépendants du langage](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)\), l’intégralité de sa hiérarchie d’héritage doit être conforme. Cela signifie que chaque type dont elle hérite, directement ou indirectement, doit être conforme. De même, si une classe implémente une ou plusieurs interfaces, celles\-ci doivent toutes être conformes au sein de leurs hiérarchies d’héritage.  
  
 Quand vous appliquez l’attribut <xref:System.CLSCompliantAttribute> à un élément de programmation, vous affectez au paramètre `isCompliant` de l’attribut la valeur `True` ou `False` pour indiquer la conformité ou la non\-conformité. Il n’existe pas de valeur par défaut pour ce paramètre et vous devez fournir une valeur.  
  
 Si vous n’appliquez pas <xref:System.CLSCompliantAttribute> à un élément, il est considéré comme étant non conforme.  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuration d'avertissements en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID d’erreur :** BC40026  
  
### Pour corriger cette erreur  
  
-   Si la conformité CLS est obligatoire, définissez ce type dans une autre hiérarchie d’héritage ou dans un autre schéma d’implémentation.  
  
-   Si le type doit rester au sein de sa hiérarchie d’héritage ou de son schéma d’implémentation actuels, supprimez <xref:System.CLSCompliantAttribute> de sa définition ou marquez\-le comme `<CLSCompliant(False)>`.  
  
## Voir aussi  
 [\<PAVE OVER\> Écriture d’un code conforme CLS](http://msdn.microsoft.com/fr-fr/4c705105-69a2-4e5e-b24e-0633bc32c7f3)