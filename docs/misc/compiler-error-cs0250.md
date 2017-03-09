---
title: "Erreur du compilateur CS0250 | Microsoft Docs"
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
  - "CS0250"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0250"
ms.assetid: a994f361-6287-4db0-9ce1-e293a8190049
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0250
N’appelez pas directement la méthode Finalize de votre classe de base. Elle est appelée automatiquement par votre destructeur.  
  
 Un programme ne peut pas forcer le nettoyage des ressources de la classe de base.  
  
 Pour plus d’informations, consultez [Destructeurs et méthodes Finalize](http://msdn.microsoft.com/fr-fr/fd376774-1643-499b-869e-9546a3aeea70).  
  
 L’exemple suivant génère l’erreur CS0250 :  
  
```  
// CS0250.cs class B { } class C : B { ~C() { base.Finalize();   // CS0250 } public static void Main() { } }  
```