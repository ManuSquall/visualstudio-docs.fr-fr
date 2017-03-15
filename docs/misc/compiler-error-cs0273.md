---
title: "Erreur du compilateur CS0273 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0273"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0273"
ms.assetid: 851ad056-feee-48fd-834c-578a1a13e926
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0273
Le modificateur d’accessibilité de l’accesseur 'property\_accessor' doit être plus restrictif que la propriété ou l’indexeur 'property'  
  
 Le modificateur d’accessibilité de l’accesseur set\/get doit être plus restrictif que la propriété ou l’indexeur 'property\/indexer'  
  
 Cette erreur se produit quand vous déclarez une propriété ou un indexeur avec un modificateur d’accès moins restrictif que celui de l’un de ses accesseurs. Pour résoudre cette erreur, utilisez le modificateur d’accès approprié sur la propriété ou sur l’accesseur set. Pour plus d'informations, consultez [Accessibilité des accesseurs](/dotnet/csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility).  
  
## Exemple  
 Cet exemple contient une propriété interne avec une méthode set interne. L’exemple suivant génère l’erreur CS0273.  
  
```  
// CS0273.cs // compile with: /target:library public class MyClass { internal int Property { get { return 0; } internal set {}   // CS0273 // try the following line instead // private set {} } }  
```