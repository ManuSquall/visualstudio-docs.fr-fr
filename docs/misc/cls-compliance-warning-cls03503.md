---
title: "Avertissement de conformit&#233; CLS CLS03503 | Microsoft Docs"
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
  - "CLS03503"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS03503"
ms.assetid: 2d2e78db-5fcf-47e1-af1e-9545f28a306b
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Avertissement de conformit&#233; CLS CLS03503
La spécification CLS n’autorise pas les modificateurs obligatoires visibles publiquement \(modreq\), mais autorise les modificateurs facultatifs \(modopt\) qu’ils ne comprennent pas  
  
 La spécification CLS n’autorise pas les modificateurs obligatoires visibles publiquement \(modreq\), mais autorise les modificateurs facultatifs \(modopt\) qu’ils ne comprennent pas.  
  
 Vérifiez que les champs ne contiennent pas de types marqués avec des modificateurs obligatoires visibles publiquement.  
  
 Pour plus d’informations sur la vérification de la conformité CLS \(Common Language Subset\), consultez [Assemblys conformes CLS](http://msdn.microsoft.com/fr-fr/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 L’exemple suivant génère l’avertissement CLS03503 :  
  
```  
// CLS03503.cpp // compile with: /clr /LD // CLS03503 expected using namespace System; using namespace System::Reflection; using namespace cli::language; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public ref class MyClass { public: volatile Int32 param;   // CLS03503 Int32 param2;   // OK };  
```