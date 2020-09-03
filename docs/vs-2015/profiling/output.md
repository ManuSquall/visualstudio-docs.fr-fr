---
title: Output | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 5e286e61-4548-42cf-a635-e608c5edbe2b
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 26a9532bcf0e641d9ad27522f207493b905dc471
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179563"
---
# <a name="output"></a>Sortie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L’option **Output** spécifie le nom du fichier de données de profilage pour la session de performances. **Output** doit être utilisé avec l’option **Start**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName [Options]  
```  
  
#### <a name="parameters"></a>Paramètres  
 `FileName`  
 Nom du fichier de données. Les chemins complets et partiels sont acceptés. Si un chemin n’est pas spécifié, le fichier est créé dans le répertoire actif.  
  
## <a name="required-options"></a>Options obligatoires  
 L’option **Output** doit être utilisée avec l’option **Start**.  
  
 **Démarrer :**`Method`  
 Spécifie le nom du fichier de sortie.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, le fichier de données de profilage est créé dans le répertoire actif.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Option](../profiling/vsperfcmd.md)   
 [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilage d’applications Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilage des services](../profiling/command-line-profiling-of-services.md)
