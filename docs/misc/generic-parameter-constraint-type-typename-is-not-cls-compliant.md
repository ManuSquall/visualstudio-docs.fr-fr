---
title: "Le type de contrainte de param&#232;tre g&#233;n&#233;rique &lt;typename&gt; n’est pas conforme&#160;CLS | Microsoft Docs"
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
  - "bc40040"
  - "vbc40040"
helpviewer_keywords: 
  - "BC40040"
ms.assetid: c640dd59-56a9-43ed-b199-32a60f7b9b06
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le type de contrainte de param&#232;tre g&#233;n&#233;rique &lt;typename&gt; n’est pas conforme&#160;CLS
Un type générique est marqué comme `<CLSCompliant(True)>`, mais une contrainte sur l’un de ses paramètres de type spécifie un type qui est marqué comme `<CLSCompliant(False)>`, qui n’est pas marqué ou qui n’est pas qualifié car il s’agit d’un type non conforme.  
  
 Pour qu’un type soit conforme à la [Indépendance du langage et composants indépendants du langage](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\), il doit utiliser uniquement les types conformes CLS. Cette règle s’applique également aux contraintes sur les paramètres de type d’un type générique.  
  
 Les types de données [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] suivants ne sont pas conformes CLS :  
  
-   [SByte Data Type](/dotnet/visual-basic/language-reference/data-types/sbyte-data-type)  
  
-   [UInteger Data Type](/dotnet/visual-basic/language-reference/data-types/uinteger-data-type)  
  
-   [ULong Data Type](/dotnet/visual-basic/language-reference/data-types/ulong-data-type)  
  
-   [UShort Data Type](/dotnet/visual-basic/language-reference/data-types/ushort-data-type)  
  
 Lorsque vous appliquez l’attribut <xref:System.CLSCompliantAttribute> à un élément de programmation, vous affectez au paramètre `isCompliant` de l’attribut la valeur `True` ou `False` pour indiquer la conformité ou la non\-conformité. Il n’existe pas de valeur par défaut pour ce paramètre et vous devez fournir une valeur.  
  
 Si vous n’appliquez pas <xref:System.CLSCompliantAttribute> à un élément, il est considéré comme étant non conforme.  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuration d'avertissements en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID d’erreur :** BC40040  
  
### Pour corriger cette erreur  
  
-   Si le type générique doit prendre un paramètre de type contraint par ce type particulier, supprimez <xref:System.CLSCompliantAttribute>. Le type ne peut pas être conforme CLS.  
  
-   Si le type générique doit être conforme CLS, remplacez le type de cette contrainte par le type conforme CLS le plus proche. Par exemple, vous pouvez utiliser `Integer` au lieu de `UInteger` si vous n’avez pas besoin de la plage de valeurs située au\-dessus de 2 147 483 647. Si vous avez besoin de la plage étendue, vous pouvez remplacer `UInteger` par `Long`.  
  
## Voir aussi  
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [\<PAVE OVER\> Écriture d’un code conforme CLS](http://msdn.microsoft.com/fr-fr/4c705105-69a2-4e5e-b24e-0633bc32c7f3)