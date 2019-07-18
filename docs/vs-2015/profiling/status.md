---
title: Status | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: ba656fa4-ef9d-4d8c-a3b6-739c3b5d23ae
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3f64364caf914c030fef806c5ae17e90a8368fa3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68157785"
---
# <a name="status"></a>Status
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L’option **Status** de VSPerfCmd.exe affiche des informations sur l’état du profileur et sur tous les processus qui sont en cours de profilage.  
  
 L’option **Status** doit être la seule option spécifiée sur la ligne de commande. Le profileur doit être initialisé avec l’option **Start** de VSPerfCmd.exe avant l’affichage de n’importe quel état.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
VSPerfCmd.exe /Status  
```  
  
#### <a name="parameters"></a>Paramètres  
 Aucun.  
  
## <a name="remarks"></a>Remarques  
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
