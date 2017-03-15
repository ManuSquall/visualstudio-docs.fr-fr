---
title: "Erreur du compilateur CS0202 | Microsoft Docs"
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
  - "CS0202"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0202"
ms.assetid: 7088850f-c206-4b95-9586-a0fa3d876c0c
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0202
foreach exige que le type de retour 'type' de 'type.GetEnumerator\(\)' ait une méthode MoveNext publique appropriée et une propriété Current publique  
  
 Une fonction <xref:System.Collections.IEnumerable.GetEnumerator%2A>, utilisée pour activer l’utilisation d’instructions foreach, ne peut pas retourner un pointeur ou un tableau. Elle doit retourner une instance d’une classe qui est en mesure d’agir comme un énumérateur. Les conditions préalables pour servir d’énumérateur incluent une propriété Current publique et une méthode MoveNext publique.  
  
> [!NOTE]
>  En C\# 2.0, le compilateur génère automatiquement Current et MoveNext pour vous. Pour plus d’informations, consultez l’exemple de code dans [Interfaces génériques](/dotnet/csharp/programming-guide/generics/generic-interfaces).  
  
 L’exemple suivant génère l’erreur CS0202 :  
  
```  
// CS0202.cs public class C1 { public int Current { get { return 0; } } public bool MoveNext () { return false; } public static implicit operator C1 (int c1) { return 0; } } public class C2 { public int Current { get { return 0; } } public bool MoveNext () { return false; } public C1[] GetEnumerator () // try the following line instead // public C1 GetEnumerator () { return null; } } public class MainClass { public static void Main () { C2 c2 = new C2(); foreach (C1 x in c2)   // CS0202 { System.Console.WriteLine(x.Current); } } }  
```