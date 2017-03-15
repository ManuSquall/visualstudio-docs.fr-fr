---
title: "Erreur du compilateur CS0712 | Microsoft Docs"
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
  - "CS0712"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0712"
ms.assetid: cde64c0c-3953-4563-8c24-8b646230bbb8
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0712
Impossible de créer une instance de la classe statique 'static class'  
  
 Il n’est pas possible de créer des instances de classes statiques. Les classes statiques sont conçues pour contenir des méthodes et champs statiques, mais elles ne peuvent pas être instanciées.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0712 :  
  
```  
// CS0712.cs public static class SC { } public class CMain { public static void Main() { SC sc = new SC();  // CS0712 } }  
```