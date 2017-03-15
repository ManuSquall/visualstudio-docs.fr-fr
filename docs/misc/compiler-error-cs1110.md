---
title: "Erreur du compilateur CS1110 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1110"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1110"
ms.assetid: 5b571a76-1891-4f33-b23d-7c4cc654a05f
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1110
Impossible d’utiliser le modificateur 'this' sur le premier paramètre de la déclaration de méthode sans une référence à System.Core.dll. Ajoutez une référence à System.Core.dll ou supprimez le modificateur 'this' de la déclaration de méthode.  
  
 Les méthodes d’extension sont prises en charge dans la version 3.5 ou ultérieure du .NET Framework. Les méthodes d’extension génèrent des métadonnées qui marquent la méthode avec un attribut. La classe d’attributs se trouve dans system.core.dll.  
  
### Pour corriger cette erreur  
  
1.  Comme indiqué par le message, ajoutez une référence à System.Core.dll ou supprimez le modificateur `this` de la déclaration de méthode.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1110 si le fichier n’est pas compilé avec une référence à System.Core.dll :  
  
```  
// cs1110.cs // CS1110 // Compile with: /target:library public static class Extensions { public static bool Test(this bool b) { return b; } }  
```  
  
## Voir aussi  
 [Méthodes d'extension](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods)