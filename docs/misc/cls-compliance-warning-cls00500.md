---
title: "Avertissement de conformit&#233;&#160;CLS CLS00500 | Microsoft Docs"
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
  - "CLS00500"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS00500"
ms.assetid: faaf377e-3738-4c0d-9a51-09db4073564e
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Avertissement de conformit&#233;&#160;CLS CLS00500
Tous les noms dans une portée conforme CLS doivent être distincts, indépendamment de leur type.  
  
 Tous les noms introduits dans une portée conforme CLS doivent être distincts, indépendamment de leur type, sauf quand les noms sont identiques et résolus par surcharge. Dans le cadre de la spécification CLS, deux noms sont identiques si leurs mappages en minuscules sont identiques. Seules les propriétés et les fonctions peuvent être surchargées. Les propriétés et les fonctions doivent être surchargées uniquement en fonction du nombre et des types de leurs paramètres, à l’exception des opérateurs de conversion, qui peuvent également être surchargés selon leur type de retour. Pour plus d’informations, consultez [Conversions définies par l'utilisateur](/visual-cpp/dotnet/user-defined-conversions-cpp-cli).  
  
 Pour plus d’informations sur la vérification de la conformité CLS, consultez [Assemblys conformes CLS](http://msdn.microsoft.com/fr-fr/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 L’exemple suivant génère l’erreur CLS00500 :  
  
```  
// CLS00500.cpp // compile with: /clr /LD // CLS00500 expected using namespace System; using namespace System::Reflection; [assembly:AssemblyKeyFile("clscompliance.snk")]; [assembly:System::CLSCompliant(true)]; public ref class a {}; public ref class A {};   // CLS00500  
```