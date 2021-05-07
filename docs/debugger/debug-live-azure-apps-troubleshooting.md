---
title: Résoudre les problèmes du débogage de capture instantanée | Microsoft Docs
description: Comprendre la résolution des problèmes et les problèmes connus liés au débogage des instantanés dans Visual Studio. Chargez ICorProfiler sans entraîner de temps d’arrêt sur votre site de production.
ms.custom: SEO-VS-2020
ms.date: 04/24/2019
ms.topic: troubleshooting
helpviewer_keywords:
- debugger
ms.assetid: 511a0697-c68a-4988-9e29-8d0166ca044a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: aad883ac0c3f703b2d6a4e10d3a0ef2468cd8465
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798438"
---
# <a name="troubleshooting-and-known-issues-for-snapshot-debugging-in-visual-studio"></a>Résolution des problèmes et problèmes connus du débogage de capture instantanée dans Visual Studio.

Si les étapes décrites dans cet article ne permettent pas de résoudre votre problème, recherchez le problème sur la [communauté des développeurs](https://aka.ms/feedback/suggest?space=8) ou signalez un nouveau problème en choisissant **aide**  >  **Envoyer des commentaires**  >  **signaler un problème** dans Visual Studio.

## <a name="issue-attach-snapshot-debugger-encounters-an-http-status-code-error"></a>Problème : « attacher Débogueur de capture instantanée » rencontre une erreur de code d’état HTTP

Si vous voyez l’erreur suivante dans la fenêtre de **sortie** lors de la tentative d’attachement, il peut s’agir d’un problème connu répertorié ci-dessous. Essayez les solutions proposées et, si le problème persiste, contactez l’alias précédent.

`[TIMESTAMP] Error --- Unable to Start Snapshot Debugger - Attach Snapshot Debugger failed: System.Net.WebException: The remote server returned an error: (###) XXXXXX`

### <a name="401-unauthorized"></a>(401) non autorisé

Cette erreur indique que l’appel REST émis par Visual Studio vers Azure utilise des informations d’identification non valides. 

Suivez ces étapes :

* Assurez-vous que votre compte de personnalisation Visual Studio dispose des autorisations d’accès à l’abonnement Azure et à la ressource à laquelle vous vous connectez. Un moyen rapide de déterminer cela consiste à vérifier si la ressource est disponible dans la boîte de dialogue à partir de débogueur de capture instantanée d’attachement de **débogage**  >  **...**  >  **Ressource Azure**  >  **Sélectionnez existant** ou dans Cloud Explorer.
* Si cette erreur persiste, utilisez l’un des canaux de commentaires décrits au début de cet article.

Si vous avez activé l’authentification/autorisation (EasyAuth) sur votre App Service, vous pouvez rencontrer une erreur 401 avec LaunchAgentAsync dans le message d’erreur de la pile des appels. Assurez-vous que l' **action à effectuer lorsque la demande n’est pas authentifiée** est définie sur **autoriser les requêtes anonymes (aucune action)** dans le portail Azure et fournissez un authorization.jsdans D:\Home\sites\wwwroot avec le contenu suivant à la place. 

```
{
  "routes": [
    {
      "path_prefix": "/",
      "policies": {
        "unauthenticated_action": "RedirectToLoginPage"
      }
    },
    {
      "http_methods": [ "POST" ],
      "path_prefix": "/41C07CED-2E08-4609-9D9F-882468261608/api/agent",
      "policies": {
        "unauthenticated_action": "AllowAnonymous"
      }
    }
  ]
}
```

Le premier itinéraire sécurise efficacement votre domaine d’application de la même façon que **vous vous connectez avec [IdentityProvider]**. Le deuxième itinéraire expose le point de terminaison SnapshotDebugger AgentLaunch en dehors de l’authentification, qui effectue l’action prédéfinie de démarrage de l’agent de diagnostic SnapshotDebugger *uniquement si* l’extension de site préinstallée SnapshotDebugger est activée pour votre App service. Pour plus d’informations sur la authorization.jssur la configuration, consultez [règles d’autorisation d’URL](https://azure.github.io/AppService/2016/11/17/URL-Authorization-Rules.html).

### <a name="403-forbidden"></a>(403) Interdit

Cette erreur indique que l’autorisation est refusée. Cela peut être dû à de nombreux problèmes différents.

Suivez ces étapes :

* Vérifiez que votre compte Visual Studio dispose d’un abonnement Azure valide avec les autorisations Role-Based Access Control (RBAC) nécessaires pour la ressource. Pour AppService, vérifiez si vous disposez des autorisations nécessaires pour [interroger](/rest/api/appservice/appserviceplans/get) le plan App service hébergeant votre application.
* Vérifiez que l’horodatage de votre ordinateur client est correct et à jour. Les serveurs avec des horodateurs de plus de 15 minutes de l’horodateur de la demande génèrent généralement cette erreur.
* Si cette erreur persiste, utilisez l’un des canaux de commentaires décrits au début de cet article.

### <a name="404-not-found"></a>(404) introuvable

Cette erreur indique que le site Web est introuvable sur le serveur.

Suivez ces étapes :

* Vérifiez que vous disposez d’un site Web déployé et en cours d’exécution sur la ressource App Service à laquelle vous êtes connecté.
* Vérifiez que le site est disponible sur https:// \<resource\> . azurewebsites.net
* Vérifiez que votre application Web personnalisée en cours d’exécution ne retourne pas de code d’État 404 quand vous y accédez à https:// \<resource\> . azurewebsites.net
* Si cette erreur persiste, utilisez l’un des canaux de commentaires décrits au début de cet article.

### <a name="406-not-acceptable"></a>(406) non acceptable

Cette erreur indique que le serveur n’est pas en mesure de répondre au type défini dans l’en-tête Accept de la demande.

Suivez ces étapes :

* Vérifiez que votre site est disponible sur https:// \<resource\> . azurewebsites.net
* Vérifiez que votre site n’a pas été migré vers de nouvelles instances. Débogueur de capture instantanée utilise la notion de ARRAffinity pour acheminer les demandes vers des instances spécifiques qui peuvent générer cette erreur par intermittence.
* Si cette erreur persiste, utilisez l’un des canaux de commentaires décrits au début de cet article.

### <a name="409-conflict"></a>(409) conflit

Cette erreur indique que la demande est en conflit avec l’état du serveur actuel.

Il s’agit d’un problème connu qui se produit lorsqu’un utilisateur tente d’attacher Débogueur de capture instantanée par rapport à un AppService qui a activé ApplicationInsights. ApplicationInsights définit le AppSettings avec une casse différente de celle de Visual Studio, ce qui est à l’origine de ce problème.

::: moniker range=">= vs-2019"
Nous l’avons résolu dans Visual Studio 2019.
::: moniker-end

Suivez ces étapes :

::: moniker range="vs-2017"

* Vérifiez dans la Portail Azure que l’AppSettings pour SnapshotDebugger (SNAPSHOTDEBUGGER_EXTENSION_VERSION) et InstrumentationEngine (INSTRUMENTATIONENGINE_EXTENSION_VERSION) sont en majuscules. Si ce n’est pas le cas, mettez à jour les paramètres manuellement, ce qui force le redémarrage du site.
::: moniker-end
* Si cette erreur persiste, utilisez l’un des canaux de commentaires décrits au début de cet article.

### <a name="500-internal-server-error"></a>(500) erreur de serveur interne

Cette erreur indique que le site est complètement inactif ou que le serveur ne peut pas traiter la demande. Débogueur de capture instantanée uniquement des fonctions sur les applications en cours d’exécution. [Application Insights débogueur de capture instantanée](/azure/azure-monitor/app/snapshot-debugger) fournit des instantanés sur les exceptions et peut être l’outil le mieux adapté à vos besoins.

### <a name="502-bad-gateway"></a>(502) passerelle incorrecte

Cette erreur indique un problème réseau côté serveur et peut être temporaire.

Suivez ces étapes :

* Essayez de patienter quelques minutes avant de joindre à nouveau le Débogueur de capture instantanée.
* Si cette erreur persiste, utilisez l’un des canaux de commentaires décrits au début de cet article.

## <a name="issue-snappoint-does-not-turn-on"></a>Problème : Le snappoint ne s’active pas

Si vous voyez une icône d’avertissement ![point d’ancrage icône d’avertissement](../debugger/media/snapshot-troubleshooting-snappoint-warning-icon.png "Icône d’avertissement point d’ancrage") avec votre point d’ancrage au lieu de l’icône de point d’ancrage normale, le point d’ancrage n’est pas activé.

![Point d’ancrage n’est pas activé](../debugger/media/snapshot-troubleshooting-dont-turn-on.png "Point d’ancrage n’est pas activé")

Suivez ces étapes :

1. Assurez-vous que vous disposez de la même version du code source que celle utilisée pour créer et déployer votre application. Assurez-vous de charger les symboles adaptés à votre déploiement. Pour cela, affichez la fenêtre **Modules** pendant le débogage de capture instantanée et vérifiez que la colonne Fichier de symboles indique qu’un fichier .pdb est chargé pour le module en cours de débogage. Le Débogueur de capture instantanée tentera de télécharger et d’utiliser automatiquement les symboles de votre déploiement.

## <a name="issue-symbols-do-not-load-when-i-open-a-snapshot"></a>Problème : Les symboles ne se chargent pas à l’ouverture d’une capture instantanée

Si la fenêtre suivante apparaît, c’est le signe que les symboles n’ont pas été chargés.

![Les symboles ne sont pas chargés](../debugger/media/snapshot-troubleshooting-symbols-wont-load.png "Les symboles ne sont pas chargés")

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

![Point d’ancrage limité](../debugger/media/snapshot-troubleshooting-throttled-snapshots.png "Point d’ancrage limité")

Suivez ces étapes :

- Les captures instantanées occupent peu de mémoire, mais présentent un coût de validation. Si le Débogueur de capture instantanée détecte que votre serveur subit une lourde charge de mémoire, il ne prend pas de captures instantanées. Pour supprimer des captures instantanées déjà prises, arrêtez la session du Débogueur de capture instantanée, puis réessayez.

::: moniker range=">= vs-2019"
## <a name="issue-snapshot-debugging-with-multiple-versions-of-the-visual-studio-gives-me-errors"></a>Problème : Le débogage de capture instantanée avec plusieurs versions de Visual Studio donne des erreurs

Visual Studio 2019 requiert une version plus récente de l’extension de site Débogueur de capture instantanée sur votre Azure App Service.  Cette version n’est pas compatible avec l’ancienne version de l’extension de site Débogueur de capture instantanée utilisée par Visual Studio 2017.  Vous obtiendrez l’erreur suivante si vous essayez d’attacher le Débogueur de capture instantanée dans Visual Studio 2019 à un Azure App Service qui a été précédemment débogué par le Débogueur de capture instantanée dans Visual Studio 2017 :

![Incompatibilité de l’extension de site Débogueur de capture instantanée Visual Studio 2019](../debugger/media/snapshot-troubleshooting-incompatible-vs2019.png "Incompatibilité de l’extension de site Débogueur de capture instantanée Visual Studio 2019")

À l’inverse, si vous utilisez Visual Studio 2017 pour attacher le Débogueur de capture instantanée à un Azure App Service qui a été précédemment débogué par le Débogueur de capture instantanée dans Visual Studio 2019, vous obtiendrez l’erreur suivante :

![Incompatibilité de l’extension de site Débogueur de capture instantanée Visual Studio 2017](../debugger/media/snapshot-troubleshooting-incompatible-vs2017.png "Incompatibilité de l’extension de site Débogueur de capture instantanée Visual Studio 2017")

Pour résoudre ce problème, supprimez les paramètres d’application suivants sur le Portail Azure et joignez à nouveau le Débogueur de capture instantanée :

- INSTRUMENTATIONENGINE_EXTENSION_VERSION
- SNAPSHOTDEBUGGER_EXTENSION_VERSION
::: moniker-end

## <a name="issue-i-am-having-problems-snapshot-debugging-and-i-need-to-enable-more-logging"></a>Problème : Le débogage de capture instantanée fonctionne mal alors que j’ai besoin de davantage de journalisation

### <a name="enable-agent-logs"></a>Activer les journaux d’agent

Pour activer et désactiver la journalisation d’agent, ouvrez Visual Studio et accédez à *Outils > Options > Débogueur de capture instantanée > Activer la journalisation d’agent*. Notez que, si *Supprimer les anciens journaux d’agent à chaque ouverture de session* est également activé, chaque connexion à Visual Studio a pour effet de supprimer les anciens journaux d’agent.

Les journaux d’agent se trouvent aux emplacements suivants :

- App Service :
  - Accédez au site Kudu de votre service App Service (soit votreappservice.**scm**.azurewebsites.net), puis à Console de débogage.
  - Les journaux d’agent sont stockés dans le répertoire D:\home\LogFiles\SiteExtensions\DiagnosticsAgentLogs\.
- VM/VMSS :
  - Connectez-vous à votre machine virtuelle. les journaux de l’agent sont stockés comme suit : C:\WindowsAzure\Logs\Plugins\Microsoft.Azure.Diagnostics.IaaSDiagnostics \<Version> \ SnapshotDebuggerAgent_ *. txt
- AKS
  - Accédez au répertoire /tmp/diag/AgentLogs/*.

### <a name="enable-profilerinstrumentation-logs"></a>Activer les journaux de profileur/d’instrumentation

Les journaux d’instrumentation se trouvent aux emplacements suivants :

- App Service :
  - La journalisation des erreurs est automatiquement envoyée à D:\Home\LogFiles\eventlog.xml, les événements sont marqués avec `<Provider Name="Instrumentation Engine" />` ou « points d’arrêt de production »
- VM/VMSS :
  - Connectez-vous à votre machine virtuelle et ouvrez l’observateur d’événements.
  - Ouvrez la vue *Journaux Windows > Application*.
  - *Filtrez le journal actuel* par *Source de l’événement* avec des *Points d’arrêt de production* ou le *Moteur d’instrumentation*.
- AKS
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

- [Débogage dans Visual Studio](../debugger/index.yml)
- [Déboguer des applications ASP.NET en production avec le Débogueur de capture instantanée](../debugger/debug-live-azure-applications.md)
- [Déboguer des Machines virtuelles/groupes de machines virtuelles identiques Azure ASP.NET en production avec le Débogueur de capture instantanée](../debugger/debug-live-azure-virtual-machines.md)
- [Déboguer Azure Kubernetes ASP.NET en production avec le Débogueur de capture instantanée](../debugger/debug-live-azure-kubernetes.md)
- [Questions fréquentes (FAQ) sur le débogage d’instantané](../debugger/debug-live-azure-apps-faq.yml)
