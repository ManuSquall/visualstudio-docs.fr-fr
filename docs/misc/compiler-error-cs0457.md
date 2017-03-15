---
title: "Erreur du compilateur CS0457 | Microsoft Docs"
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
  - "CS0457"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0457"
ms.assetid: 5d5cf762-c817-4468-9455-59e966b8c140
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0457
Conversions définies par l’utilisateur ambiguës 'nom\_méthode\_conversion1' et 'nom\_méthode\_conversion2' lors de la conversion de 'nom\_type1' en 'nom\_type2'  
  
 Deux méthodes de conversion sont applicables et le compilateur est incapable de déterminer celle à utiliser.  
  
 L’un des scénarios pouvant provoquer cette erreur est le suivant :  
  
-   Vous souhaitez convertir une classe A en classe B, où A et B ne sont pas liées.  
  
-   A est dérivée d’A0, et il existe une méthode qui convertit A0 en B.  
  
-   B a une sous\-classe B1 et il existe une méthode qui convertit A en B1.  
  
 Le compilateur considère les deux méthodes de conversion de manière égale, car la première conversion fournit le meilleur type de destination et la deuxième fournit le meilleur type source. Le compilateur ne pouvant choisir, cette erreur est générée. Pour résoudre cette erreur, écrivez une nouvelle méthode explicite qui convertit A en B.  
  
 Cette erreur peut aussi se produire s’il existe deux méthodes qui convertissent A en B. Pour résoudre le problème, spécifiez la conversion à utiliser par un cast explicite.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0457.  
  
```  
// CS0457.cs using System; public class A { } public class G0 {  } public class G1<R> : G0 {  } public class H0 { public static implicit operator G0(H0 h) { return new G0(); } } public class H1<R> : H0 { public static implicit operator G1<R>(H1<R> h) { return new G1<R>(); } } public class Test { public static void F0(G0 g) {  } public static void Main() { H1<A> h1a = new H1<A>(); F0(h1a);   // CS0457 } }  
```