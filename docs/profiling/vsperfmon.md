---
title: VSPerfMon | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPerfMon tool
- command line, tools
- command-line tools, VSPerfMon tool
- data [Visual Studio ALM], VSPerfMon tool
- performance data, VSPerfMon tool
- performance tools, VSPerfMon tool
- profilng tools,VSPerfCmd
ms.assetid: 37052afb-7a58-441f-bb17-f1587cc57068
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 50519554f7ec71e277dc776b05bc2967c1071f52
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779894"
---
# <a name="vsperfmon"></a>VSPerfMon
Vous pouvez utiliser l’outil VSPerfMon pour collecter les données de performances d’une application. En règle générale, cet outil est lancé par *VSPerfCmd.exe*. VSPerfMon affiche des informations supplémentaires sur l’attachement ou le détachement de processus qui ne sont pas disponibles à l’aide de l’outil VSPerfCmd. Pour afficher ces informations, démarrez VSPerfMon dans une fenêtre distincte. Pour appeler VSPerfMon, utilisez la syntaxe suivante :

```cmd
VSPerfMon [/U] </TRACE [/COUNTER:cfg] | /SAMPLE | /COVERAGE> /CROSSSESSION /OUTPUT <file name> [/WINCOUNTER:cfg] [/USER [DOMAIN\]username]
```

 Le tableau suivant décrit les options de l’outil VSPerfMon :

|Options|Description|
|-------------|-----------------|
|**U**|La sortie redirigée de la console est écrite au format Unicode.  Cela doit être la première option spécifiée.|
|**OUTPUT:** `<` *nom de fichier* `>`|Redirige la sortie vers le nom de fichier spécifié.|
|**Trace**|Démarre l’analyseur de performances pour le profilage instrumenté.|
|**Échantillon**|Démarre l’analyseur de performances pour le profilage par échantillonnage.|
|**Couverture**|Démarre l’analyseur de performances pour la collection de couverture du code.|
|**Concurrence**|Démarre l’analyseur de performances pour le profilage de conflit de ressources.|
|**USER:** `[` *domaine* `\]` *nom_utilisateur*|Autorise l’accès client à l’analyseur de performances à partir du compte spécifié.|
|**CROSSSESSION**|Active le profilage intersession.|
|**COMPTEUR**`:cfg`|Quand la méthode de profilage par instrumentation (TRACE) est utilisée, spécifie un compteur UC à collecter à chaque point d’instrumentation. Vous pouvez collecter des données de plusieurs compteurs en spécifiant plusieurs options Counter.<br /><br /> Utilisez la syntaxe suivante pour spécifier les données de compteur (*cfg*) :<br /><br /> **nom_compteur** [**,Rechargement**[,**nom_convivial**]]<br /><br /> -   **nom_compteur** est le nom d’un compteur retourné par la commande VSPerfCmd /QueryCounters.<br />-   **Rechargement** est l’intervalle d’échantillonnage des événements de compteur. N’utilisez pas *Rechargement* avec la méthode d’instrumentation.<br />- Si spécifié, **nom_convivial** remplace **nom_compteur** dans les noms de colonnes des rapports sur les outils de profilage.|
|**WINCOUNTER** `:path`|Spécifie un compteur de performance Windows à inclure avec les données de la marque. `path` est une chaîne du compteur de performance Windows au format PDH du chemin du compteur. Par exemple :<br /><br /> \Processor(0)\\% Processor Time<br /><br /> \System\Context Switches/sec|
|**AUTOMARK** `:n`|Spécifie l’intervalle (en millisecondes) entre les marques automatiques quand vous utilisez /WINCOUNTER. Valeur arrondie aux 500 ms les plus proches.<br /><br /> Utilisez 0 pour désactiver les marques automatiques. (par défaut=500 ms si non spécifié)|

## <a name="see-also"></a>Voir aussi
- [VSInstr](../profiling/vsinstr.md)
- [Vsperfcmd](../profiling/vsperfcmd.md)
- [VSPerfReport](../profiling/vsperfreport.md)
- [Vues du rapport des performances](../profiling/performance-report-views.md)
