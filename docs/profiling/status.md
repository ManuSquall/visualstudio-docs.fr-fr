---
title: Status | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ba656fa4-ef9d-4d8c-a3b6-739c3b5d23ae
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 25f452dcb473abf87d8992f36f5326973937e85e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967870"
---
# <a name="status"></a>Status
L’option **Status** de *VSPerfCmd.exe* affiche des informations sur l’état du profileur et sur tous les processus qui sont en cours de profilage.

 L’option **Status** doit être la seule option spécifiée sur la ligne de commande. Le profileur doit être initialisé avec l’option **Start** de *VSPerfCmd.exe* avant l’affichage d’un état.

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /Status
```

#### <a name="parameters"></a>Paramètres
 Aucun.

## <a name="remarks"></a>Remarques
 L’option **Status** affiche les informations d’état suivantes pour le profileur.

 **Nom du fichier de sortie** Chemin et nom du fichier de données du profileur actif.

 **Mode de collecte** SAMPLE ou TRACE

 **Nombre maximal de processus** Nombre maximal de processus qui peuvent être profilés simultanément, et nombre de processus actifs.

 **Nombre maximal de threads** Nombre maximal de threads qui peuvent être profilés simultanément.

 **Nombre de mémoires tampons** Nombre de mémoires tampons dédiées à l’écriture des données de profilage.

 **Taille des mémoires tampons** Taille en octets d’une mémoire tampon.

 L’option **Status** affiche les informations d’état suivantes pour chaque processus en cours de profilage.

 **Processus** Nom du processus profilé.

 **ID de processus** Identificateur système du processus.

 **Nombre de threads** Nombre de threads en cours d’exécution.

 **Nombre Start/Stop global** Compteur interne principal du profileur pour contrôler la collecte des données de ce processus. Le compteur doit être égal à un pour collecter des données. Le nombre de Start/Stop peut être manipulé par les API du profileur et les options de VSPerfCmd **GlobalOn**, **GlobalOff**, **ProcessOn**, **ProcessOff**, **ThreadOn** et **ThreadOff**.

 **Nombre de Suspend/Resume** Compteur interne secondaire du profileur pour contrôler la collecte de données de ce processus. Le compteur doit être inférieur ou égal à zéro pour que des données soient collectées. Le nombre de **Suspend/Resume** peut être manipulé seulement par les API du profileur.

 **Utilisateurs avec droits d’accès au gestionnaire** Liste les noms des utilisateurs qui ont accès au profileur. Vous pouvez accorder l’accès à des utilisateurs supplémentaires en utilisant l’option **Admin** de VSPerfCmd.exe

## <a name="see-also"></a>Voir aussi
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profiler des applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profiler des applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profiler des services](../profiling/command-line-profiling-of-services.md)