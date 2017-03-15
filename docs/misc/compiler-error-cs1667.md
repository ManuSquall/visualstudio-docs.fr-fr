---
title: "Erreur du compilateur CS1667 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1667"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1667"
ms.assetid: 59f64828-58bc-487c-862a-75537e21d4ea
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1667
L’attribut 'attribute' n’est pas valide sur les accesseurs de propriété ni d’événement. Il n’est valide que sur les déclarations 'declaration type'.  
  
 Cette erreur se produit si vous utilisez un attribut sur un accesseur de propriété ou d’événement, alors que vous devriez l’utiliser sur la propriété ou sur l’événement. Cette erreur peut se produire avec les attributs <xref:System.CLSCompliantAttribute>, <xref:System.Diagnostics.ConditionalAttribute> et <xref:System.ObsoleteAttribute>.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1670 :  
  
```  
// CS1667.cs using System; public class C { private int i; //Try this instead: //[Obsolete] public int ObsoleteProperty { [Obsolete]  // CS1667 get { return i; } set { i = value; } } public static void Main() { } }  
```