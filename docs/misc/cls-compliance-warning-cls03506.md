---
title: "Avertissement de conformit&#233; CLS CLS03506 | Microsoft Docs"
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
  - "CLS03506"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS03506"
ms.assetid: baec820c-aabb-44c4-b0cd-043c3ca9c537
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Avertissement de conformit&#233; CLS CLS03506
**La spécification CLS n’autorise pas les modificateurs obligatoires visibles publiquement \(modreq\), mais autorise les modificateurs facultatifs \(modopt\) qu’ils ne comprennent pas**  
  
 La spécification CLS n’autorise pas les modificateurs obligatoires visibles publiquement \(modreq\), mais autorise les modificateurs facultatifs \(modopt\) qu’ils ne comprennent pas.  
  
 Vérifiez que les signatures de méthode ne contiennent pas de types marqués avec des modificateurs obligatoires visibles publiquement.  
  
 Pour plus d’informations sur la vérification de la conformité CLS \(Common Language Subset\), consultez [Assemblys conformes CLS](http://msdn.microsoft.com/fr-fr/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 L’exemple suivant génère l’avertissement CLS03506 :  
  
```  
// CLS03506.cpp // compile with: /clr /LD // CLS03506 expected using namespace System; using namespace System::Reflection; using namespace cli::language; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public ref class One { public: void F1(volatile Int32 parameter) {}   // CLS03506 void F2( Int32 parameter) {}   // OK };  
```