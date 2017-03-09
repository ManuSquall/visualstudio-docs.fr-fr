---
title: "Avertissement du compilateur (niveau&#160;2) CS0278 | Microsoft Docs"
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
  - "CS0278"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0278"
ms.assetid: 5418cbbe-bcec-4379-a6f6-410987beb96a
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;2) CS0278
'type' n’implémente pas le modèle 'nom\_modèle'. 'nom\_méthode' est ambigu avec 'nom\_méthode'.  
  
 Plusieurs instructions en C\# reposent sur des modèles définis, tels que `foreach` et `using`. Par exemple, `foreach` repose sur la classe de collection qui implémente le modèle « énumérable ».  
  
 L’erreur CS0278 peut se produire si le compilateur ne peut pas établir la correspondance en raison d’ambiguïtés. Par exemple, le modèle « énumérable » exige la présence d’une méthode appelée `MoveNext`. Or, il se peut que votre code contienne deux méthodes appelées `MoveNext`. Le compilateur tente alors de trouver une interface à utiliser, mais il est recommandé de déterminer et résoudre la cause de l’ambiguïté.  
  
 Pour plus d'informations, consultez [Comment : accéder à une classe de collection à l'aide de foreach](../Topic/How%20to:%20Access%20a%20Collection%20Class%20with%20foreach%20\(C%23%20Programming%20Guide\).md).  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0278 :  
  
```  
// CS0278.cs using System.Collections.Generic; public class myTest { public static void TestForeach<W>(W w) where W: IEnumerable<int>, IEnumerable<string> { foreach (int i in w) {}   // CS0278 } }  
```