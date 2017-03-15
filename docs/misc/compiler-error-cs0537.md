---
title: "Erreur du compilateur CS0537 | Microsoft Docs"
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
  - "CS0537"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0537"
ms.assetid: 6c832a5f-47dc-4f60-aed8-69ac328af44b
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0537
La classe System.Object ne peut pas posséder de classe de base ni implémenter une interface  
  
 L’erreur CS0537 se produit lors de la reconstruction des bibliothèques de classes <xref:System> et où <xref:System.Object> dérive d’une autre classe. Vous ne rencontrerez très probablement pas cette erreur. Dans la cas contraire, ne dérivez pas <xref:System.Object> d’une classe ou interface : il s’agit de la racine de toute la hiérarchie de classes .NET Framework, et par conséquent, il ne dérive pas d’un autre élément.