---
title: GC (VSPerfCmd) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7c81e88b-a748-4cf5-a7a1-3429608e1b54
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f15cf7c5991187431c06a01c67c7105f48dc28de
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53913215"
---
# <a name="gc-vsperfcmd"></a>GC (VSPerfCmd)
L’option **GC** active la collecte des données d’allocation mémoire et de durée de vie des objets de .NET Framework. L’option **GC** peut être utilisée seulement avec la méthode de profilage par échantillonnage et seulement avec l’option **Launch**.  
  
 Quand vous utilisez l’option **GC**, la commande VSPerfClrEnv **/sampleon** n’est pas obligatoire.  
  
 Si aucun paramètre n’est spécifié, ou si le paramètre **Allocation** est spécifié, seules les données d’allocation mémoire de .NET Framework sont collectées. Si le paramètre **Lifetime** est spécifié, les données d’allocation mémoire de .NET Framework et de durée de vie des objets de .NET Framework sont collectées.  
  
## <a name="syntax"></a>Syntaxe  
  
```cmd  
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
  
## <a name="example"></a>Exemple  
 L’exemple suivant lance une application et collecte les données d’allocation mémoire de .NET Framework.  
  
```cmd  
VSPerfCmd.exe /Launch:TestApp.exe /gc  
```  
  
## <a name="see-also"></a>Voir aussi  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profiler des applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profiler des applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profiler des services](../profiling/command-line-profiling-of-services.md)