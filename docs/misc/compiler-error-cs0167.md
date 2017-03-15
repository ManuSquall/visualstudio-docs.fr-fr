---
title: "Erreur du compilateur CS0167 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0167"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0167"
ms.assetid: e6901b40-11a0-422c-9ea3-3b25c0ad7791
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0167
Il manque la méthode Invoke du délégué 'délégué'  
  
 Vous avez importé et utilisé un programme managé \(qui utilise le common language runtime .NET Framework\) qui a été créé avec un autre compilateur. Ce compilateur a autorisé un [délégué](/dotnet/csharp/language-reference/keywords/delegate) incorrect. Par conséquent, la méthode `Invoke` n’était pas disponible. Pour plus d'informations, consultez [Délégués](/dotnet/csharp/programming-guide/delegates/index).