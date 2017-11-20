---
title: "Problèmes connus et dépannage pour le débogage de l’instantané | Documents Microsoft"
ms.date: 11/07/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugger
ms.assetid: 511a0697-c68a-4988-9e29-8d0166ca044a
caps.latest.revision: "1"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5e111159029710684a1a49be2859f6ac5699a70a
ms.sourcegitcommit: 2c7f48ad6073a81fa927568793633f26cc1f0b15
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="troubleshooting-and-known-issues-for-snapshot-debugging-in-visual-studio"></a>Problèmes connus et dépannage pour la capture instantanée de débogage dans Visual Studio

Si les étapes décrites dans cette rubrique ne résolvent pas votre problème, contactez snaphelp@microsoft.com.

## <a name="issue-snappoint-does-not-turn-on"></a>Problème : Snappoint n’active pas

Si vous voyez une icône d’avertissement ![icône d’avertissement Snappoint](../debugger/media/snapshot-troubleshooting-snappoint-warning-icon.png "icône d’avertissement Snappoint") avec votre snappoint au lieu de l’icône snappoint régulière, puis le snappoint n’est pas activé.

![N’active pas Snappoint](../debugger/media/snapshot-troubleshooting-dont-turn-on.png "Snappoint n’active pas")

Effectuez les étapes suivantes :

1. Assurez-vous que vous avez la même version de code source qui a été utilisée pour générer et déployer votre application.
1. Assurez-vous que vous chargez les symboles appropriés pour votre déploiement. Pour ce faire, consultez la **Modules** fenêtre lors du débogage de l’instantané et vérifiez que la colonne du fichier de symboles affiche un fichier .pdb chargé pour le module que vous déboguez. Notez que le débogueur d’instantané tente de se télécharger automatiquement et d’utiliser des symboles pour votre déploiement.

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
- Débogage de l’instantané ne fonctionne pas sur les Services d’application qui ont [mise en cache locale](https://docs.microsoft.com/en-us/azure/app-service/app-service-local-cache) sous tension.

## <a name="see-also"></a>Voir aussi

[Débogage dans Visual Studio](../debugger/index.md)  
[Déboguer des applications ASP.NET en direct à l’aide du débogueur de l’instantané](../debugger/debug-live-azure-applications.md)  
[Forum aux questions pour le débogage de l’instantané](../debugger/debug-live-azure-apps-faq.md)  
