---
title: "Avertissement du compilateur (niveau&#160;1) CS3016 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS3016"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3016"
ms.assetid: b2ae721d-13ab-4e9d-a288-741d7825defe
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;1) CS3016
L'utilisation de tableaux en tant qu'arguments d'attributs n'est pas conforme CLS  
  
 Le passage d’un tableau à un attribut n’est pas conforme à la spécification CLS \(Common Language Specification\). Pour plus d’informations sur la conformité CLS, consultez [Écriture d’un code conforme CLS](http://msdn.microsoft.com/fr-fr/4c705105-69a2-4e5e-b24e-0633bc32c7f3) et [Indépendance du langage et composants indépendants du langage](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md).  
  
## Exemple  
 L’exemple suivant génère l’avertissement CS3016 :  
  
```  
// CS3016.cs using System; [assembly : CLSCompliant(true)] [C(new int[] {1, 2})]   // CS3016 // try the following line instead // [C()] class C : Attribute { public C() { } public C(int[] a) { } public static void Main () { } }  
```