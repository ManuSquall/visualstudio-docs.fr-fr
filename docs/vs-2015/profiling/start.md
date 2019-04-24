---
title: Start | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: b85d0fe9-f67a-4b7c-8d48-7eecf3f2dfe9
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 83dc76e3e92a05f936d94c8cd0f6a2b9b69e4cc1
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60073551"
---
# <a name="start"></a>Start
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L’option **Start** est une option de VSPerfCmd.exe qui initialise le profileur avec la méthode de profilage spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName [Options]  
```  
  
#### <a name="parameters"></a>Paramètres  
 `Method`  
 Doit être un des mots clés suivants :  
  
- **TRACE** - Spécifie la méthode d’instrumentation.  
  
- **SAMPLE** - Spécifie la méthode d’échantillonnage.  
  
- **COVERAGE** - Spécifie la couverture du code.  
  
- **CONCURRENCY** - Spécifie la méthode de résolution des conflits de ressources.  
  
## <a name="required-options"></a>Options obligatoires  
 L’option **Output** doit être spécifiée quand **Start** est spécifié sur la ligne de commande.  
  
 **Output:** `filename`  
 Spécifie le nom du fichier de sortie.  
  
## <a name="exclusive-options"></a>Options exclusives  
 Les options suivantes peuvent être utilisées seulement avec l’option **Start** sur une ligne de commande.  
  
 **CrossSession**&#124;**CS**  
 Active le profilage interprocessus. Les noms **CrossSession** et **CS** de l’option sont tous deux pris en charge.  
  
 **User:**[`domain\`]`username`  
 Permet l’accès du client au moniteur à partir du compte spécifié.  
  
 **WinCounter:** `Path` [**Automark**:`n`]  
 **WinCounter** spécifie un compteur de performances Windows à inclure comme marque dans le fichier de données de profilage. **AutoMark** spécifie l’intervalle en millisecondes entre les collectes du fichier de données.  
  
## <a name="invalid-options"></a>Options non valides  
 Les options suivantes ne peuvent pas être utilisées avec l’option **Start** sur une ligne de commande.  
  
 **Status**  
 **Status** s’applique aux processus profilés. Il répertorie les processus et les threads, ainsi que l’état de leur profil actuel (Activé/Désactivé). Par exemple, si un processus est arrêté, **Status** ne l’indique pas dans le rapport. **Status** indique que le processus est profilé ou non.  
  
 **Shutdown**[**:**`Timeout`]  
 Désactive le profileur.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre l’utilisation de l’option **Start** de VSPerfCmd.exe pour initialiser le profileur.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## <a name="see-also"></a>Voir aussi  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilage de services](../profiling/command-line-profiling-of-services.md)
