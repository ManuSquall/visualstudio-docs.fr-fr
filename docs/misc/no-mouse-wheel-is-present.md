---
title: "Absence de roulette de souris | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrMouse_NoWheelIsPresent"
ms.assetid: e924ffba-4af1-4247-9a6f-d19a03738f62
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Absence de roulette de souris
La propriété `My.Computer.Mouse.WheelScrollLines` a été appelée, mais la souris ne possède pas de roulette de défilement.  
  
### Pour corriger cette erreur  
  
-   Vérifiez la propriété `My.Computer.Mouse.WheelExists` pour déterminer si la souris a une roulette de défilement avant d’appeler la propriété `My.Computer.Mouse.WheelScrollLines`.  
  
     ou  
  
-   Installez une souris dotée d’une roulette de défilement sur l’ordinateur.  
  
## Voir aussi  
 [My.Computer.Mouse.WheelScrollLines, propriété](http://msdn.microsoft.com/fr-fr/67600f96-25d7-4dd9-946a-b46e1fc6a57f)   
 [My.Computer.Mouse.WheelExists, propriété](http://msdn.microsoft.com/fr-fr/332d44f7-0b66-4eaa-b4ce-d7f161bfbd07)   
 [Gestion des exceptions et des erreurs en Visual Basic](http://msdn.microsoft.com/fr-fr/3e351e73-cf23-40ab-8b60-05794160529e)