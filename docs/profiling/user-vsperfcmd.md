---
title: User (VSPerfCmd) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ee1a478e-374d-4f30-ae28-d260b9d4723a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 23522f699d6fbb15e2f626e22e990163163eab5e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54940334"
---
# <a name="user-vsperfcmd"></a>User (VSPerfCmd)
L’option **User** spécifie le nom de domaine et d’utilisateur du compte propriétaire du processus profilé. Cette option n’est nécessaire que si le processus s’exécute sous le compte d’un utilisateur autre que celui connecté. Le propriétaire de processus est listé dans la colonne Nom d’utilisateur, sous l’onglet **Processus** du Gestionnaire des tâches Windows.  
  
 Vous pouvez spécifier l’option **User** seulement sur une ligne de commande qui contient aussi l’option **Start**.  
  
## <a name="syntax"></a>Syntaxe  
  
```cmd  
VSPerfCmd.exe /Start:Method /Output:FileName /User:[Domain\]UserName [Options]  
```  
  
#### <a name="parameters"></a>Paramètres  
 `Domain`  
 Nom du domaine de l’utilisateur.  
  
 `UserName`  
 Nom de l'utilisateur.  
  
## <a name="required-options"></a>Options obligatoires  
 L’option **User** peut être utilisée seulement avec l’option **Start**.  
  
 **Start:** `Method`  
 Initialise le profileur avec la méthode de profilage spécifiée.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre l’utilisation de l’option **User**.  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /User:SYSTEM  
```  
  
## <a name="see-also"></a>Voir aussi  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profiler des applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profiler des applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profiler des services](../profiling/command-line-profiling-of-services.md)