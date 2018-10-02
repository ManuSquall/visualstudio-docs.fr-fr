---
title: Output | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5e286e61-4548-42cf-a635-e608c5edbe2b
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d08942b36fedab1f5c5535619bcb6c520093ff9b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47508560"
---
# <a name="output"></a>Sortie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [sortie](https://docs.microsoft.com/visualstudio/profiling/output).  
  
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
  
 **Start:** `Method`  
 Spécifie le nom du fichier de sortie.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, le fichier de données de profilage est créé dans le répertoire actif.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
```  
  
## <a name="see-also"></a>Voir aussi  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilage de services](../profiling/command-line-profiling-of-services.md)



