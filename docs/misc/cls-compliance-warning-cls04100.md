---
title: "Avertissement de conformit&#233; CLS CLS04100 | Microsoft Docs"
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
  - "CLS04100"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS04100"
ms.assetid: a77cb26c-2546-473b-90da-41775289fc04
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Avertissement de conformit&#233; CLS CLS04100
Les attributs doivent être de type 'System::Attribute' ou hériter de celui\-ci  
  
 Pour être conforme CLS, un attribut personnalisé doit hériter de System::Attribute.  
  
 Pour plus d’informations sur la vérification de la conformité CLS \(Common Language Subset\), consultez [CLS Compliant Assemblies](http://msdn.microsoft.com/fr-fr/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 La déclaration suivante \(en langage d’assembly MSIL\) montre ce qui peut provoquer l’avertissement CLS04100 :  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Object  
```  
  
 Pour résoudre cet avertissement, faites dériver l’attribut de System::Attribute :  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Attribute  
```