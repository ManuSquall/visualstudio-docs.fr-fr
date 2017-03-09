---
title: "Erreur du compilateur CS0400 | Microsoft Docs"
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
  - "CS0400"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0400"
ms.assetid: 58f91f3b-30f4-433b-9a13-0cff258a2630
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0400
Le type ou le nom d’espace de noms 'identifier' est introuvable dans l’espace de noms global \(une référence d’assembly est\-elle manquante ?\)  
  
 L’identificateur utilisé avec l’opérateur de portée globale \(`::`\) est introuvable dans l’espace de noms global. Une référence d’assembly contenant l’identificateur est peut\-être manquante, ou l’identificateur est peut être déclaré dans une classe ou un espace de noms différent de l’espace de noms global. Cette erreur peut également se produire si un identificateur global n’est pas déclaré ou est mal orthographié.  
  
 Pour éviter cette erreur, recherchez la déclaration de l’identificateur et vérifiez l’orthographe ; si la déclaration se trouve dans un assembly différent, vérifiez que vous disposez de la référence d’assembly appropriée. Si l’identificateur est déclaré dans un autre type ou espace de noms, utilisez le nom qualifié complet après ::. L’exemple suivant génère l’erreur CS0400 :  
  
```  
// CS0400.cs class C { public static void Main() { // CS0400 - D could not be found // in the global namespace. global::D d = new global::D(); } }  
```