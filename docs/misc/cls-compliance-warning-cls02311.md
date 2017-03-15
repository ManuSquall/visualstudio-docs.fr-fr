---
title: "Avertissement de conformit&#233; CLS CLS02311 | Microsoft Docs"
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
  - "CLS02311"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS02311"
ms.assetid: 2faddffb-866d-417f-9ff3-9c61616030fb
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Avertissement de conformit&#233; CLS CLS02311
Une classe conforme CLS doit hériter d’une classe conforme CLS  
  
 Une classe conforme CLS doit hériter d’une classe conforme CLS.  Par exemple, 'System::Object'.  
  
 Pour plus d’informations sur la vérification de la conformité CLS, consultez [Assemblys conformes CLS](http://msdn.microsoft.com/fr-fr/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 L’exemple suivant génère l’avertissement CLS02311 :  
  
```  
// CLS02311.cpp // compile with: /clr /LD // CLS02311 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; [CLSCompliant(true)] public ref class CompliantType {}; [CLSCompliant(false)] public ref class NotCompliantType {}; public ref class One : public NotCompliantType {};   // CLS02311 public ref class Two : public CompliantType {};   // OK  
```