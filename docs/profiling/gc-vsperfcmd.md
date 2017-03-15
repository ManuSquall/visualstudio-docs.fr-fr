---
title: "GC (VSPerfCmd) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7c81e88b-a748-4cf5-a7a1-3429608e1b54
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# GC (VSPerfCmd)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'option **GC** active la collecte des données d'allocation de mémoire .NET Framework et de durée de vie de l'objet.  L'option **GC** ne peut être utilisée qu'avec la méthode de profilage d'échantillonnage et uniquement avec l'option **Launch**.  
  
 Lorsque vous utilisez l'option **GC**, la commande **\/sampleon** VSPerfClrEnv n'est pas obligatoire.  
  
 Si aucun paramètre n'est spécifié ou si le paramètre **Allocation** est spécifié, seules les données d'allocation de mémoire .NET Framework sont collectées.  Si le paramètre **Lifetime** est spécifié, à la fois les données d'allocation de mémoire .NET Framework et les données de durée de vie de l'objet .NET Framework sont collectées.  
  
## Syntaxe  
  
```  
VSPerfCmd.exe /Launch:AppName /GC[:{Allocation|Lifetime}] [Options]  
```  
  
#### Paramètres  
 **Allocation**  
 Par défaut.  Collecte les données d'allocation de mémoire .NET Framework.  
  
 **Lifetime**  
 Collecte les données liées à l'allocation de la mémoire .NET Framework et à la durée de vie des objets .NET Framework.  
  
## Options requises  
 L'option **GC** ne peut être utilisée qu'avec l'option **Launch**.  
  
 **Launch:** `AppName`  
 Démarre l'application spécifiée et commence le profilage avec la méthode d'échantillonnage.  
  
## Exemple  
 L'exemple suivant lance une application et collecte les données d'allocation de mémoire .NET Framework.  
  
```  
VSPerfCmd.exe /Launch:TestApp.exe /gc  
```  
  
## Voir aussi  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilage de services](../profiling/command-line-profiling-of-services.md)