---
title: "Avertissement du compilateur (niveau&#160;2) CS0279 | Microsoft Docs"
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
  - "CS0279"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0279"
ms.assetid: 5e5faa8f-3d5b-4999-aa62-ff7f131a3e04
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;2) CS0279
'nom\_type' n’implémente pas le modèle 'nom\_modèle'. 'nom\_méthode' est static ou non public.  
  
 Il existe plusieurs instructions en langage C\# qui reposent sur des modèles définis, telles que `foreach` et `using`. Par exemple, `foreach` repose sur la classe de collection qui implémente le modèle énumérable. Cette erreur se produit lorsque le compilateur est incapable d’effectuer la correspondance car une méthode est déclarée `static` ou non `public`. Les méthodes dans les modèles doivent obligatoirement être des instances de classes et être public.  
  
## Exemple  
 L’exemple suivant génère l’avertissement CS0279 :  
  
```  
// CS0279.cs using System; using System.Collections; public class myTest : IEnumerable { IEnumerator IEnumerable.GetEnumerator() { yield return 0; } internal IEnumerator GetEnumerator() { yield return 0; } public static void Main() { foreach (int i in new myTest()) {}  // CS0279 } }  
```