---
title: "Le membre &#39;Mustoverride&#39; non conforme CLS n’est pas autoris&#233; dans un &lt;nom_classe&gt;&#39; conforme CLS | Microsoft Docs"
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
  - "bc40034"
  - "vbc40034"
helpviewer_keywords: 
  - "BC40034"
ms.assetid: 4eb36b3a-1bbe-4e99-9ecb-a12b8729b128
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le membre &#39;Mustoverride&#39; non conforme CLS n’est pas autoris&#233; dans un &lt;nom_classe&gt;&#39; conforme CLS
Une classe est marquée comme `<CLSCompliant(True)>`, mais elle contient une propriété ou une procédure `MustOverride` qui est marquée comme étant `<CLSCompliant(False)>` ou qui n’est pas marquée.  
  
 Quand une classe est conforme CLS \([Indépendance du langage et composants indépendants du langage](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)\), les applications qui utilisent cette classe accèdent uniquement aux membres qui sont également marqués comme `<CLSCompliant(True)>` et ignorent les membres qui ne le sont pas. Toutefois, les applications ne peuvent pas ignorer les propriétés ou les procédures `MustOverride`, car elles doivent y accéder pour les substituer.  
  
 Quand vous appliquez l’attribut <xref:System.CLSCompliantAttribute> à un élément de programmation, vous affectez au paramètre `isCompliant` de l’attribut la valeur `True` ou `False` pour indiquer la conformité ou la non\-conformité. Il n’existe pas de valeur par défaut pour ce paramètre et vous devez fournir une valeur.  
  
 Si vous n’appliquez pas <xref:System.CLSCompliantAttribute> à un élément, il est considéré comme étant non conforme.  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuration d'avertissements en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID d’erreur :** BC40034  
  
### Pour corriger cette erreur  
  
-   Si la conformité CLS est requise et si vous contrôlez le code source de la classe, marquez le membre comme `<CLSCompliant(True)>`.  
  
-   Si la conformité CLS est requise et si vous ne contrôlez pas le code source de la classe, ou si le code ne peut pas être conforme, définissez ce membre dans une autre classe.  
  
-   Si vous avez besoin que ce membre reste non conforme, supprimez le mot clé `MustOverride` de sa définition, supprimez la <xref:System.CLSCompliantAttribute> de la définition de classe ou marquez la classe comme `<CLSCompliant(False)>`.  
  
## Voir aussi  
 [MustOverride](/dotnet/visual-basic/language-reference/modifiers/mustoverride)   
 [\<PAVE OVER\> Écriture d’un code conforme CLS](http://msdn.microsoft.com/fr-fr/4c705105-69a2-4e5e-b24e-0633bc32c7f3)