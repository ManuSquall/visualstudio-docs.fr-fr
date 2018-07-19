---
title: Output | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 5e286e61-4548-42cf-a635-e608c5edbe2b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 20f152a1c282688fb00428274e450d7073dfa946
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35254878"
---
# <a name="output"></a>Sortie
L’option **Output** spécifie le nom du fichier de données de profilage pour la session de performances. **Output** doit être utilisé avec l’option **Start**.  
  
## <a name="syntax"></a>Syntaxe  
  
```cmd  
VSPerfCmd.exe /Start:Method /Output:FileName [Options]  
```  
  
#### <a name="parameters"></a>Paramètres  
 `FileName`  
 Nom du fichier de données. Les chemins complets et partiels sont acceptés. Si un chemin n’est pas spécifié, le fichier est créé dans le répertoire actif.  
  
## <a name="required-options"></a>Options obligatoires  
 L’option **Output** doit être utilisée avec l’option **Start**.  
  
 **Start:** `Method`  
 Spécifie le nom du fichier de sortie.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, le fichier de données de profilage est créé dans le répertoire actif.  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
```  
  
## <a name="see-also"></a>Voir aussi  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profiler des applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profiler des applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profiler des services](../profiling/command-line-profiling-of-services.md)