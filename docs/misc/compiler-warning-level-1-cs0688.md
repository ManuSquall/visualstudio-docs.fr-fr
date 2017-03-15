---
title: "Avertissement du compilateur (niveau&#160;1) CS0688 | Microsoft Docs"
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
  - "CS0688"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0688"
ms.assetid: 8ce5af36-663e-46e8-87e9-bb32555796ae
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;1) CS0688
'méthode1' a une demande de liaison, mais se substitue à ou implémente 'méthode2' qui n’a pas une demande de liaison. Une faille de sécurité existe.  
  
 La demande de liaison définie sur la méthode de classe dérivée peut facilement être contournée en appelant la méthode de classe de base. Pour éliminer la faille de sécurité, il faut que la méthode de classe de base utilise également la demande de liaison. Pour plus d’informations, consultez [Demand et LinkDemand](http://msdn.microsoft.com/fr-fr/1ab877f2-70f4-4e0d-8116-943999dfe8f5).  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0688. Pour résoudre l’avertissement sans modifier la classe de base, supprimez l’attribut de sécurité de la méthode de substitution. Le problème de sécurité ne sera pas résolu.  
  
```  
// CS0688.cs // compile with: /W:1 using System; using System.Security.Permissions; class Base { //Uncomment the following line to close the security hole //[FileIOPermission(SecurityAction.LinkDemand, All=@"C:\\")] public virtual void DoScaryFileStuff() { } } class Derived: Base { [FileIOPermission(SecurityAction.LinkDemand, All=@"C:\\")] // CS0688 public override void DoScaryFileStuff() { } static void Main() { } }  
```