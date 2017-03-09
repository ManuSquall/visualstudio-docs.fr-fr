---
title: "Avertissement de conformit&#233;&#160;CLS CLS00211 | Microsoft Docs"
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
  - "CLS00211"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS00211"
ms.assetid: 3a103f6f-bfb7-42ed-83ab-1c0f34fb9672
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Avertissement de conformit&#233;&#160;CLS CLS00211
Les membres de types non conformes CLS ne seront pas marqués comme conformes CLS  
  
 Si un type est marqué comme étant non conforme CLS, les membres de type ne peuvent pas être marqués comme conformes CLS.  
  
 Pour plus d’informations sur la vérification de conformité CLS, consultez [CLS Compliant Assemblies](http://msdn.microsoft.com/fr-fr/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 L’exemple suivant génère l’erreur CLS00211 :  
  
```  
// CLS00211.cpp // compile with: /clr /LD // CLS00211 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; [CLSCompliant(false)] public ref class One { public: [CLSCompliant(true)]   // CLS00211 void X() {} };  
```