---
title: "Comment puis-je d&#233;boguer les violations d&#39;acc&#232;s lorsque mon programme fonctionne hors du d&#233;bogueur&#160;? | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.access"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "violation d'accès (débogage)"
  - "déboguer (Visual Studio), violations d'accès"
ms.assetid: 780a298a-132e-4245-8370-8c82ca27c6c1
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Comment puis-je d&#233;boguer les violations d&#39;acc&#232;s lorsque mon programme fonctionne hors du d&#233;bogueur&#160;?
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

## Description du problème  
 Mon programme fonctionne correctement dans l'environnement Visual Studio, mais lorsque je l'exécute de façon autonome avec le système d'exploitation Windows, il génère une violation d'accès.  Comment puis\-je corriger cette erreur ?  
  
## Solution  
 Paramétrez l'option [Débogage juste\-à\-temps](../debugger/just-in-time-debugging-in-visual-studio.md) et exécutez votre programme de façon autonome jusqu'à ce que la violation d'accès se produise.  Dans la boîte de dialogue **Violation d'accès**, vous pouvez ensuite cliquer sur **Annuler** afin de démarrer le débogueur.  
  
 Consultez également, dans la Base de connaissances, l'article Q133174, « How to Locate Where a General Protection \(GP\) Fault Occurs ». Vous trouverez les articles de la Base de connaissances sur le CD MSDN Library ou en effectuant une recherche sur le site [http:\/\/support.microsoft.com\/](http://support.microsoft.com/).  
  
## Voir aussi  
 [Forum Aux Questions sur le débogage du code natif](../debugger/debugging-native-code-faqs.md)   
 [Débogage du code natif](../debugger/debugging-native-code.md)