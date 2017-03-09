---
title: "Erreur du compilateur CS0424 | Microsoft Docs"
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
  - "CS0424"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0424"
ms.assetid: 09ae482c-255a-4f99-8dc8-ba31c3ea8c71
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0424
'class' : une classe avec l’attribut ComImport ne peut pas spécifier une classe de base  
  
 Spécifier l’attribut <xref:System.Runtime.InteropServices.ComImportAttribute> implique que l’implémentation de la classe soit importée à partir d’un module COM. Les méthodes ou champs supplémentaires hérités de la classe de base ne peuvent pas être ajoutés à l’implémentation définie dans le module COM.  
  
 L’exemple suivant génère l’erreur CS0424 :  
  
```  
// CS0424.cs // compile with: /target:library using System.Runtime.InteropServices; public class A {} [ ComImport, Guid("7ab770c7-0e23-4d7a-8aa2-19bfad479829") ] class B : A {}   // CS0424 error  
```