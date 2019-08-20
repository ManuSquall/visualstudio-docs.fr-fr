---
title: Résoudre les problèmes du débogage de capture instantanée | Microsoft Docs
ms.custom: ''
ms.date: 04/24/2019
ms.topic: troubleshooting
helpviewer_keywords:
- debugger
ms.assetid: 511a0697-c68a-4988-9e29-8d0166ca044a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e3c66ba4a5031326ec288d3a5f2f3c4851d17ca6
ms.sourcegitcommit: 74c5360186731de07828764eb32ea1033a8c2275
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2019
ms.locfileid: "67559765"
---
# <a name="troubleshooting-and-known-issues-for-snapshot-debugging-in-visual-studio"></a>Résolution des problèmes et problèmes connus du débogage de capture instantanée dans Visual Studio.

Si les étapes décrites dans cet article ne résolvent pas votre problème, recherchez le problème sur [Communauté de développeurs](https://developercommunity.visualstudio.com/spaces/8/index.html) ou signaler un problème en choisissant **aide** > **envoyer des commentaires**   >  **Signaler un problème** dans Visual Studio.

## <a name="issue-attach-snapshot-debugger-encounters-an-http-status-code-error"></a>Problème : « Attacher le débogueur de capture instantanée » rencontre une erreur de code d’état HTTP

Si vous voyez l’erreur suivante dans le **sortie** fenêtre pendant la tentative d’attachement, il peut être un problème connu répertorié ci-dessous. Essayez les solutions proposées et si le problème persiste contactez alias précédent.

`[TIMESTAMP] Error --- Unable to Start Snapshot Debugger - Attach Snapshot Debugger failed: System.Net.WebException: The remote server returned an error: (###) XXXXXX`

### <a name="401-unauthorized"></a>(401) non autorisé

Cette erreur indique que l’appel REST émise par Visual Studio vers Azure utilise des informations d’identification non valide. Un bogue connu avec le module Azure Active Directory facile OAuth peut produire cette erreur.

Suivez ces étapes :

* Assurez-vous que votre compte de personnalisation de Visual Studio dispose des autorisations pour l’abonnement Azure et les ressources que vous joignez. Un moyen rapide pour déterminer cela consiste à vérifier si la ressource est disponible dans la boîte de dialogue à partir de **déboguer** > **attacher un débogueur de capture instantanée...**   >  **Ressource azure** > **sélectionner**, ou dans Cloud Explorer.
* Si cette erreur persiste, utilisez un des canaux de commentaires décrites au début de cet article.

### <a name="403-forbidden"></a>(403) Forbidden

Cette erreur indique que l’autorisation est refusée. Cela peut être dû à de nombreux problèmes différents.

Suivez ces étapes :

* Vérifiez que votre compte Visual Studio dispose d’un abonnement Azure valide avec les autorisations de contrôle d’accès en fonction du rôle (RBAC) nécessaires pour la ressource. Pour app service, vérifiez si vous êtes autorisé à [requête](https://docs.microsoft.com/rest/api/appservice/appserviceplans/get) le Plan App Service qui héberge votre application.
* Vérifiez que l’horodatage de votre ordinateur client est correct et à jour. Serveurs avec un cachet temporel hors tension par plus de 15 minutes de l’horodatage de la demande généralement cette erreur produisent.
* Si cette erreur persiste, utilisez un des canaux de commentaires décrites au début de cet article.

### <a name="404-not-found"></a>(404) introuvable

Cette erreur indique que le site Web n’a pas pu être trouvé sur le serveur.

Suivez ces étapes :

* Vérifiez que vous avez un site Web déployé et en cours d’exécution sur la ressource App Service que vous joignez à.
* Vérifiez que le site est disponible à l’adresse https://\<ressource\>. azurewebsites.net
* Si cette erreur persiste, utilisez un des canaux de commentaires décrites au début de cet article.

### <a name="406-not-acceptable"></a>(406) non Acceptable

Cette erreur indique que le serveur est incapable de répondre le type défini dans l’en-tête Accept de la demande.

Suivez ces étapes :

* Vérifiez que votre site est disponible à l’adresse https://\<ressource\>. azurewebsites.net
* Vérifiez que votre site n’a pas migré vers les nouvelles instances. Débogueur de capture instantanée utilise la notion de ARRAffinity pour router les demandes à des instances spécifiques, ce qui peuvent générer cette erreur par intermittence.
* Si cette erreur persiste, utilisez un des canaux de commentaires décrites au début de cet article.

### <a name="409-conflict"></a>Conflit (409)

Cette erreur indique que la demande est en conflit avec l’état actuel du serveur.

Il s’agit d’un problème connu qui se produit lorsqu’un utilisateur tente d’attacher le débogueur de capture instantanée par rapport à un service app service qui a activé application Insights. Application Insights définit AppSettings avec une casse différente que Visual Studio, à l’origine de ce problème.

::: moniker range=">= vs-2019"
Nous avons résolu ceci dans Visual Studio 2019.
::: moniker-end

Suivez ces étapes :

::: moniker range="vs-2017"

* Dans le portail Azure, vérifiez que l’AppSettings pour SnapshotDebugger (SNAPSHOTDEBUGGER_EXTENSION_VERSION) et InstrumentationEngine (INSTRUMENTATIONENGINE_EXTENSION_VERSION) sont en majuscules. Dans le cas contraire, mettre à jour les paramètres manuellement, ce qui force un redémarrage du site.
::: moniker-end
* Si cette erreur persiste, utilisez un des canaux de commentaires décrites au début de cet article.

### <a name="500-internal-server-error"></a>Erreur de serveur interne (500)

Cette erreur indique que le site est complètement arrêtée ou que le serveur ne peut pas traiter la demande. Instantané débogueur ne fonctionne que sur les applications en cours d’exécution. [Débogueur de captures instantanées application Insights](https://docs.microsoft.com/azure/azure-monitor/app/snapshot-debugger) fournit la prise d’instantanés sur les exceptions et peut être le meilleur outil pour vos besoins.

### <a name="502-bad-gateway"></a>Passerelle incorrecte (502)

Cette erreur indique un problème réseau côté serveur et peut être temporaire.

Suivez ces étapes :

* Essayez d’attendre quelques minutes avant d’attacher le débogueur de capture instantanée à nouveau.
* Si cette erreur persiste, utilisez un des canaux de commentaires décrites au début de cet article.

## <a name="issue-snappoint-does-not-turn-on"></a>Problème : Point d’ancrage n’active pas

Si une icône d’avertissement ![Icône d’avertissement de snappoint](../debugger/media/snapshot-troubleshooting-snappoint-warning-icon.png "Icône d’avertissement de snappoint") apparaît sur le snappoint au lieu de l’icône standard, c’est le signe que le snappoint n’est pas activé.

![Le snappoint ne s’active pas](../debugger/media/snapshot-troubleshooting-dont-turn-on.png "Le snappoint ne s’active pas")

Suivez ces étapes :

1. Assurez-vous que vous disposez de la même version de code source qui a été utilisé pour générer et déployer votre application. Assurez-vous de charger les symboles adaptés à votre déploiement. Pour cela, affichez la fenêtre **Modules** pendant le débogage de capture instantanée et vérifiez que la colonne Fichier de symboles indique qu’un fichier .pdb est chargé pour le module en cours de débogage. Le Débogueur de capture instantanée tentera de télécharger et d’utiliser automatiquement les symboles de votre déploiement.

## <a name="issue-symbols-do-not-load-when-i-open-a-snapshot"></a>Problème : Symboles ne se chargent pas lorsque j’ouvre une capture instantanée

Si la fenêtre suivante apparaît, c’est le signe que les symboles n’ont pas été chargés.

![Les symboles ne se chargent pas](../debugger/media/snapshot-troubleshooting-symbols-wont-load.png "Les symboles ne se chargent pas")

Suivez ces étapes :

- Cliquez sur le lien **Modifier les paramètres des symboles…** sur cette page. Dans les paramètres **Débogage > Symbole**, ajoutez un répertoire de cache de symboles. Relancez le débogage de capture instantanée une fois le chemin des symboles défini.

   Les symboles, ou fichiers .pdb, disponibles dans votre projet doivent correspondre à votre déploiement App Service. La plupart des déploiements (avec Visual Studio, CI/CD avec Azure Pipelines ou Kudu, etc.) publient les fichiers de symboles avec le service App Service. Le fait de définir le répertoire de cache de symboles permet à Visual Studio d’utiliser ces symboles.

   ![Paramètres des symboles](../debugger/media/snapshot-troubleshooting-symbol-settings.png "Paramètres des symboles")

- Si, en revanche, votre organisation utilise un serveur de symboles ou place les symboles dans un autre chemin, utilisez les paramètres des symboles pour charger les symboles adaptés à votre déploiement.

## <a name="issue-i-cannot-see-the-attach-snapshot-debugger-option-in-the-cloud-explorer"></a>Problème : Je ne vois pas l’option « Attacher le débogueur instantané » dans l’Explorateur de Cloud

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

## <a name="issue-i-only-see-throttled-snapshots-in-the-diagnostic-tools"></a>Problème : Je vois seulement limité des instantanés dans les outils de Diagnostic

![Snappoint limité](../debugger/media/snapshot-troubleshooting-throttled-snapshots.png "Snappoint limité")

Suivez ces étapes :

- Les captures instantanées occupent peu de mémoire, mais présentent un coût de validation. Si le Débogueur de capture instantanée détecte que votre serveur subit une lourde charge de mémoire, il ne prend pas de captures instantanées. Pour supprimer des captures instantanées déjà prises, arrêtez la session du Débogueur de capture instantanée, puis réessayez.

::: moniker range=">= vs-2019"
## <a name="issue-snapshot-debugging-with-multiple-versions-of-the-visual-studio-gives-me-errors"></a>Problème : Débogage d’instantané avec plusieurs versions de Visual Studio me donne des erreurs

Visual Studio 2019 nécessite une version plus récente de l’extension de site de débogueur de capture instantanée sur votre Azure App Service.  Cette version n’est pas compatible avec l’ancienne version de l’extension de site de débogueur de capture instantanée utilisée par Visual Studio 2017.  Si vous essayez d’attacher le débogueur de capture instantanée dans Visual Studio 2019 à un Azure App Service qui a été déboguée précédemment par le débogueur de capture instantanée dans Visual Studio 2017, vous obtenez l’erreur suivante :

![Extension de site incompatible débogueur de capture instantanée Visual Studio 2019](../debugger/media/snapshot-troubleshooting-incompatible-vs2019.png "extension de débogueur de capture instantanée Incompatible site Visual Studio 2019")

À l’inverse, si vous utilisez Visual Studio 2017 pour attacher le débogueur de capture instantanée à un Azure App Service qui a été déboguée précédemment par le débogueur de capture instantanée dans Visual Studio 2019, vous obtiendrez l’erreur suivante :

![Extension de site incompatible débogueur de capture instantanée Visual Studio 2017](../debugger/media/snapshot-troubleshooting-incompatible-vs2017.png "extension de débogueur de capture instantanée Incompatible site Visual Studio 2017")

Pour résoudre ce problème, supprimez les paramètres d’application suivants sur le Portail Azure et joignez à nouveau le Débogueur de capture instantanée :

- INSTRUMENTATIONENGINE_EXTENSION_VERSION
- SNAPSHOTDEBUGGER_EXTENSION_VERSION
::: moniker-end

## <a name="issue-i-am-having-problems-snapshot-debugging-and-i-need-to-enable-more-logging"></a>Problème : Je rencontre des problèmes de débogage d’instantané et j’ai besoin activer la journalisation plus

### <a name="enable-agent-logs"></a>Activer les journaux d’agent

Pour activer et désactiver la journalisation d’agent, ouvrez Visual Studio et accédez à *Outils > Options > Débogueur de capture instantanée > Activer la journalisation d’agent*. Notez que, si *Supprimer les anciens journaux d’agent à chaque ouverture de session* est également activé, chaque connexion à Visual Studio a pour effet de supprimer les anciens journaux d’agent.

Les journaux d’agent se trouvent aux emplacements suivants :

- App Service :
  - Accédez au site Kudu de votre service App Service (soit votreappservice.**scm**.azurewebsites.net), puis à Console de débogage.
  - Journaux de l’agent sont stockés dans le répertoire suivant :  D:\home\LogFiles\SiteExtensions\DiagnosticsAgentLogs\
- VM/VMSS :
  - Connectez-vous à votre machine virtuelle, l’agent sont stockés comme suit :  C:\WindowsAzure\Logs\Plugins\Microsoft.Azure.Diagnostics.IaaSDiagnostics\<Version>\SnapshotDebuggerAgent_*.txt
- AKS :
  - Accédez au répertoire /tmp/diag/AgentLogs/*.

### <a name="enable-profilerinstrumentation-logs"></a>Activer les journaux de profileur/d’instrumentation

Les journaux d’instrumentation se trouvent aux emplacements suivants :

- App Service :
  - Journalisation des erreurs est automatiquement envoyée à D:\Home\LogFiles\eventlog.xml, les événements sont marqués avec `<Provider Name="Instrumentation Engine" />` ou « Points d’arrêt de la Production »
- VM/VMSS :
  - Connectez-vous à votre machine virtuelle et ouvrez l’observateur d’événements.
  - Ouvrez l’affichage suivant : *Les journaux Windows > Application*.
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
- [Déboguer des applications ASP.NET en production à l’aide du débogueur de capture instantanée](../debugger/debug-live-azure-applications.md)
- [Débogage en direct ASP.NET Azure virtuel Machines\Virtual Machines identiques à l’aide du débogueur de capture instantanée](../debugger/debug-live-azure-virtual-machines.md)
- [Déboguer ASP.NET Azure Kubernetes en direct à l’aide du débogueur de capture instantanée](../debugger/debug-live-azure-kubernetes.md)
- [FAQ pour le débogage d’instantané](../debugger/debug-live-azure-apps-faq.md)
