---
title: "Avertissement de conformit&#233; CLS CLS01211 | Microsoft Docs"
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
  - "CLS01211"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01211"
ms.assetid: a6df4b7a-81e8-4e77-90d1-ec1cc3a759f5
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Avertissement de conformit&#233; CLS CLS01211
La visibilité et l'accessibilité des types et des membres seront déterminées de telle sorte que les types utilisés dans la signature d'un membre seront visibles et accessibles lorsque le membre proprement dit est visible et accessible. Par exemple, un type qui est visible en dehors de son assembly n’aura pas de type de base visible uniquement à l’intérieur de l’assembly.  
  
 Les types et les interfaces hérités ou implémentés par un type \(A\) doivent avoir une accessibilité supérieure ou égale à celle du type.  Par exemple, une méthode publique qui est visible à l'extérieur de son assembly n'aura pas d'argument dont le type est visible uniquement dans l'assembly.  
  
 Pour plus d’informations sur la vérification de conformité CLS, consultez [CLS Compliant Assemblies](http://msdn.microsoft.com/fr-fr/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 L’exemple suivant génère l’erreur CLS01211 :  
  
```  
// CLS01211.cpp // compile with: /clr /LD // CLS01211 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; private interface class I {}; public interface class I2 : public I {};  
```