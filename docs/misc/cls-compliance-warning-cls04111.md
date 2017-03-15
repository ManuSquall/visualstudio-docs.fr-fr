---
title: "Avertissement de conformit&#233; CLS CLS04111 | Microsoft Docs"
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
  - "CLS04111"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS04111"
ms.assetid: 4b445ce7-d823-4cf3-b971-1c181be5fa41
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Avertissement de conformit&#233; CLS CLS04111
Les attributs doivent être de type 'System::Attribute' ou hériter de celui\-ci  
  
 Pour être conforme CLS, un attribut personnalisé doit hériter de System::Attribute.  Un attribut qui n’a pas hérité de System::Attribute a été appliqué à un type.  
  
 La déclaration suivante \(en langage d’assembly MSIL\) montre ce qui peut provoquer l’avertissement CLS04111 :  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Object  
```  
  
 Pour résoudre cet avertissement, faites dériver l’attribut de System::Attribute :  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Attribute  
```