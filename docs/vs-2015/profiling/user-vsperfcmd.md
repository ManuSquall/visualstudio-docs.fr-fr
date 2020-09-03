---
title: User (VSPerfCmd) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: ee1a478e-374d-4f30-ae28-d260b9d4723a
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 311d02ad3e15f184f8b7e21b5794d73c41a8d4fb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145386"
---
# <a name="user-vsperfcmd"></a>User (VSPerfCmd)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L’option **User** spécifie le nom de domaine et d’utilisateur du compte propriétaire du processus profilé. Cette option n’est nécessaire que si le processus s’exécute sous le compte d’un utilisateur autre que celui connecté. Le propriétaire du processus est répertorié dans la colonne Nom d’utilisateur, sous l’onglet Processus du gestionnaire des tâches de Windows.  
  
 L’option **User** peut uniquement être spécifiée sur une ligne de commande qui contient également l’option option **Start** .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName /User:[Domain\]UserName [Options]  
```  
  
#### <a name="parameters"></a>Paramètres  
 `Domain`  
 Nom du domaine de l’utilisateur.  
  
 `UserName`  
 Nom de l'utilisateur.  
  
## <a name="required-options"></a>Options obligatoires  
 L’option **User** peut être utilisée seulement avec l’option **Start**.  
  
 **Démarrer :**`Method`  
 Initialise le profileur avec la méthode de profilage spécifiée.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre l’utilisation de l’option **User**.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /User:SYSTEM  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Option](../profiling/vsperfcmd.md)   
 [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilage d’applications Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilage des services](../profiling/command-line-profiling-of-services.md)
