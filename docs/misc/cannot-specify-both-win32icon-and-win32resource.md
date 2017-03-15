---
title: "Impossible de sp&#233;cifier &#224; la fois /win32icon et /win32resource | Microsoft Docs"
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
  - "vbc2023"
  - "bc2023"
helpviewer_keywords: 
  - "BC2023"
ms.assetid: 60914807-1fde-4fef-9c6f-6f4a62527eed
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Impossible de sp&#233;cifier &#224; la fois /win32icon et /win32resource
Les options `/win32resource` et `/win32icon` sont mutuellement exclusives, car elles insèrent toutes deux des informations d’icônes dans le fichier de sortie.  
  
 **ID d’erreur :** BC2023  
  
### Pour corriger cette erreur  
  
-   Utilisez uniquement l’option `/win32icon` pour insérer un fichier .ico dans le fichier de sortie. Ce fichier .ico représente le fichier de sortie dans l’Explorateur Windows.  
  
     — ou —  
  
-   Utilisez uniquement l’option `/win32resource` pour insérer un fichier de ressources Win32 dans le fichier de sortie. Une ressource Win32 peut contenir des informations de version ou de bitmap \(icône\) qui permettent d’identifier votre application dans l’Explorateur Windows.  
  
## Voir aussi  
 [\/win32icon](/dotnet/visual-basic/reference/command-line-compiler/win32icon)   
 [\/win32resource](/dotnet/visual-basic/reference/command-line-compiler/win32resource)