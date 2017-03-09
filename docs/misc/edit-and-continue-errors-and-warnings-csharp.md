---
title: "Erreurs et avertissements de Modifier &amp; Continuer (C#) | Microsoft Docs"
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
  - "vs.csharp.enc.error_4001"
  - "vs.csharp.enc.error_4034"
  - "vs.csharp.enc.error_4003"
  - "vs.csharp.enc.error_4026"
  - "vs.csharp.enc.error_4032"
  - "vs.csharp.enc.error_4017"
  - "vs.csharp.enc.error_4053"
  - "vs.csharp.enc.error_4024"
  - "vs.csharp.enc.error_4012"
  - "vs.csharp.enc.error_4066"
  - "vs.csharp.enc.error_4020"
  - "vs.csharp.enc.error_4008"
  - "vs.csharp.enc.error_4033"
  - "vs.csharp.enc.error_4014"
  - "vs.csharp.enc.error_4023"
  - "vs.csharp.enc.error_4011"
  - "vs.csharp.enc.error_4006"
  - "vs.csharp.enc.error_4059"
  - "vs.csharp.enc.error_4015"
  - "vs.csharp.enc.error_4018"
  - "vs.csharp.enc.error_4028"
  - "vs.csharp.enc.error_4013"
  - "vs.csharp.enc.error_4009"
  - "vs.csharp.enc.error_4021"
  - "vs.csharp.enc.error_4065"
  - "vs.csharp.enc.error_4029"
  - "vs.csharp.enc.error_4058"
  - "vs.csharp.enc.error_4019"
  - "vs.csharp.enc.error_4007"
  - "vs.csharp.enc.error_4052"
  - "vs.csharp.enc.error_4025"
  - "vs.csharp.enc.error_4055"
  - "vs.csharp.enc.error_4022"
  - "vs.csharp.enc.error_4002"
  - "vs.csharp.enc.error_4016"
  - "vs.csharp.enc.error_4043"
  - "vs.csharp.enc.error_4027"
  - "vs.csharp.enc.error_4054"
  - "vs.csharp.enc.error_4004"
  - "vs.csharp.enc.error_4010"
  - "vs.csharp.enc.error_4030"
  - "vs.csharp.enc.error_4005"
  - "vs.csharp.enc.error_4035"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Modifier & Continuer (C#), erreurs et avertissements"
  - "erreurs (C#), débogage"
  - "erreurs (débogueur), Modifier & Continuer"
ms.assetid: c0e12b0a-8009-4a4a-979f-c804a91a5d9b
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "susanno"
manager: "douge"
---
# Erreurs et avertissements de Modifier &amp; Continuer (C#)
Vous avez modifié une section de code qui n'est pas autorisée en Visual C\# dans Modifier & Continuer.  
  
 [!INCLUDE[csharp_current_short](../misc/includes/csharp_current_short_md.md)]Modifier & Continuer vous permet d'arrêter l'exécution d'un programme en mode Arrêt, d'apporter des modifications à l'exécution de code, puis de continuer l'exécution du programme avec les modifications récemment incorporées.  
  
 Les modifications de code déclaratif qui affectent la structure publique d'une classe sont interdites, et certaines modifications que vous pouvez apporter à une méthode, au corps d'une propriété ou à des déclarations privées dans une classe ne sont pas autorisées. Autant que possible, Modifier & Continuer marque le code qui ne peut pas être modifié en gris clair et affiche un message d'erreur.  
  
 Pour plus d’informations sur les modifications prises en charge par Modifier & Continuer pour [!INCLUDE[csharp_current_short](../misc/includes/csharp_current_short_md.md)], consultez [Modifications de code prises en charge \(C\#\)](../debugger/supported-code-changes-csharp.md). Pour plus d’informations sur une erreur ou un avertissement spécifique, vous pouvez lancer une recherche ou publier une question sur le [forum de l’IDE Visual C\#](http://go.microsoft.com/fwlink/?LinkId=214693) dans MSDN.  
  
### Pour corriger cette erreur  
  
1.  Dans le menu **Déboguer**, choisissez **Annuler** pour annuler la modification.  
  
     ou  
  
2.  Arrêtez la session de débogage, procédez à vos modifications et démarrez une nouvelle session de débogage.  
  
## Voir aussi  
 [Modifier & Continuer \(Visual C\#\)](../debugger/edit-and-continue-visual-csharp.md)