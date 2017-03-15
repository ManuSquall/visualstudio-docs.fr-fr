---
title: "Avertissement de conformit&#233; CLS CLS01706 | Microsoft Docs"
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
  - "CLS01706"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01706"
ms.assetid: b89ccbf1-7256-4842-a0af-44a803f28340
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Avertissement de conformit&#233; CLS CLS01706
Les types de pointeurs non managés ne sont pas conformes CLS  
  
 Une signature de fonction conforme CLS ne peut pas contenir un type de pointeur non managé.  
  
 Pour plus d’informations sur la vérification de la conformité CLS \(Common Language Subset\), consultez [Assemblys conformes CLS](http://msdn.microsoft.com/fr-fr/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 L’exemple suivant génère l’avertissement CLS01706 :  
  
```  
// CLS01706.cpp // compile with: /clr /LD // CLS01706 expected [assembly:System::CLSCompliant (true)]; [assembly:System::Reflection::AssemblyKeyFile("clscompliance.snk")]; public ref class One { public: void Method1(int* parameter) {}   // CLS01706 void Method1(One ^ parameter) {}   // OK };  
```