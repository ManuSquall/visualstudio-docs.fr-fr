---
title: "Avertissement de conformit&#233; CLS CLS01701 | Microsoft Docs"
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
  - "CLS01701"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01701"
ms.assetid: 6ccbe156-9017-44ea-bd4e-a838af2ec2e7
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Avertissement de conformit&#233; CLS CLS01701
Les types de pointeurs non managés ne sont pas conformes à CLS  
  
 Un constructeur conforme à CLS ne peut pas contenir une déclaration de pointeur natif.  
  
 Pour plus d’informations sur la vérification de conformité CLS, consultez [Assemblys conformes à CLS](http://msdn.microsoft.com/fr-fr/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 L’exemple suivant génère l’erreur CLS1701 :  
  
```  
// CLS01701.cpp // compile with: /clr /LD // CLS01701 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public ref class One { public: One(int* Parameter) {}   // CLS01701 };  
```