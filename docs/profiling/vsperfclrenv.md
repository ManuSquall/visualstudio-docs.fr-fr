---
title: VSPerfCLREnv | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- command-line tools, VSPerfCLREnv
- command line, tools
- performance tools, VSPerfCLREnv
- profiling tools,VSPerfCLREnv
- VSPerfCLREnv tool
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fc032fc89b6dee609fa3c69ebd210aa8adefd17c
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/11/2018
---
# <a name="vsperfclrenv"></a>VSPerfCLREnv

L’outil VSPerfCLREnv sert à définir les variables d’environnement nécessaires pour profiler une application .NET Framework. Il utilise la syntaxe suivante :

```cmd
VsPerfCLREnv [/option]
```

L’option que vous choisissez dépend du type de profilage que vous utilisez : échantillonnage, instrumentation ou global. Vous devez utiliser une option séparée pour inclure les données d’interaction de couche dans les données de profilage. La syntaxe de chaque option est décrite dans les tableaux suivants.

> [!NOTE]
> Quand vous avez terminé le profilage, exécutez **VSPerfCLREnv** avec l’option **/off** ou **/globaloff** pour supprimer les variables d’environnement nécessaires au profilage. Pour plus d’informations, consultez « Options VSPerfCLREnv pour supprimer des paramètres d’environnement » ci-après.

## <a name="vsperfclrenv-options-for-including-tier-interaction-data"></a>Options VSPerfCLREnv pour inclure des données d’interaction de couche

> [!WARNING]
> Pour collecter des données de profilage d’interaction de couche, vous pouvez utiliser n’importe quelle édition de Visual Studio. Cependant, ces données ne sont consultables que dans Visual Studio Enterprise.

Le profilage d’interaction de couche fournit des informations supplémentaires sur les requêtes ADO.NET dans des applications multicouches. Les données sont collectées uniquement pour les appels de fonctions synchrones. Vous pouvez ajouter les données d’interaction à toute exécution de profilage à l’aide de n’importe quelle méthode de profilage.

Les options **InteractionOn** et **GlobalInteractionOn** permettent de collecter des données d’interaction de couche. Vous devez définir l’option d’interaction après la variable d’environnement VSPerfCLREnv qui est obligatoire pour profiler une application.

L’exemple suivant inclut les données d’interaction de couche dans une exécution de profilage qui utilise la méthode d’échantillonnage :

```cmd
VSPerfCLREnv /SampleOn
VSPerfCLREnv /InteractionOn
VSPerfCmd /Start:Sample /Output:MyApp.exe.vsp /Launch:MyApp.exe
```

L’exemple suivant inclut les données d’interaction de couche dans une exécution de profilage pour un service Windows :

```cmd
VSPerfCLREnv /GlobalSampleOn
VSPerfCLREnv /GlobalInteractionOn
REM Restart the computer and start the service
VSPerfCmd /Start:Sample /Output:MyService.exe.vsp 
VSPerfCmd /Attach:MyService.exe
```

## <a name="vsperfclrenv-options-for-process-instrumentation-profiling"></a>Options VSPerfCLREnv pour le profilage par instrumentation de processus

Le tableau suivant décrit les options VSPerfCLREnv pour le profilage par instrumentation :

|Option|Description|
|------------|-----------------|
|**TraceOn**|Permet le profilage à l’aide de la méthode d’instrumentation. Ne permet pas le profilage de l’allocation de mémoire ou la collecte des données de durée de vie des objets.|
|**TraceGC**|Permet le profilage de l’allocation de mémoire à l’aide de la méthode d’instrumentation. Ne permet pas la collecte des données de durée de vie des objets.|
|**TraceGCLife**|Permet le profilage de l’allocation de mémoire et la collecte des données de durée de vie des objets à l’aide de la méthode d’instrumentation.|

## <a name="vsperfclrenv-options-for-process-sampling-profiling"></a>Options VSPerfCLREnv pour le profilage par échantillonnage de processus

Le tableau suivant décrit les options VSPerfCLREnv pour le profilage par échantillonnage :

|Option|Description|
|------------|-----------------|
|**SampleOn**|Permet le profilage à l’aide de la méthode d’échantillonnage. Ne permet pas le profilage de l’allocation de mémoire ou la collecte des données de durée de vie des objets.|
|**SampleGC**|Permet le profilage de l’allocation de mémoire à l’aide de la méthode d’échantillonnage. Ne permet pas la collecte des données de durée de vie des objets.|
|**SampleGCLife**|Permet le profilage de l’allocation de mémoire à l’aide de la méthode d’échantillonnage. Permet également la collecte des données de durée de vie des objets.|
|**SampleLineOff**|Désactive la collecte des données de profilage .NET au niveau ligne.|

## <a name="vsperfclrenv-options-for-global-profiling"></a>Options VSPerfCLREnv pour le profilage global

Pour profiler un service managé tel qu’une application web ASP.NET qui est lancée par le système d’exploitation et non par l’utilisateur, utilisez les versions globales des options de profilage VSPerfCLREnv. Le tableau suivant décrit les versions globales des options VSPerfCLREnv. Ces options définissent les variables d’environnement appropriées dans le Registre.

|Option|Description|
|------------|-----------------|
|**GlobalTraceOn**|Permet le profilage global à l’aide de la méthode d’instrumentation. Ne collecte pas les événements d’allocation de mémoire ou les données de durée de vie des objets.|
|**GlobalTraceGC**|Permet le profilage global de l’allocation de mémoire à l’aide de la méthode d’instrumentation. Ne permet pas la collecte des données de durée de vie des objets.|
|**GlobalTraceGCLife**|Permet le profilage global de l’allocation de mémoire à l’aide de la méthode d’instrumentation. Permet également la collecte des données de durée de vie des objets.|
|**GlobalSampleOn**|Permet le profilage global à l’aide de la méthode d’échantillonnage. Ne permet pas la collecte des événements d’allocation de mémoire ou des données de durée de vie des objets.|
|**GlobalSampleGC**|Permet le profilage global de l’allocation de mémoire à l’aide de la méthode d’échantillonnage. Ne permet pas la collecte des données de durée de vie des objets.|
|**GlobalSampleGCLife**|Permet le profilage global de l’allocation de mémoire à l’aide de la méthode d’échantillonnage. Permet également la collecte des données de durée de vie des objets.|

## <a name="vsperfclrenv-options-to-delete-environment-settings"></a>Options VSPerfCLREnv pour supprimer des paramètres d’environnement

 Quand vous avez terminé de profiler l’application managée, utilisez une des options suivantes pour supprimer les variables d’environnement ajoutées par VSPerfCLREnv. Le tableau suivant explique comment supprimer les variables d’environnement des profilages global et standard :

|Option|Description|
|------------|-----------------|
|**Off**|Supprime les variables d’environnement pour le profilage .NET standard. Utilisez cette option quand les options VSPerfClrEnv non globales ont été utilisées pour définir les variables d’environnement du profileur.|
|**GlobalOff**|Supprime les variables d’environnement pour le profilage .NET global. Utilisez cette option quand l’application a été démarrée par le système d’exploitation et pas par le profileur.|

## <a name="remarks"></a>Notes

Ces options ne sont pas obligatoires pour le profilage d’une application managée si celle-ci est démarrée à l’aide de l’Explorateur de performances dans l’IDE. L’Explorateur de performances définit automatiquement tous les paramètres d’environnement obligatoires.

Si l’environnement approprié n’a pas été défini pendant le profilage, un avertissement est émis pendant l’analyse et les noms des fonctions managées ne sont pas correctement résolus.

## <a name="see-also"></a>Voir aussi

[Profilage à partir de la ligne de commande](../profiling/using-the-profiling-tools-from-the-command-line.md)