---
title: "Erreur&#160;: Microsoft Visual Studio Remote Debugging Monitor sur l&#39;ordinateur distant s&#39;ex&#233;cute avec un utilisateur diff&#233;rent | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "anyuser (option)"
  - "anyuser (option)"
  - "msvsmon.exe"
  - "Remote Debugging Monitor"
  - "débogage distant, Remote Debugging Monitor"
ms.assetid: e5b18734-2daf-4c58-b5de-24ae1295703e
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Erreur&#160;: Microsoft Visual Studio Remote Debugging Monitor sur l&#39;ordinateur distant s&#39;ex&#233;cute avec un utilisateur diff&#233;rent
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si vous essayez d'effectuer un débogage distant, vous risquez de recevoir ce message d'erreur :  
  
 Microsoft Visual Studio Remote Debugging Monitor sur l'ordinateur distant s'exécute avec un utilisateur différent.  
  
## Cause  
 Ce message se produit lorsque vous déboguez en mode Aucune authentification et l'utilisateur qui a démarré msvsmon n'est pas l'utilisateur qui exécute Visual Studio.  
  
## Solution  
 La solution la plus sûre et la mieux adaptée consiste à exécuter Remote Debugging Monitor \(msvsmon.exe\) sous le même compte d'utilisateur que Visual Studio.  Si vous ne pouvez pas le faire, vous pouvez exécuter Remote Debugging Monitor sous l'autre compte avec l'option **Permettre à tous les utilisateurs de déboguer** sélectionnée dans la boîte de dialogue **Options** de Remote Debugging Monitor.  
  
> [!CAUTION]
>  Accorder à d'autres utilisateurs l'autorisation de se connecter implique l'éventualité d'une connexion accidentelle à la session de débogage distant incorrecte.  Le débogage exécuté en mode **Aucune authentification** n'est jamais sécurisé et doit être utilisé avec précaution.  
  
 Pour plus d'informations, consultez [Démarrer Remote Debugging Monitor](../Topic/Start%20%20the%20Remote%20Debugging%20Monitor.md).  
  
## Voir aussi  
 [Erreurs de débogage distant et dépannage](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Débogage distant](../debugger/remote-debugging.md)