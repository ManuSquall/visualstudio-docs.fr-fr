---
title: "Le type d&#233;l&#233;gu&#233; &#39;&lt;nom_d&#233;l&#233;gu&#233;&gt;&#39; de l’&#233;v&#233;nement &#39;&lt;nom_&#233;v&#233;nement&gt;&#39; n’est pas conforme CLS | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc40050"
  - "vbc40050"
helpviewer_keywords: 
  - "BC40050"
ms.assetid: 92f5be26-9a82-46d4-bf97-005f2c7ca424
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le type d&#233;l&#233;gu&#233; &#39;&lt;nom_d&#233;l&#233;gu&#233;&gt;&#39; de l’&#233;v&#233;nement &#39;&lt;nom_&#233;v&#233;nement&gt;&#39; n’est pas conforme CLS
[Event Statement](/dotnet/visual-basic/language-reference/statements/event-statement) utilise un délégué pour spécifier sa signature, mais [Delegate Statement](/dotnet/visual-basic/language-reference/statements/delegate-statement) est marqué comme étant `<CLSCompliant(False)>` ou n’est pas marqué.  
  
 Quand vous appliquez l’attribut <xref:System.CLSCompliantAttribute> à un élément de programmation, vous affectez au paramètre `isCompliant` de l’attribut la valeur `True` ou `False` pour indiquer la conformité ou la non\-conformité. Comme il n’existe pas de valeur par défaut pour ce paramètre, vous devez fournir une valeur.  
  
 Si vous n’appliquez pas <xref:System.CLSCompliantAttribute> à un élément, il est considéré comme étant non conforme.  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuration d'avertissements en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID d’erreur :** BC40050  
  
### Pour corriger cette erreur  
  
-   Si vous exigez la conformité CLS et que vous contrôlez la définition du délégué, appliquez <xref:System.CLSCompliantAttribute> à sa déclaration pour le marquer comme étant `<CLSCompliant(True)>`.  
  
-   Si vous ne contrôlez pas la définition du délégué ou que vous ne pouvez pas le marquer comme étant conforme, supprimez <xref:System.CLSCompliantAttribute> de l’instruction `Event` ou marquez\-le comme étant `<CLSCompliant(False)>`.  
  
## Voir aussi  
 [\<PAVE OVER\> Écriture de code conforme CLS](http://msdn.microsoft.com/fr-fr/4c705105-69a2-4e5e-b24e-0633bc32c7f3)