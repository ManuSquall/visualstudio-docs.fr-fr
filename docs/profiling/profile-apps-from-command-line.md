---
title: Mesurer les performances à partir de la ligne de commande
description: Mesurez les performances de l’UC et l’utilisation de la mémoire managée dans votre application à partir de la ligne de commande.
ms.custom: ''
ms.date: 02/21/2020
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools, command-line
- Diagnostics Tools, command-line
- CPU Usage, command-line
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: b0d2b0964c565bab4d3a0731a14b93ccd976bb69
ms.sourcegitcommit: e132a870ec198fdcec289227f1a0c1c48fef070c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/04/2020
ms.locfileid: "93344492"
---
# <a name="measure-application-performance-from-the-command-line"></a>Mesurer les performances d’une application à partir de la ligne de commande

Vous pouvez collecter des informations sur le niveau de performance d’une application à l’aide d’outils en ligne de commande.

Dans l’exemple décrit dans cet article, vous collectez des informations sur le niveau de performance du Bloc-notes Microsoft, mais la même méthode peut servir à profiler n’importe quel processus.

## <a name="prerequisites"></a>Prérequis

* Visual Studio 2019 ou versions ultérieures

* Connaissance des outils en ligne de commande

* Pour collecter des informations sur les performances sur un ordinateur distant sur lequel Visual Studio n’est pas installé, installez le [outils de contrôle à distance de Visual Studio](https://visualstudio.microsoft.com/downloads#remote-tools-for-visual-studio-2019) sur l’ordinateur distant. La version des outils doit correspondre à votre version de Visual Studio.

## <a name="collect-performance-data"></a>Collecter des données de performances

Pour profiler une application à l’aide des outils CLI de diagnostics Visual Studio, l’outil de profilage et l’un des agents collecteurs sont attachés à un processus. Quand vous attachez l’outil de profilage, vous débutez une session de diagnostic qui capture et stocke des données de profilage jusqu’à l’arrêt de l’outil, après quoi ces données sont exportées dans un fichier *.diagsession*. Vous pouvez ensuite ouvrir ce fichier dans Visual Studio pour analyser les résultats.

1. Démarrez le Bloc-notes, puis ouvrez le Gestionnaire des tâches pour obtenir son ID de processus (PID). Dans le Gestionnaire des tâches, recherchez le PID sous l’onglet **Détails**.

1. Ouvrez une invite de commandes et accédez au répertoire contenant l’exécutable de l’agent de collecte, généralement ici (pour Visual Studio Enterprise).

   ```<Visual Studio installation folder>\2019\Enterprise\Team Tools\DiagnosticsHub\Collector\```

1. Démarrez *VSDiagnostics.exe* en tapant la commande suivante :

   ```cmd
   VSDiagnostics.exe start <id> /attach:<pid> /loadConfig:<configFile>
   ```

   Les arguments qui doivent être inclus sont les suivants :

   * \<*id*> Identifie la session de collecte. L’ID doit être un nombre compris entre 1 et 255.
   * \<*pid*>, PID du processus que vous souhaitez profiler, dans le cas présent, le PID que vous avez trouvé à l’étape 1.
   * \<*configFile*>, fichier de configuration de l’agent de collecte que vous souhaitez lancer. Pour plus d’informations, consultez [Fichiers de configuration des agents](#config_file).

   Par exemple, vous pouvez utiliser la commande suivante pour l’agent CPUUsageBase en remplaçant le *PID* comme décrit précédemment.

   ```cmd
   VSDiagnostics.exe start 1 /attach:<pid> /loadConfig:AgentConfigs\CPUUsageLow.json
   ```

1. Redimensionnez le Bloc-notes ou tapez quelque chose pour que des informations de profilage intéressantes soient collectées.

1. Arrêtez la session de collecte et envoyez la sortie à un fichier en tapant la commande suivante :

   ```cmd
   VSDiagnostics.exe stop <id> /output:<path to file>
   ```

1. Localisez la sortie du fichier *. diagsession* à partir de la commande précédente, puis ouvrez-la dans Visual Studio ( **fichier**  >  **ouvert** ) pour examiner les informations collectées.

   Pour analyser les résultats, consultez la documentation de l’outil d’analyse des performances correspondant. Par exemple, il peut s’agir de l’utilisation de l' [UC](../profiling/cpu-usage.md), de l’outil d' [allocation d’objets .net](../profiling/dotnet-alloc-tool.md)ou de l’outil [de base de données](../profiling/analyze-database.md) .

## <a name="agent-configuration-files"></a><a name="config_file"></a> Fichiers de configuration des agents

Les agents de collecte sont des composants interchangeables qui collectent différents types de données en fonction de ce que vous essayez de mesurer.

Pour des raisons pratiques, vous pouvez stocker ces informations dans un fichier de configuration d’agent. Le fichier de configuration est un fichier *.json* qui contient au minimum le nom du fichier *.dll* et son CLSID COM. Voici des exemples de fichiers de configuration que vous pouvez trouver dans le dossier suivant :

```<Visual Studio installation folder>Team Tools\DiagnosticsHub\Collector\AgentConfigs\```

Pour télécharger et afficher les fichiers de configuration de l’agent, consultez les liens suivants :

- https://aka.ms/vs/diaghub/agentconfig/cpubase
- https://aka.ms/vs/diaghub/agentconfig/cpuhigh
- https://aka.ms/vs/diaghub/agentconfig/cpulow
- https://aka.ms/vs/diaghub/agentconfig/database
- https://aka.ms/vs/diaghub/agentconfig/dotnetasyncbase
- https://aka.ms/vs/diaghub/agentconfig/dotnetallocbase
- https://aka.ms/vs/diaghub/agentconfig/dotnetalloclow
- https://aka.ms/vs/diaghub/agentconfig/dotnetcountersbase

Les configurations CpuUsage (base/haute/basse) correspondent aux données collectées pour l’outil de profilage de l’utilisation de l' [UC](../profiling/cpu-usage.md) .
Les configurations DotNetObjectAlloc (base/faible) correspondent aux données collectées pour l' [outil d’allocation d’objets .net](../profiling/dotnet-alloc-tool.md).

Les configurations Base/Low/High font référence au taux d’échantillonnage. Par exemple, Low correspond à 100 échantillons/seconde et High à 4 000 échantillons/seconde.

Pour que l’outil *VSDiagnostics.exe* fonctionne avec un agent de collecte, il nécessite une DLL et un CLSID COM pour l’agent approprié. Ce dernier peut également avoir des options de configuration supplémentaires. Si vous utilisez un agent sans fichier de configuration, utilisez le format dans la commande suivante.

```cmd
VSDiagnostics.exe start <id> /attach:<pid> /loadAgent:<agentCLSID>;<agentName>[;<config>]
```

## <a name="permissions"></a>Autorisations

Pour profiler une application qui nécessite des autorisations élevées, vous devez le faire à partir d’une invite de commandes avec élévation de privilèges.
