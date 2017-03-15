---
title: "Avertissement de conformit&#233; CLS CLS01103 | Microsoft Docs"
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
  - "CLS01103"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01103"
ms.assetid: 0d0aebaa-441a-4dc0-9745-8de3a551204b
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Avertissement de conformit&#233; CLS CLS01103
Tous les types apparaissant dans une signature devront être conformes à CLS  
  
 Si un type est conforme CLS, alors tous les champs, sauf s’ils sont marqués non conformes CLS, doivent être des types conformes CLS.  
  
 Pour plus d’informations sur la vérification de conformité CLS, consultez [Assemblys conformes à CLS](http://msdn.microsoft.com/fr-fr/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
```  
// CLS01103.cpp // compile with: /clr /LD // CLS01103 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; [CLSCompliant(false)] public ref class NotCompliantType {}; // Ref class public ref class One { public: NotCompliantType^ Member1;   // CLS01103 static NotCompliantType^ Member2;   // CLS01103 };  
```