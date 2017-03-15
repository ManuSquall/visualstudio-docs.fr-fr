---
title: "Erreur du compilateur CS1017 | Microsoft Docs"
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
  - "CS1017"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1017"
ms.assetid: e0902e8a-b042-4711-a8a6-83456a3f88cb
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1017
Des clauses Catch ne peuvent pas suivre la clause catch générale d'une instruction try  
  
 Un bloc `catch` qui n’accepte pas de paramètres doit être le dernier d’une série de blocs `catch`. Pour plus d’informations sur les exceptions, consultez [Instructions de gestion des exceptions](/dotnet/csharp/language-reference/keywords/exception-handling-statements).  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1017 :  
  
```  
// CS1017.cs using System; namespace x { public class b : Exception { } public class a { public static void Main() { try { } catch   // CS1017, must be last catch { } catch(b) { throw; } } } }  
```