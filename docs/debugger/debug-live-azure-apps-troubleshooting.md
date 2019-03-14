---
title: Résolution des problèmes de débogage d’instantané | Microsoft Docs
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
ms.openlocfilehash: 9e2213c1e573efa1811d3b578c3d7bd92f1b77f2
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57526412"
---
# <a name="troubleshooting-and-known-issues-for-snapshot-debugging-in-visual-studio"></a>Problèmes connus et dépannage pour le débogage d’instantané dans Visual Studio

Si les étapes décrites dans cet article ne résolvent pas votre problème, contactez snaphelp@microsoft.com.

## <a name="issue-snappoint-does-not-turn-on"></a>Problème : Point d’ancrage n’active pas

Si vous voyez une icône d’avertissement ![icône d’avertissement de point d’ancrage](../debugger/media/snapshot-troubleshooting-snappoint-warning-icon.png "icône d’avertissement de point d’ancrage") avec votre point d’ancrage au lieu de l’icône de point d’ancrage standard, puis le point d’ancrage n’est pas activé.

![Point d’ancrage n’active pas](../debugger/media/snapshot-troubleshooting-dont-turn-on.png "point d’ancrage n’active pas")

Procédez comme suit :

1. Assurez-vous que vous disposez de la même version de code source qui a été utilisé pour générer et déployer votre app.isua1. Assurez-vous que vous chargez les symboles appropriés pour votre déploiement. Pour ce faire, vous devez afficher le **Modules** fenêtre lors du débogage d’instantané et vérifiez que la colonne du fichier de symboles affiche un fichier .pdb chargé pour le module que vous déboguez. Le débogueur d’instantané tente de télécharger et utiliser des symboles pour votre déploiement automatiquement.

## <a name="issue-symbols-do-not-load-when-i-open-a-snapshot"></a>Problème : Les symboles ne se chargent pas lorsque j’ouvre une capture instantanée

Si vous voyez après la fenêtre, les symboles n’a pas chargé.

![Ne pas chargent de symboles](../debugger/media/snapshot-troubleshooting-symbols-wont-load.png "symboles ne se chargent pas")

Procédez comme suit :

- Cliquez sur le **modifier les paramètres des symboles...** lien de cette page. Dans le **débogage > symboles** paramètres, ajoutez un répertoire de cache de symboles. Redémarrez le débogage d’instantané une fois que le chemin des symboles a été défini.

   Les symboles, ou les fichiers .pdb disponibles dans votre projet doivent correspondre à votre déploiement d’App Service. La plupart des déploiements (déploiement via Visual Studio, CI/CD avec Azure Pipelines ou Kudu, etc.) publiera le long de vos fichiers de symboles à votre App Service. Définition du répertoire de cache de symboles permet à Visual Studio à utiliser ces symboles.

   ![Paramètres des symboles](../debugger/media/snapshot-troubleshooting-symbol-settings.png "paramètres des symboles")

- Également, si votre organisation utilise un serveur de symboles ou supprime les symboles dans un autre chemin d’accès, vous pouvez utiliser les paramètres des symboles pour charger les symboles appropriés pour votre déploiement.

## <a name="issue-i-cannot-see-the-attach-snapshot-debugger-option-in-the-cloud-explorer"></a>Problème : je ne vois pas l’option « Attacher le débogueur instantané » dans l’Explorateur de Cloud

Procédez comme suit :

- Assurez-vous que le composant de débogueur de capture instantanée est installé. Ouvrez Visual Studio Installer et vérifiez la **débogueur de capture instantanée** composant dans la charge de travail Azure.
::: moniker range="< vs-2019"
- Assurez-vous que votre application est prise en charge. Actuellement, seuls ASP.NET (4.6.1+) et les applications ASP.NET Core (2.0 +) déployées dans Azure App Services sont pris en charge.
::: moniker-end
::: moniker range=">= vs-2019"
- Vérifiez que votre application est prise en charge :
  - Azure App Services - applications ASP.NET exécutées sur .NET Framework 4.6.1 ou version ultérieure.
  - Azure App Services - applications ASP.NET Core s’exécutant sur .NET Core 2.0 ou version ultérieure sur Windows.
  - Azure applications ASP.NET de Machines virtuelles (et VMSS) - en cours d’exécution sur .NET Framework 4.6.1 ou version ultérieure.
  - Azure des Machines virtuelles (VMSS) - ASP.NET Core applications et en cours d’exécution sur .NET Core 2.0 ou version ultérieure sur Windows.
  - Services Kubernetes Azure - applications ASP.NET Core s’exécutant sur .NET Core 2.2 ou version ultérieure sur Debian 9.
  - Services Kubernetes Azure - applications ASP.NET Core s’exécutant sur .NET Core 2.2 ou version ultérieure sur 3.8 Alpine.
  - Services Kubernetes Azure - applications ASP.NET Core s’exécutant sur .NET Core 2.2 ou version ultérieure sur Ubuntu 18.04.
::: moniker-end

## <a name="issue-i-only-see-throttled-snapshots-in-the-diagnostic-tools"></a>Problème : je vois seulement limité des instantanés dans les outils de Diagnostic

![Point d’ancrage limitées](../debugger/media/snapshot-troubleshooting-throttled-snapshots.png "limitées de point d’ancrage")

Procédez comme suit :

- Instantanés occupent peu de mémoire mais ont un coût de la validation. Si le débogueur de capture instantanée détecte que votre serveur est sous une charge de mémoire importante, il ne prendre des captures instantanées. Vous pouvez supprimer les instantanés déjà capturées par l’arrêt de la session du débogueur de capture instantanée, puis réessayez.

## <a name="known-issues"></a>Problèmes connus

- Débogage d’instantané avec plusieurs clients de Visual Studio sur le même plan App Service n’est pas pris en charge actuellement.
- Optimisations de langage intermédiaire Roslyn ne sont pas pris en charge dans les projets ASP.NET Core. Pour certains projets ASP.NET Core, vous ne serez peut-être pas en mesure de voir certaines variables ou utiliser des variables dans les instructions conditionnelles.
- Variables spéciales, telles que *$FUNCTION* ou *$CALLER*, ne peut pas être évaluée dans des instructions conditionnelles ou des points de journalisation pour les projets ASP.NET Core.
- Débogage d’instantané ne fonctionne pas sur les Services d’application qui ont [mise en cache locale](/azure/app-service/app-service-local-cache) sous tension.
- Débogage des applications API d’instantané n’est pas pris en charge.

## <a name="site-extension-upgrade"></a>Mise à niveau de site Extension

Débogage d’instantané et Application Insights varient selon un ICorProfiler, qui se charge dans le processus de site et provoque des problèmes de verrouillage de fichier pendant la mise à niveau. Nous recommandons ce processus pour ne garantir l’aucun temps d’arrêt à votre site de production.

- Créer un [emplacement de déploiement](/azure/app-service/web-sites-staged-publishing) au sein de votre application de Service et déployer votre site à l’emplacement.
- Remplacez l’emplacement de production à partir de Cloud Explorer dans Visual Studio ou à partir du portail Azure.
- Arrêter le site de l’emplacement. Cela prendra quelques secondes de tuer le processus w3wp.exe de site à partir de toutes les instances.
- Mise à niveau de l’extension de site connecteur depuis le site Kudu ou le portail Azure (*Panneau de Service d’application > Outils de développement > Extensions > mises à jour*).
- Démarrer le site de l’emplacement. Nous vous recommandons de visiter le site pour le préchauffage à nouveau.
- Remplacez l’emplacement de production.

## <a name="see-also"></a>Voir aussi

- [Débogage dans Visual Studio](../debugger/index.md)
- [Déboguer des applications ASP.NET en production à l’aide du débogueur de capture instantanée](../debugger/debug-live-azure-applications.md)
- [Débogage en direct ASP.NET Azure virtuel Machines\Virtual Machines identiques à l’aide du débogueur de capture instantanée](../debugger/debug-live-azure-virtual-machines.md)
- [Déboguer ASP.NET Azure Kubernetes en direct à l’aide du débogueur de capture instantanée](../debugger/debug-live-azure-kubernetes.md)
- [FAQ pour le débogage d’instantané](../debugger/debug-live-azure-apps-faq.md)