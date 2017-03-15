---
title: "Avertissement de conformit&#233;&#160;CLS CLS04114 | Microsoft Docs"
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
  - "CLS04114"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS04114"
ms.assetid: 84285fbb-ecd1-46e6-9bdb-dc44db40dcc0
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Avertissement de conformit&#233;&#160;CLS CLS04114
Les attributs doivent être de type 'System::Attribute' ou hériter de celui\-ci  
  
 Pour être conforme CLS, un attribut personnalisé doit hériter de System::Attribute.  Un attribut qui n’a pas hérité de System::Attribute a été appliqué à un délégué.  
  
 Pour plus d’informations sur la vérification de la conformité CLS \(Common Language Subset\), consultez [Assemblys conformes CLS](http://msdn.microsoft.com/fr-fr/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 La déclaration suivante \(en langage d’assembly MSIL\) montre ce qui peut provoquer l’avertissement CLS04100 :  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Object  
```  
  
 puis un délégué qui utilise l’attribut :  
  
```  
.custom instance void MyAttribute::.ctor(int32) = ( 01 00 01 00 00 00 00 00 )  
```  
  
 Pour résoudre cet avertissement, faites dériver l’attribut de System::Attribute :  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Attribute  
```