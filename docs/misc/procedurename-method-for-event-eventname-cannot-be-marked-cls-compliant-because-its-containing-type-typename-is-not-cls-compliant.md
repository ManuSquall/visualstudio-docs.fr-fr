---
title: "La m&#233;thode &#39;&lt;nom_proc&#233;dure&gt;&#39; pour l’&#233;v&#233;nement &#39;&lt;nom_&#233;v&#233;nement&gt;&#39; ne peut pas &#234;tre marqu&#233;e comme conforme CLS, car son type conteneur &#39;&lt;nom_type&gt;&#39; n’est pas conforme CLS | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc40053"
  - "bc40053"
helpviewer_keywords: 
  - "BC40053"
ms.assetid: 5f7aaf64-b5e6-4f97-9ebd-44cd4c7e8bf5
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La m&#233;thode &#39;&lt;nom_proc&#233;dure&gt;&#39; pour l’&#233;v&#233;nement &#39;&lt;nom_&#233;v&#233;nement&gt;&#39; ne peut pas &#234;tre marqu&#233;e comme conforme CLS, car son type conteneur &#39;&lt;nom_type&gt;&#39; n’est pas conforme CLS
Un événement personnalisé déclare une procédure `AddHandler` ou `RemoveHandler` et la marque comme `<CLSCompliant(True)>`, mais l’événement est défini dans un type qui est marqué comme `<CLSCompliant(False)>` ou qui n’est pas marqué.  
  
 Quand vous appliquez <xref:System.CLSCompliantAttribute> à un élément de programmation, vous affectez au paramètre `isCompliant` de l’attribut la valeur `True` ou `False` pour indiquer la conformité ou la non\-conformité. Il n’existe pas de valeur par défaut pour ce paramètre et vous devez fournir une valeur.  
  
 Si vous n’appliquez pas <xref:System.CLSCompliantAttribute> à un élément, il est considéré comme étant non conforme.  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuration d'avertissements en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID d’erreur :** BC40053  
  
### Pour corriger cette erreur  
  
-   Si vous avez besoin de la conformité CLS, définissez l’événement dans un type qui est conforme CLS.  
  
-   Si vous souhaitez que l’événement reste dans son type contenant, supprimez <xref:System.CLSCompliantAttribute> de sa définition ou marquez\-le comme `<CLSCompliant(False)>`.  
  
## Voir aussi  
 [How to: Declare Custom Events To Avoid Blocking](../Topic/How%20to:%20Declare%20Custom%20Events%20To%20Avoid%20Blocking%20\(Visual%20Basic\).md)   
 [How to: Declare Custom Events To Conserve Memory](../Topic/How%20to:%20Declare%20Custom%20Events%20To%20Conserve%20Memory%20\(Visual%20Basic\).md)   
 [NOT IN BUILD : AddHandler et RemoveHandler](http://msdn.microsoft.com/fr-fr/a7a24bd2-519a-46fe-8a2c-2b9df2ca28ef)   
 [\<PAVE OVER\> Écriture d’un code conforme CLS](http://msdn.microsoft.com/fr-fr/4c705105-69a2-4e5e-b24e-0633bc32c7f3)