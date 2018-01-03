---
title: Status | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba656fa4-ef9d-4d8c-a3b6-739c3b5d23ae
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d1168fb27330f49a714e64478fc7ab167569dadb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="status"></a>Status
L’option **Status** de VSPerfCmd.exe affiche des informations sur l’état du profileur et sur tous les processus qui sont en cours de profilage.  
  
 L’option **Status** doit être la seule option spécifiée sur la ligne de commande. Le profileur doit être initialisé avec l’option **Start** de VSPerfCmd.exe avant l’affichage de n’importe quel état.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
VSPerfCmd.exe /Status  
```  
  
#### <a name="parameters"></a>Paramètres  
 Aucun.  
  
## <a name="remarks"></a>Notes  
 L’option **Status** affiche les informations d’état suivantes pour le profileur.  
  
 **Nom du fichier de sortie**  
 Chemin et nom de fichier du fichier de données du profileur actif.  
  
 **Mode de collecte**  
 SAMPLE ou TRACE  
  
 **Nombre maximal de processus**  
 Nombre maximal de processus qui peuvent être profilés simultanément, et nombre de processus actuellement actifs.  
  
 **Nombre maximal de threads**  
 Nombre maximal de threads qui peuvent être profilés simultanément.  
  
 **Nombre de mémoires tampons**  
 Le nombre de mémoires tampons dédiées à l’écriture des données de profilage.  
  
 **Taille des mémoires tampons**  
 Taille en octets d’une mémoire tampon.  
  
 L’option **Status** affiche les informations d’état suivantes pour chaque processus en cours de profilage.  
  
 **Process**  
 Nom du processus profilé.  
  
 **ID du processus**  
 Identificateur système du processus.  
  
 **Nombre de threads**  
 Nombre de threads en cours d’exécution.  
  
 **Nombre de Start/Stop**  
 Compteur interne principal du profileur pour contrôler la collecte de données de ce processus. Le compteur doit être égal à un pour collecter des données. Le nombre de Start/Stop peut être manipulé par les API du profileur et les options de VSPerfCmd **GlobalOn**, **GlobalOff**, **ProcessOn**, **ProcessOff**, **ThreadOn** et **ThreadOff**.  
  
 **Nombre de Suspend/Resume**  
 Compteur interne secondaire du profileur pour contrôler la collecte de données de ce processus. Le compteur doit être inférieur ou égal à zéro pour que des données soient collectées. Le nombre de **Suspend/Resume** peut être manipulé seulement par les API du profileur.  
  
 **Utilisateurs avec droits d’accès au moniteur**  
 Liiste les noms des utilisateurs qui ont accès au profileur. Vous pouvez accorder l’accès à des utilisateurs supplémentaires en utilisant l’option **Admin** de VSPerfCmd.exe  
  
## <a name="see-also"></a>Voir aussi  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilage de services](../profiling/command-line-profiling-of-services.md)