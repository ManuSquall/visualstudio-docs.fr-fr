---
title: "LineOff | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 76082063-20ef-47ae-ad64-81b43b654865
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# LineOff
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Par défaut, le profileur collecte le numéro de ligne de code source et les données d'offset du numéro de ligne lorsque vous utilisez la méthode de profilage de l'échantillonnage.  L'option VSPerfCmd **LineOff** désactive la collecte de données de numéro de ligne lorsque VSPerfCmd est utilisé pour démarrer l'application.  Les données de profilage sont collectées au niveau de la fonction lorsque **LineOff** est spécifié.  
  
 Vous ne pouvez utiliser **LineOff** qu'avec l'option **Launch**, et uniquement lorsque le profileur a été initialisé pour l'échantillonnage à l'aide de l'option **Start**:**Sample**.  
  
## Syntaxe  
  
```  
VSPerfCmd.exe /Launch:AppName /LineOff [Options]  
```  
  
#### Paramètres  
 Aucun  
  
## Options requises  
 L'option **LineOff** ne peut être utilisée qu'en ligne de commande avec l'option  **Launch**.  
  
 **Launch:** `AppName`  
 Démarre l'application spécifiée et commence le profilage avec la méthode d'échantillonnage.  
  
## Exemple  
 Cet exemple démarre l'application et le profileur et désactive l'échantillonnage au niveau de la ligne.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /LineOff  
```  
  
## Voir aussi  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilage de services](../profiling/command-line-profiling-of-services.md)