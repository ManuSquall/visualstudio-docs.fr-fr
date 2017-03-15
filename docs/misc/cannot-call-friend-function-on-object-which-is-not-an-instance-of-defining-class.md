---
title: "Impossible d’appeler une fonction Friend pour un objet qui n’est pas une instance de la classe de d&#233;finition. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrID97"
ms.assetid: b9d821f0-8565-4f15-bb35-184789c69662
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Impossible d’appeler une fonction Friend pour un objet qui n’est pas une instance de la classe de d&#233;finition.
Vous avez tenté soit d’appeler la procédure `Friend` d’une classe, soit d’accéder à une propriété ou à une méthode `Friend` interprocessus ou inter\-threads. Une procédure `Friend` peut être appelée à partir d’un module à l’extérieur de la classe, mais elle fait partie du projet dans lequel la classe est définie.  
  
### Pour corriger cette erreur  
  
-   Vérifiez que vous appelez la procédure ou que vous y accédez à partir d’un module qui fait partie du projet dans lequel la classe est définie.  
  
## Voir aussi  
 [Friend](/dotnet/visual-basic/language-reference/modifiers/friend)