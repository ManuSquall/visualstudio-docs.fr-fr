---
title: "Avertissement de conformit&#233; CLS CLS00711 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CLS00711"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS00711"
ms.assetid: 76481641-bda1-4128-8da8-ccba577b7ba1
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Avertissement de conformit&#233; CLS CLS00711
Le type sous\-jacent d’un enum doit être un type d’entier CLS intégré  
  
 Si vous spécifiez le type sous\-jacent d’un enum et que vous souhaitez obtenir un assembly conforme CLS \(Common Language Subset\), le type sous\-jacent de l’enum doit être un type d’entier conforme CLS.  
  
 Pour plus d’informations sur les enums CLR, consultez [Enum, classe](/visual-cpp/windows/enum-class-cpp-component-extensions).  
  
 Pour plus d’informations sur la vérification de conformité CLS, consultez [Assemblys conformes CLS](http://msdn.microsoft.com/fr-fr/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 L’exemple suivant génère l’erreur CLS00711 :  
  
```  
// CLS00711.cpp // compile with: /clr /LD // CLS00711 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public ref class One { public: enum class MyEnum_cls_bad : Char { bad_one = 1, bad_two = 2, bad_three = 3 }; enum class MyEnum_cls_good : Int32 { good_one = 1, good_two = 2, good_three = 3 }; };  
```