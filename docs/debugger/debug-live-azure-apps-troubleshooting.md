---
title: Problèmes connus et dépannage pour le débogage de l’instantané | Documents Microsoft
ms.date: 11/07/2017
ms.technology:
- vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- debugger
ms.assetid: 511a0697-c68a-4988-9e29-8d0166ca044a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ae5da4031ceb2716970b028fb15c11348df89c4a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="troubleshooting-and-known-issues-for-snapshot-debugging-in-visual-studio"></a>Problèmes connus et dépannage pour la capture instantanée de débogage dans Visual Studio

Si les étapes décrites dans cette rubrique ne résolvent pas votre problème, contactez snaphelp@microsoft.com.

## <a name="issue-snappoint-does-not-turn-on"></a>Problème : Snappoint n’active pas

Si vous voyez une icône d’avertissement ![icône d’avertissement Snappoint](../debugger/media/snapshot-troubleshooting-snappoint-warning-icon.png "icône d’avertissement Snappoint") avec votre snappoint au lieu de l’icône snappoint régulière, puis le snappoint n’est pas activé.

![N’active pas Snappoint](../debugger/media/snapshot-troubleshooting-dont-turn-on.png "Snappoint n’active pas")

Effectuez les étapes suivantes :

1. Assurez-vous que vous avez la même version de code source qui a été utilisée pour générer et déployer votre app.isua1. Assurez-vous que vous chargez les symboles appropriés pour votre déploiement. Pour ce faire, consultez la **Modules** fenêtre lors du débogage de l’instantané et vérifiez que la colonne du fichier de symboles affiche un fichier .pdb chargé pour le module que vous déboguez. Notez que le débogueur d’instantané tente de se télécharger automatiquement et d’utiliser des symboles pour votre déploiement.

## <a name="issue-symbols-do-not-load-when-i-open-a-snapshot"></a>Problème : Les symboles ne se chargent pas lorsque j’ouvre une capture instantanée

Si vous voyez suite de fenêtre, les symboles n’a pas chargé.

![Ne pas chargent de symboles](../debugger/media/snapshot-troubleshooting-symbols-wont-load.png "ne pas chargent de symboles")

Effectuez les étapes suivantes :

- Cliquez sur le **modifier les paramètres des symboles...** lien de cette page. Dans le **débogage > symboles** paramètres, ajoutez un répertoire de cache de symboles. Redémarrez le débogage de capture instantanée après que le chemin d’accès des symboles a été définie.

   Les symboles ou les fichiers .pdb, disponibles dans votre projet doivent correspondre à votre déploiement du Service d’applications. La plupart des déploiements (déploiement via Visual Studio, l’élément de configuration/CD avec VSTS ou Kudu, etc.) publiera les fichiers de symboles sur votre service de l’application. Définir le répertoire de cache de symboles permet à Visual Studio utiliser ces symboles.

   ![Paramètres de symboles](../debugger/media/snapshot-troubleshooting-symbol-settings.png "de symboles de paramètres")

- Également, si votre organisation utilise un serveur de symboles ou supprime les symboles dans un autre chemin d’accès, vous pouvez utiliser les paramètres des symboles pour charger les symboles appropriés pour votre déploiement.

## <a name="issue-i-cannot-see-the-attach-snapshot-debugger-option-in-the-cloud-explorer"></a>Problème : je ne peux pas voir l’option « Attacher le débogueur instantané » dans l’Explorateur de Cloud

Effectuez les étapes suivantes :

- Vérifiez que le composant de débogueur de l’instantané est installé. Ouvrez le programme d’installation Visual Studio et vérifiez la **instantané débogueur** composant dans la charge de travail Azure.
- Assurez-vous que votre application est prise en charge. Actuellement, seuls ASP.NET (4.6.1+) et les applications ASP.NET Core (2.0 +) déployées vers les Services d’application Azure sont pris en charge.

## <a name="issue-i-only-see-throttled-snapshots-in-the-diagnostic-tools"></a>Problème : je ne vois limitée des instantanés dans les outils de Diagnostic

![THROTTLED snappoint](../debugger/media/snapshot-troubleshooting-throttled-snapshots.png "limitée snappoint")

Effectuez les étapes suivantes :

- Instantanés occupent très peu de mémoire, mais ont une charge dédiée. Si le débogueur de l’instantané détecte que votre serveur est soumis à une charge mémoire élevée, il ne prendra pas des instantanés. Vous pouvez supprimer les instantanés déjà capturées par l’arrêt de la session du débogueur de l’instantané, puis réessayez.

## <a name="known-issues"></a>Problèmes connus

- Débogage d’instantané avec plusieurs clients Visual Studio sur le même Service d’application n’est pas pris en charge actuellement.
- Optimisations de langage intermédiaire de Roslyn ne sont pas pris en charge dans les projets ASP.NET Core. Pour certains projets ASP.NET Core, vous ne serez peut-être pas en mesure de certaines variables ou utiliser des variables dans les instructions conditionnelles. 
- Variables spéciales, telles que *$FUNCTION* ou *$CALLER*, ne peut pas être évaluée dans des instructions conditionnelles ou logpoints pour les projets ASP.NET Core.
- Débogage de l’instantané ne fonctionne pas sur les Services d’application qui ont [mise en cache locale](/azure/app-service/app-service-local-cache) sous tension.
- Débogage des applications de l’API de capture instantanée n’est pas pris en charge actuellement.

## <a name="site-extension-upgrade"></a>Mise à niveau des extensions de site

Débogage de l’instantané et Application Insights dépendent un ICorProfiler qui est chargé dans le processus de site et provoque des problèmes de verrouillage de fichier pendant la mise à niveau. Nous vous recommandons de ce processus afin de ne garantir aucun temps d’arrêt à votre site de production.

- Créer un [emplacement de déploiement](/azure/app-service/web-sites-staged-publishing) au sein de votre application de Service et de déployer votre site vers l’emplacement.
- Remplacez l’emplacement de production à partir de l’Explorateur de Cloud dans Visual Studio ou à partir du portail Azure.
- Arrêter le site de l’emplacement. Cette opération prendra quelques secondes de tuer le processus w3wp.exe de site à partir de toutes les instances.
- Mise à niveau de l’extension de site connecteur à partir du site Kudu ou le portail Azure (*Panneau de Service de l’application > Outils de développement > Extensions > mise à jour*).
- Démarrer le site de l’emplacement. Nous vous recommandons de visiter le site pour le préchauffage à nouveau.
- Remplacez l’emplacement de production.

## <a name="see-also"></a>Voir aussi

[Débogage dans Visual Studio](../debugger/index.md)  
[Déboguer des applications ASP.NET en direct à l’aide du débogueur de l’instantané](../debugger/debug-live-azure-applications.md)  
[FAQ pour le débogage d’instantané](../debugger/debug-live-azure-apps-faq.md)  
