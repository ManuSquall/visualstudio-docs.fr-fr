---
title: "Le ConnectionTimeout doit &#234;tre sup&#233;rieur &#224;&#160;0 | Microsoft Docs"
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
  - "vbrNetwork_BadConnectionTimeout"
ms.assetid: 15ac09a7-47f0-44f3-9e84-5bd10bd07450
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le ConnectionTimeout doit &#234;tre sup&#233;rieur &#224;&#160;0
Quand vous chargez et téléchargez des fichiers avec l’[My.Computer.Network Object](/dotnet/visual-basic/language-reference/objects/my-computer-network-object), vous devez spécifier un `connectionTimeout` supérieur à `0`.  
  
### Pour corriger cette erreur  
  
-   Fournissez un `connectionTimeout` supérieur à `0`.  
  
## Voir aussi  
 [My.Computer.Network.UploadFile \(méthode\)](http://msdn.microsoft.com/fr-fr/5505ea3e-3dbd-460b-9f8f-62c84c0a4de6)   
 [My.Computer.Network.DownloadFile \(méthode\)](http://msdn.microsoft.com/fr-fr/aeb7ed8f-1ac9-4242-ae57-9f35914eb329)   
 [How to: Upload a File](../Topic/How%20to:%20Upload%20a%20File%20in%20Visual%20Basic.md)   
 [How to: Download a File](../Topic/How%20to:%20Download%20a%20File%20in%20Visual%20Basic.md)   
 [Opérations réseau dans le .NET Framework avec Visual Basic](http://msdn.microsoft.com/fr-fr/c5379021-44ef-4d6a-acf5-e951fdcab6b2)