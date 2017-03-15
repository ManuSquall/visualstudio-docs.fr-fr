---
title: "Avertissement de conformit&#233; CLS CLS01201 | Microsoft Docs"
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
  - "CLS01201"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01201"
ms.assetid: 8c3e6ce4-8ea5-487a-bbed-56a36eceb024
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Avertissement de conformit&#233; CLS CLS01201
La visibilité et l'accessibilité des types et des membres seront déterminées de telle sorte que les types utilisés dans la signature d'un membre seront visibles et accessibles lorsque le membre proprement dit est visible et accessible. Par exemple, un constructeur public qui est visible à l’extérieur de son assembly n’aura pas d’argument dont le type est visible uniquement dans l’assembly.  
  
 L’accessibilité des types figurant dans les signatures de constructeur doit être supérieure ou égale à celle du constructeur.  Par exemple, un constructeur public visible à l’extérieur de son assembly n’aura pas d’argument dont le type est visible uniquement dans l’assembly.  
  
 Pour plus d’informations sur la vérification de la conformité CLS, consultez [Assemblys conformes à CLS](http://msdn.microsoft.com/fr-fr/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 L’exemple suivant génère l’avertissement CLS01201 :  
  
```  
/* CLS01201.cpp */ // compile with: /clr /LD // CLS01201 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; private ref class AssemblyLevelType {}; public ref class One { public: One(AssemblyLevelType^ parameter) {}   // not cls compliant }; private value class Two { public: Two(AssemblyLevelType^ parameter) {}   // OK };  
```