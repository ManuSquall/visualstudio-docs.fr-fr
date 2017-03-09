---
title: "Avertissement de conformit&#233; CLS CLS01203 | Microsoft Docs"
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
  - "CLS01203"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01203"
ms.assetid: fe27463a-27df-473b-985a-b04c3bfac4d3
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Avertissement de conformit&#233; CLS CLS01203
La visibilité et l'accessibilité des types et des membres seront déterminées de telle sorte que les types utilisés dans la signature d'un membre seront visibles et accessibles lorsque le membre proprement dit est visible et accessible. Par exemple, le type d’un champ public qui est visible en dehors de son assembly ne doit pas être uniquement visible à l’intérieur de l’assembly.  
  
 La visibilité et l'accessibilité des types et des membres seront déterminées de telle sorte que les types utilisés dans la signature d'un membre seront visibles et accessibles lorsque le membre proprement dit est visible et accessible. Par exemple, le type d’un champ public qui est visible en dehors de son assembly ne doit pas être uniquement visible à l’intérieur de l’assembly.  
  
 Pour plus d’informations sur la vérification de la conformité CLS, consultez [Assemblys conformes CLS](http://msdn.microsoft.com/fr-fr/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 L’exemple suivant génère l’avertissement CLS01203 :  
  
```  
/* CLS01203.cpp */ // compile with: /clr /LD // CLS01203 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public ref class PublicLevelType {}; private ref class AssemblyLevelType {}; public ref class One { public: AssemblyLevelType^ Member1;   // not cls compliant PublicLevelType^ Member2;   // cls compliant };  
```