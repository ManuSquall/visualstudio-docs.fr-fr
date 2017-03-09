---
title: "Erreur du compilateur CS0160 | Microsoft Docs"
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
  - "CS0160"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0160"
ms.assetid: 4ef07061-8ef5-42d9-b043-3f81307d569f
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0160
Une clause catch précédente intercepte déjà toutes les exceptions de this ou d’un super type \('type'\)  
  
 Une série d’instructions **catch** doit être classée dans l’ordre décroissant de dérivation. Par exemple, les objets les plus dérivés doivent figurer en premier.  
  
 Pour plus d’informations, consultez [Instructions de gestion des exceptions](/dotnet/csharp/language-reference/keywords/exception-handling-statements) et [Exceptions et gestion des exceptions](/dotnet/csharp/programming-guide/exceptions/exceptions-and-exception-handling).  
  
 L’exemple suivant génère l’avertissement CS0160 :  
  
```  
// CS0160.cs public class MyClass2 : System.Exception {} public class MyClass { public static void Main() { try {} catch(System.Exception) {}   // Second-most derived; should be second catch catch(MyClass2) {}   // CS0160  Most derived; should be first catch } }  
```