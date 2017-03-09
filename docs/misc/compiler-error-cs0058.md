---
title: "Erreur du compilateur CS0058 | Microsoft Docs"
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
  - "CS0058"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0058"
ms.assetid: 9535da60-03b9-41ab-93e1-e57b6440fca9
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0058
Accessibilité incohérente : le type de retour 'type' est moins accessible que le délégué 'delegate'  
  
 Une construction publique doit retourner un objet accessible publiquement. Pour plus d'informations, consultez [Modificateurs d'accès](/dotnet/csharp/programming-guide/classes-and-structs/access-modifiers).  
  
 L’exemple suivant génère l’erreur CS0058, car aucun modificateur d’accès n’est appliqué à MyClass. Un accès privé est donc attribué par défaut :  
  
```  
// CS0058.cs class MyClass // try the following line instead // public class MyClass { } public delegate MyClass MyClassDel();   // CS0058 public class A { public static void Main() { } }  
```  
  
## Voir aussi  
 [privées](/dotnet/csharp/language-reference/keywords/private)