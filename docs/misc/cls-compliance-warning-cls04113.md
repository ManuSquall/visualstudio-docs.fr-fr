---
title: "Avertissement de conformit&#233; CLS CLS04113 | Microsoft Docs"
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
  - "CLS04113"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS04113"
ms.assetid: 628f56bf-5f2f-4245-b4fd-02d4605a901c
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Avertissement de conformit&#233; CLS CLS04113
**Les attributs doivent être de type 'System::Attribute' ou hériter de celui\-ci**  
  
 Pour être conforme CLS, un attribut personnalisé doit hériter de System::Attribute.  
  
 Pour plus d’informations sur la vérification de la conformité CLS \(Common Language Subset\), consultez [Assemblys conformes CLS](http://msdn.microsoft.com/fr-fr/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 La déclaration suivante \(en langage d’assembly MSIL\) montre ce qui peut provoquer l’avertissement CLS04100 :  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Object  
```  
  
 Pour résoudre cet avertissement, faites dériver l’attribut de System::Attribute :  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Attribute  
```