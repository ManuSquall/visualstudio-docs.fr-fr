---
title: "Marque | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1d72cef3-bb09-4bbb-8864-6ea0ab623ff9
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Marque
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'option **Mark** de VSPerfCmd.exe insère les informations spécifiées dans le fichier de données de profilage.  Mark peut apparaître dans un rapport VSPerfReport séparé ou dans le mode Mark Report de l'interface utilisateur du profileur.  **Mark** peut être utilisé pour spécifier des points de début et de fin dans les filtres de rapport et d'affichage.  
  
 L'option **Mark** doit être la seule option spécifiée sur la ligne de commande.  
  
## Syntaxe  
  
```  
VSPerfCmd.exe /Mark:MarkID,[MarkName]   
```  
  
#### Paramètres  
 `MarkID`  
 Entier défini par l'utilisateur répertorié comme ID de marque dans les affichages et les rapports du profileur.  `MarkID` n'a pas à être unique.  
  
 `MarkName`  
 \(Facultatif\) Chaîne définie par l'utilisateur répertoriée comme Marquer le nom dans les affichages et les rapports du profileur.  Si `MarkName` n'est pas spécifié, le champ Marquer le nom de la liste est vide.  Mettre entre guillemets les chaînes qui contiennent des espaces ou des barres obliques \(« \/ »\).  
  
## Exemple  
 Cet exemple insère une marque avec un ID de 123 et le nom de marque « TestMark ».  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
VSPerfCmd.exe /Mark:123,TestMark  
```  
  
## Voir aussi  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilage de services](../profiling/command-line-profiling-of-services.md)