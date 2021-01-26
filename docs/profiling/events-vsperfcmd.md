---
title: Events (VSPerfCmd) | Microsoft Docs
description: La journalisation des Suivi d’v nements pour Windows de contrôle (ETW) à l’aide de l’option events dans l’outil de ligne de commande VSPerfCmd.exe. Passez en revue les paramètres de syntaxe.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: eb139327-4783-4f2a-874c-efad377a7be4
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 614ac24e38966c1d09df91d6771cab2b3914454d
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801388"
---
# <a name="events-vsperfcmd"></a>Events (VSPerfCmd)
L’option **événements** *VSPerfCmd.exe* contrôle la journalisation suivi d’v nements pour Windows (ETW). Les données ETW sont enregistrées dans un fichier .etl, qui est distinct du fichier de données du profileur. Les données peuvent être affichées dans un rapport avec la commande [VSPerfReport](../profiling/vsperfreport.md) /summary:etw.

 L’option **Events** peut être appelée à tout moment avant que la commande VSPerfCmd **Shutdown** soit appelée pour arrêter le profilage.

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /events {On|Off} {Guid|ProviderName} [,Flags[,Level]
```

#### <a name="parameters"></a>Paramètres
 **On**&#124;**Off** Démarre ou arrête la collecte des données d’événement.

 `Guid` GUID du contrôle fournisseur.

 `ProviderName` Nom du fournisseur inscrit auprès de WMI (Windows Management Instrumentation).

 `Flags` Valeur d’indicateurs hexadécimale commençant par « 0x » et qui est définie par le fournisseur d’événements.

 `Level` Spécifie la quantité de données collectées. `Level` est défini par le fournisseur d’événements.

 L’option **Events** interprète les mots clés suivants du noyau comme des noms de fournisseurs :

 **Process** Événements de processus

 **Thread** Événements de thread

 **Image** Événements de chargement et de déchargement d’image

 **Disk** Événements d’E/S de disque

 **File** Événements d’E/S de fichier

 **Hardfault** Défauts de page matériels

 **Pagefault** Défauts de page logiciels

 **Network** Événements réseau

 **Registry** Événements d’accès au Registre

 Notez que le fournisseur de noyau peut être seulement activé. Il ne peut pas être désactivé et ses indicateurs ne peuvent pas être modifiés jusqu’à l’arrêt du moniteur.

## <a name="remarks"></a>Notes

> [!NOTE]
> Quand des événements ETW du CLR sont activés, des données de démarrage supplémentaires sont également collectées dans le rapport Vue Trace. Pour exclure les événements de démarrage du rapport, utilisez la commande suivante :

```cmd
C:\<path>VSPerfCmd -events on, \".NET Common Language Runtime\", 0x7fffffff, 5
```

> [!IMPORTANT]
> Si vous n’excluez pas les événements de démarrage, comme ces événements ne sont pas listés dans le fichier MOF (Managed Object Format), ils apparaissent sous forme de GUID dans le rapport. Pour plus d’informations, consultez cette page sur le site web Microsoft : [Exemple de fichier MOF (Managed Object Format)](https://msdn.microsoft.com/library/default.aspx).

## <a name="see-also"></a>Voir aussi
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profiler des applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profiler des applications Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profiler des services](../profiling/command-line-profiling-of-services.md)
