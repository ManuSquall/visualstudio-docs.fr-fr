---
title: "Avertissement de conformit&#233; CLS CLS01206 | Microsoft Docs"
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
  - "CLS01206"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01206"
ms.assetid: e72f2293-874b-406c-9f22-92aeb64ac732
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Avertissement de conformit&#233; CLS CLS01206
La visibilité et l'accessibilité des types et des membres seront déterminées de telle sorte que les types utilisés dans la signature d'un membre seront visibles et accessibles lorsque le membre proprement dit est visible et accessible. Par exemple, une fonction membre publique qui est visible à l’extérieur de son assembly n’aura pas d’argument dont le type est visible uniquement dans l’assembly.  
  
 L’accessibilité des types figurant dans les signatures de méthode doit être supérieure ou égale à celle de la méthode.  Par exemple, une méthode publique qui est visible à l'extérieur de son assembly n'aura pas d'argument dont le type est visible uniquement dans l'assembly.  
  
 Pour plus d’informations sur la vérification de la conformité CLS, consultez [CLS Compliant Assemblies](http://msdn.microsoft.com/fr-fr/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 L’exemple suivant génère l’erreur CLS01206 :  
  
```  
/* CLS01206.cpp */ // compile with: /clr /LD // CLS01206 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public ref class PublicLevelType {}; private ref class AssemblyLevelType {}; public ref class One { public: AssemblyLevelType^ Method1() { return gcnew AssemblyLevelType(); } };  
```