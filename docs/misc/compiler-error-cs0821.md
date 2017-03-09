---
title: "Erreur du compilateur CS0821 | Microsoft Docs"
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
  - "CS0821"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0821"
ms.assetid: ef449115-93e8-4fa5-848a-d30dc7f68ddf
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0821
Les variables locales implicitement typées ne peuvent pas être fixed  
  
 Les variables locales implicitement typées et les types anonymes ne sont pas pris en charge dans le contexte `fixed`.  
  
### Pour corriger cette erreur  
  
1.  Supprimez le modificateur `fixed` de la variable ou affectez un type explicite à celle\-ci.  
  
## Exemple  
 Le code suivant génère l’erreur CS0821 :  
  
```  
class A { static int x; public static int Main() { unsafe { fixed (var p = &x) { } } return -1; } }  
```  
  
## Voir aussi  
 [Variables locales implicitement typées](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)