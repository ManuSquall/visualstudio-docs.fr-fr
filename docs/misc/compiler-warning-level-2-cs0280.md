---
title: "Avertissement du compilateur (niveau&#160;2) CS0280 | Microsoft Docs"
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
  - "CS0280"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0280"
ms.assetid: 9b453478-92aa-4fd2-9b87-780fd138603a
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;2) CS0280
'type' n’implémente pas le modèle 'pattern name'. La signature de 'method name' est incorrecte.  
  
 Deux instructions en langage C\#, **foreach** et **using**, s’appuient sur des modèles prédéfinis, « collection » et « ressource » respectivement. Cet avertissement se produit quand le compilateur ne peut pas faire correspondre l’une de ces instructions à son modèle en raison d’une signature incorrecte d’une méthode. Par exemple, le modèle « collection » nécessite la présence d’une méthode appelée <xref:System.Collections.IEnumerator.MoveNext%2A> qui ne prend aucun paramètre et retourne un `boolean`. Votre code peut contenir une méthode <xref:System.Collections.IEnumerator.MoveNext%2A> qui a un paramètre ou qui retourne peut\-être un objet.  
  
 Le modèle « ressource » et `using` fournissent un autre exemple. Le modèle « ressource » nécessite la méthode <xref:System.IDisposable.Dispose%2A> ; si vous définissez une propriété portant le même nom, vous obtenez cet avertissement.  
  
 Pour y remédier, assurez\-vous que les signatures de méthode dans votre type correspondent aux signatures des méthodes correspondantes dans le modèle et assurez\-vous de n’avoir aucune propriété portant le même nom qu’une méthode requise par le modèle.  
  
## Exemple  
 L’exemple suivant génère l’avertissement CS0280.  
  
```  
// CS0280.cs using System; using System.Collections; public class ValidBase: IEnumerable { IEnumerator IEnumerable.GetEnumerator() { yield return 0; } internal IEnumerator GetEnumerator() { yield return 0; } } class Derived : ValidBase { // field, not method new public int GetEnumerator; } public class Test { public static void Main() { foreach (int i in new Derived()) {}   // CS0280 } }  
```