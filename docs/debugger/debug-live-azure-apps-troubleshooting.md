---
title: Résoudre les problèmes du débogage de capture instantanée | Microsoft Docs
ms.custom: seodec18
ms.date: 11/07/2018
ms.topic: troubleshooting
helpviewer_keywords:
- debugger
ms.assetid: 511a0697-c68a-4988-9e29-8d0166ca044a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7b7916cbd3a7faa633baf53a18686779dc2b386c
ms.sourcegitcommit: 509fc3a324b7748f96a072d0023572f8a645bffc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58857760"
---
# <a name="troubleshooting-and-known-issues-for-snapshot-debugging-in-visual-studio"></a>Résolution des problèmes et problèmes connus du débogage de capture instantanée dans Visual Studio.

Si les étapes décrites dans cet article ne résolvent pas votre problème, contactez snaphelp@microsoft.com.

## <a name="issue-snappoint-does-not-turn-on"></a>Problème : Le snappoint ne s’active pas

Si une icône d’avertissement ![Icône d’avertissement de snappoint](../debugger/media/snapshot-troubleshooting-snappoint-warning-icon.png "Icône d’avertissement de snappoint") apparaît sur le snappoint au lieu de l’icône standard, c’est le signe que le snappoint n’est pas activé.

![Le snappoint ne s’active pas](../debugger/media/snapshot-troubleshooting-dont-turn-on.png "Le snappoint ne s’active pas")

Suivez ces étapes :

1. Vérifiez que vous utilisez la version du code source qui servi à générer et à déployer votre app.isua1. Assurez-vous de charger les symboles adaptés à votre déploiement. Pour cela, affichez la fenêtre **Modules** pendant le débogage de capture instantanée et vérifiez que la colonne Fichier de symboles indique qu’un fichier .pdb est chargé pour le module en cours de débogage. Le Débogueur de capture instantanée tentera de télécharger et d’utiliser automatiquement les symboles de votre déploiement.

## <a name="issue-symbols-do-not-load-when-i-open-a-snapshot"></a>Problème : Les symboles ne se chargent pas à l’ouverture d’une capture instantanée

Si la fenêtre suivante apparaît, c’est le signe que les symboles n’ont pas été chargés.

![Les symboles ne se chargent pas](../debugger/media/snapshot-troubleshooting-symbols-wont-load.png "Les symboles ne se chargent pas")

Suivez ces étapes :

- Cliquez sur le lien **Modifier les paramètres des symboles…** sur cette page. Dans les paramètres **Débogage > Symbole**, ajoutez un répertoire de cache de symboles. Relancez le débogage de capture instantanée une fois le chemin des symboles défini.

   Les symboles, ou fichiers .pdb, disponibles dans votre projet doivent correspondre à votre déploiement App Service. La plupart des déploiements (avec Visual Studio, CI/CD avec Azure Pipelines ou Kudu, etc.) publient les fichiers de symboles avec le service App Service. Le fait de définir le répertoire de cache de symboles permet à Visual Studio d’utiliser ces symboles.

   ![Paramètres des symboles](../debugger/media/snapshot-troubleshooting-symbol-settings.png "Paramètres des symboles")

- Si, en revanche, votre organisation utilise un serveur de symboles ou place les symboles dans un autre chemin, utilisez les paramètres des symboles pour charger les symboles adaptés à votre déploiement.

## <a name="issue-i-cannot-see-the-attach-snapshot-debugger-option-in-the-cloud-explorer"></a>Problème : L’option « Joindre le Débogueur de capture instantanée » n’apparaît pas dans Cloud Explorer

Suivez ces étapes :

- Vérifiez que le composant Débogueur de capture instantanée est installé. Ouvrez Visual Studio Installer et cochez le composant **Débogueur de capture instantanée** dans la charge de travail Azure.
::: moniker range="< vs-2019"
- Vérifiez que votre application est prise en charge. Actuellement, seules les applications ASP.NET (4.6.1+) et ASP.NET Core (2.0+) déployées sur Azure App Service sont prises en charge.
::: moniker-end
::: moniker range=">= vs-2019"
- Vérifiez que votre application est prise en charge :
  - Azure App Service – Applications ASP.NET exécutées sur .NET Framework 4.6.1 (ou une version ultérieure).
  - Azure App Service – Applications ASP.NET Core exécutées sur .NET Core 2.0 (ou une version ultérieure) sur Windows.
  - Machines virtuelles Azure (et groupe de machines virtuelles identiques) – Applications ASP.NET exécutées sur .NET Framework 4.6.1 (ou une version ultérieure).
  - Machines virtuelles Azure (et groupe de machines virtuelles identiques) – Applications ASP.NET Core exécutées sur .NET Core 2.0 (ou une version ultérieure) sur Windows.
  - Azure Kubernetes Services – Applications ASP.NET Core exécutées sur .NET Core 2.2 (ou une version ultérieure) sur Debian 9.
  - Azure Kubernetes Services – Applications ASP.NET Core exécutées sur .NET Core 2.2 (ou une version ultérieure) sur Alpine 3.8.
  - Azure Kubernetes Services – Applications ASP.NET Core exécutées sur .NET Core 2.2 (ou une version ultérieure) sur Ubuntu 18.04.
::: moniker-end

## <a name="issue-i-only-see-throttled-snapshots-in-the-diagnostic-tools"></a>Problème : Seules des captures instantanées limitées apparaissent dans les Outils de diagnostic

![Snappoint limité](../debugger/media/snapshot-troubleshooting-throttled-snapshots.png "Snappoint limité")

Suivez ces étapes :

- Les captures instantanées occupent peu de mémoire, mais présentent un coût de validation. Si le Débogueur de capture instantanée détecte que votre serveur subit une lourde charge de mémoire, il ne prend pas de captures instantanées. Pour supprimer des captures instantanées déjà prises, arrêtez la session du Débogueur de capture instantanée, puis réessayez.

## <a name="issue-snapshot-debugging-with-multiple-versions-of-the-visual-studio-gives-me-errors"></a>Problème : Le débogage de capture instantanée avec plusieurs versions de Visual Studio donne des erreurs

Visual Studio 2019 exige une version plus récente de l’extension de site Débogueur de capture instantanée sur le service Azure App Service.  Cette version n’est pas compatible avec l’ancienne version de l’extension de site du Débogueur de capture instantanée utilisée par Visual Studio 2017.  Si vous essayez de joindre le Débogueur de capture instantanée de Visual Studio 2019 à un service Azure App Service qui avait fait l’objet d’un débogage par le Débogueur de capture instantanée de Visual Studio 2017, vous obtenez l’erreur suivante :

![Extension de site Débogueur de capture instantanée incompatible avec Visual Studio 2019](../debugger/media/snapshot-troubleshooting-incompatible-vs2019.png "Extension de site Débogueur de capture instantanée incompatible avec Visual Studio 2019")

Si, à l’inverse, vous utilisez Visual Studio 2017 pour joindre le Débogueur de capture instantanée à un service Azure App Service qui avait fait l’objet d’un débogage par le Débogueur de capture instantanée dans Visual Studio 2019, vous obtenez l’erreur suivante :

![Extension de site Débogueur de capture instantanée incompatible avec Visual Studio 2017](../debugger/media/snapshot-troubleshooting-incompatible-vs2017.png "Extension de site Débogueur de capture instantanée incompatible avec Visual Studio 2017")

Pour résoudre ce problème, supprimez les paramètres d’application suivants sur le Portail Azure et joignez à nouveau le Débogueur de capture instantanée :

- INSTRUMENTATIONENGINE_EXTENSION_VERSION
- SNAPSHOTDEBUGGER_EXTENSION_VERSION

## <a name="issue-i-am-having-problems-snapshot-debugging-and-i-need-to-enable-more-logging"></a>Problème : Le débogage de capture instantanée fonctionne mal alors que j’ai besoin de davantage de journalisation

### <a name="enable-agent-logs"></a>Activer les journaux d’agent

Pour activer et désactiver la journalisation d’agent, ouvrez Visual Studio et accédez à *Outils > Options > Débogueur de capture instantanée > Activer la journalisation d’agent*. Notez que, si *Supprimer les anciens journaux d’agent à chaque ouverture de session* est également activé, chaque connexion à Visual Studio a pour effet de supprimer les anciens journaux d’agent.

Les journaux d’agent se trouvent aux emplacements suivants :

- App Service :
  - Accédez au site Kudu de votre service App Service (soit votreappservice.**scm**.azurewebsites.net), puis à Console de débogage.
  - Les journaux d’agent sont stockés dans le répertoire D:\home\LogFiles\SiteExtensions\DiagnosticsAgentLogs\.
- VM/VMSS :
  - Connectez-vous à votre machine virtuelle. Les journaux d’agent sont stockés  sous C:\WindowsAzure\Logs\Plugins\Microsoft.Azure.Diagnostics.IaaSDiagnostics\<Version>\SnapshotDebuggerAgent_*.txt
- AKS :
  - Accédez au répertoire /tmp/diag/AgentLogs/*.

### <a name="enable-profilerinstrumentation-logs"></a>Activer les journaux de profileur/d’instrumentation

Les journaux d’instrumentation se trouvent aux emplacements suivants :

- App Service :
  - La journalisation des erreurs est automatiquement envoyée à D:\Home\LogFiles\eventlog.xml. Les événements sont marqués <<Provider Name="Instrumentation Engine" //>> ou « Production Breakpoints ».
- VM/VMSS :
  - Connectez-vous à votre machine virtuelle et ouvrez l’observateur d’événements.
  - Ouvrez la vue *Journaux Windows > Application*.
  - *Filtrez le journal actuel* par *Source de l’événement* avec des *Points d’arrêt de production* ou le *Moteur d’instrumentation*.
- AKS :
  - Journalisation du moteur d’instrumentation à l’adresse /tmp/diag/log.txt (définissez MicrosoftInstrumentationEngine_FileLogPath dans le fichier DockerFile).
  - Journalisation ProductionBreakpoint à l’adresse /tmp/diag/shLog.txt.

## <a name="known-issues"></a>Problèmes connus

- Le débogage de capture instantanée avec plusieurs clients Visual Studio sur le même service App Service n’est pas pris en charge à l’heure actuelle.
- Les optimisations Roslyn IL ne sont pas entièrement prises en charge dans les projets ASP.NET Core. Dans certains projets ASP.NET Core, certaines variables ne s’affichent pas ou ne sont pas utilisables dans des instructions conditionnelles.
- Il n’est pas possible d’évaluer des variables spéciales comme *$FUNCTION* ou *$CALLER* dans des instructions conditionnelles ou des logpoints pour les projets ASP.NET Core.
- Le débogage de capture instantanée ne fonctionne pas sur les services App Service où la [Mise en cache locale](/azure/app-service/app-service-local-cache) est activée.
- Le débogage de capture instantanée d’API Apps n’est pas pris en charge à l’heure actuelle.

## <a name="site-extension-upgrade"></a>Mise à niveau de l’extension de site

Le débogage de capture instantanée et Application Insights dépendent d’un ICorProfiler, qui se charge dans le processus du site et provoque des problèmes de verrouillage de fichier pendant la mise à niveau. Nous recommandons ce processus pour éviter tout temps d’arrêt sur le site de production.

- Créez un [Emplacement de déploiement](/azure/app-service/web-sites-staged-publishing) dans votre service App Service et déployez-y votre site.
- Basculez de cet emplacement vers l’emplacement de production dans Cloud Explorer dans Visual Studio ou sur le Portail Azure.
- Arrêtez le site de l’emplacement de déploiement. Cela prend quelques secondes, le temps de tuer le processus w3wp.exe du site sur toutes les instances.
- Mettez à niveau l’extension de site de l’emplacement de déploiement sur le site Kudu ou le Portail Azure (*Panneau App Service > Outils de développement > Extensions > Mettre à jour*).
- Lancez le site de l’emplacement de déploiement. Nous vous recommandons de visiter le site pour l’activer à nouveau.
- Basculez de l’emplacement de production vers l’emplacement de déploiement.

## <a name="see-also"></a>Voir aussi

- [Débogage dans Visual Studio](../debugger/index.md)
- [Déboguer des applications ASP.NET en production avec le Débogueur de capture instantanée](../debugger/debug-live-azure-applications.md)
- [Déboguer des Machines virtuelles/groupes de machines virtuelles identiques Azure ASP.NET en production avec le Débogueur de capture instantanée](../debugger/debug-live-azure-virtual-machines.md)
- [Déboguer Azure Kubernetes ASP.NET en production avec le Débogueur de capture instantanée](../debugger/debug-live-azure-kubernetes.md)
- [Questions fréquentes (FAQ) sur le débogage d’instantané](../debugger/debug-live-azure-apps-faq.md)