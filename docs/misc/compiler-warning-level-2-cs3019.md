---
title: "Avertissement du compilateur (niveau&#160;2) CS3019 | Microsoft Docs"
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
  - "CS3019"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3019"
ms.assetid: b41117cf-8956-4989-93fd-9903812e2d2f
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;2) CS3019
La vérification de conformité CLS ne sera pas effectuée sur 'type', car il n’est pas visible hors de cet assembly.  
  
 Cet avertissement se produit lorsqu’un type ou un membre qui a l’attribut <xref:System.CLSCompliantAttribute> n’est pas visible à partir d’un autre assembly. Pour résoudre cette erreur, supprimez l’attribut sur les classes ou les membres qui ne sont pas visibles à partir de l’autre assembly, ou rendez le type ou les membres visibles. Pour plus d’informations sur la conformité CLS, consultez [\<PAVE OVER\> Écriture d’un code conforme CLS](http://msdn.microsoft.com/fr-fr/4c705105-69a2-4e5e-b24e-0633bc32c7f3).  
  
## Exemple  
 L’exemple suivant génère l’avertissement CS3019 :  
  
```  
// CS3019.cs // compile with: /W:2 using System; [assembly: CLSCompliant(true)] // To fix the error, remove the next line [CLSCompliant(true)]  // CS3019 class C { [CLSCompliant(false)]  // CS3019 void Foo() { } static void Main() { } }  
```  
  
## Voir aussi  
 [Indépendance du langage et composants indépendants du langage](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)