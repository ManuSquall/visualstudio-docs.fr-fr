---
title: Start | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: b85d0fe9-f67a-4b7c-8d48-7eecf3f2dfe9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cf374c03f7918e48c57f221ada22e43b435c0a78
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="start"></a>Start
L’option **Start** est une option de VSPerfCmd.exe qui initialise le profileur avec la méthode de profilage spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName [Options]  
```  
  
#### <a name="parameters"></a>Paramètres  
 `Method`  
 Doit être un des mots clés suivants :  
  
-   **TRACE** - Spécifie la méthode d’instrumentation.  
  
-   **SAMPLE** - Spécifie la méthode d’échantillonnage.  
  
-   **COVERAGE** - Spécifie la couverture du code.  
  
-   **CONCURRENCY** - Spécifie la méthode de résolution des conflits de ressources.  
  
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