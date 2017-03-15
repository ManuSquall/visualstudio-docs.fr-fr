---
title: "Avertissement de conformit&#233; CLS CLS01714 | Microsoft Docs"
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
  - "CLS01714"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01714"
ms.assetid: 8ba94d1e-ad27-4dd2-919a-19be75119e53
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Avertissement de conformit&#233; CLS CLS01714
Les types de pointeurs non managés ne sont pas conformes à CLS  
  
 Une signature de délégué conforme CLS ne peut pas contenir un type de pointeur non managé.  
  
 Pour plus d’informations sur la vérification de la conformité CLS \(Common Language Subset\), consultez [Assemblys conformes CLS](http://msdn.microsoft.com/fr-fr/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 L’exemple suivant génère l’erreur CLS01714 :  
  
```  
// CLS01714.cpp // compile with: /clr /LD // CLS01714 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public delegate void MyDelegate1(int* Parameter);   // CLS01714  
```