---
title: "Erreur du compilateur CS0026 | Microsoft Docs"
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
  - "CS0026"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0026"
ms.assetid: 8767fbc1-8ba7-4e88-a9f9-7e620411882b
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0026
Le mot clé 'this' n'est pas valide dans un initialiseur de propriété statique, de méthode statique ou de champ statique  
  
 Le mot clé [this](/dotnet/csharp/language-reference/keywords/this) fait référence à un objet qui est une instance d’un type. Dans la mesure où les méthodes statiques sont indépendantes de toute instance de la classe conteneur, le mot clé « this » est sans signification et n’est donc pas autorisé. Pour plus d’informations, consultez [Classes statiques et membres de classe statique](/dotnet/csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members) et [Objets](/dotnet/csharp/programming-guide/classes-and-structs/objects).  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0026 :  
  
```  
// CS0026.cs public class A { public static int i = 0; public static void Main() { // CS0026 this.i = this.i + 1; // Try the following line instead: // i = i + 1; } }  
```