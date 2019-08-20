---
title: GC (VSPerfCmd) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7c81e88b-a748-4cf5-a7a1-3429608e1b54
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2bdb28f74dd305dc497521e95d38e00192c21c54
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68193601"
---
# <a name="gc-vsperfcmd"></a>GC (VSPerfCmd)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L’option **GC** active la collecte des données d’allocation mémoire et de durée de vie des objets de .NET Framework. L’option **GC** peut être utilisée seulement avec la méthode de profilage par échantillonnage et seulement avec l’option **Launch**.  
  
 Quand vous utilisez l’option **GC**, la commande VSPerfClrEnv **/sampleon** n’est pas obligatoire.  
  
 Si aucun paramètre n’est spécifié, ou si le paramètre **Allocation** est spécifié, seules les données d’allocation mémoire de .NET Framework sont collectées. Si le paramètre **Lifetime** est spécifié, les données d’allocation mémoire de .NET Framework et de durée de vie des objets de .NET Framework sont collectées.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
VSPerfCmd.exe /Launch:AppName /GC[:{Allocation|Lifetime}] [Options]  
```  
  
#### <a name="parameters"></a>Paramètres  
 **Allocation**  
 Par défaut. Collecte les données d’allocation mémoire de .NET Framework.  
  
 **Durée de vie**  
 Collecte les données d’allocation de mémoire de .NET Framework et les données de durée de vie des objets de .NET Framework.  
  
## <a name="required-options"></a>Options obligatoires  
 L’option **GC** peut être utilisée seulement avec l’option **Launch**.  
  
 **Launch :** `AppName`  
 Démarre l’application spécifiée et commence le profilage avec la méthode d’échantillonnage.  
  
## <a name="example"></a>Exemples  
 L’exemple suivant lance une application et collecte les données d’allocation mémoire de .NET Framework.  
  
```  
VSPerfCmd.exe /Launch:TestApp.exe /gc  
```  
  
## <a name="see-also"></a>Voir aussi  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilage de services](../profiling/command-line-profiling-of-services.md)
