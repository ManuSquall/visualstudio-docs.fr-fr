---
title: "La version personnalis&#233;e de &#39;System.Runtime.CompilerServices.ExtensionAttribute&#39; trouv&#233;e par le compilateur n’est pas valide | Microsoft Docs"
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
  - "vbc36558"
  - "bc36558"
helpviewer_keywords: 
  - "BC36558"
ms.assetid: f47d310a-95fd-4340-bda2-21262c217dbb
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La version personnalis&#233;e de &#39;System.Runtime.CompilerServices.ExtensionAttribute&#39; trouv&#233;e par le compilateur n’est pas valide
La version personnalisée de 'System.Runtime.CompilerServices.ExtensionAttribute' trouvée par le compilateur n’est pas valide. Ses indicateurs d’utilisation d’attribut doivent être définis pour autoriser les assemblys, les classes et les méthodes.  
  
 La version personnalisée de <xref:System.Runtime.CompilerServices.ExtensionAttribute?displayProperty=fullName> trouvée par le compilateur ne définit pas ses indicateurs d’utilisation d’attribut pour permettre l’application de l’attribut à des assemblys, des méthodes et des classes. L’application à au moins ces trois éléments de programme est obligatoire.  
  
 **ID d’erreur :** BC36558  
  
### Pour corriger cette erreur  
  
-   Modifiez la définition de l’attribut pour qu’il soit applicable au moins aux assemblys, méthodes et classes, comme illustré dans les exemples suivants.  
  
-   Utilisez <xref:System.Runtime.CompilerServices.ExtensionAttribute?displayProperty=fullName> au lieu de la version personnalisée.  
  
## Exemple  
 L’exemple suivant utilise l’attribut `AttributeUsage` pour spécifier les éléments de programme auxquels la nouvelle version de `ExtensionAttribute` peut s’appliquer. L’exemple spécifie trois membres de l’énumération `AttributeTargets` : `Assembly`, `Class` et `Method`. L’omission de l’un de ces éléments provoque cette erreur.  
  
```  
Namespace System.Runtime.CompilerServices <AttributeUsage(AttributeTargets.Assembly Or _ AttributeTargets.Class Or AttributeTargets.Method)> Class ExtensionAttribute Inherits System.Attribute ' Definitions of methods, fields, and properties. End Class End Namespace  
```  
  
 Vous pouvez également autoriser l’application de `ExtensionAttribute` à tous les éléments de programme à l’aide du membre `All` de `AttributeTargets`.  
  
```  
<AttributeUsage(AttributeTargets.All)>  
```  
  
 La suppression de la ligne `AttributeUsage`, comme indiqué dans le code suivant, produit le même résultat.  
  
```  
Namespace System.Runtime.CompilerServices Class ExtensionAttribute Inherits System.Attribute ' Definitions of methods, fields, and properties. End Class End Namespace  
```  
  
## Voir aussi  
 <xref:System.Runtime.CompilerServices.ExtensionAttribute>   
 [NOT IN BUILD : Vue d’ensemble des attributs en Visual Basic](http://msdn.microsoft.com/fr-fr/0d0cff64-892d-4f57-83bd-bef388553d4f)   
 [NOT IN BUILD : Attributs personnalisés en Visual Basic](http://msdn.microsoft.com/fr-fr/d72d8a5c-8f64-4614-b15b-cad66845d047)   
 [méthodes d'extension.](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [NOT IN BUILD : Procédure : définition de vos propres attributs](http://msdn.microsoft.com/fr-fr/039609c4-ec43-4f44-945f-aa3b5b535c6a)   
 [Écriture des attributs personnalisés](../Topic/Writing%20Custom%20Attributes.md)