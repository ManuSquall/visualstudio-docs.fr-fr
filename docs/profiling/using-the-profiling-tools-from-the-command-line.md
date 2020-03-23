---
title: Utilisation des outils de profilage à partir de la ligne de commande | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command line, performance tools
- command-line tools, performance tools
- profiling tools,command line
- tools, command-line
- command line, tools
ms.assetid: 6593fa82-181e-4009-a0ed-02aa24c2c063
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1420aa9f92e8ef7564478499c78393510ad61c23
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778035"
---
# <a name="use-the-profiling-tools-from-the-command-line"></a>Utiliser les outils de profilage à partir de la ligne de commande
Vous pouvez utiliser les outils en ligne de commande des outils de profilage de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour profiler des applications à l’invite de commandes et pour automatiser le profilage à l’aide de fichiers de commandes et de scripts. Vous pouvez également générer des fichiers de rapports à une invite de commandes. Vous pouvez utiliser le profileur autonome léger pour collecter des données sur les ordinateurs où [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] n’est pas installé.

> [!NOTE]
> Les fonctionnalités de sécurité renforcée de Windows 8 et Windows Server 2012 ont imposé des changements importants dans la façon dont le profileur Visual Studio collecte les données sur ces plateformes. Les applications UWP nécessitent aussi de nouvelles techniques de collecte. Consultez [Outils d’analyse des performances sur les applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Tâches courantes

| Tâche | Contenu associé |
| - | - |
| **Définir l’emplacement des symboles :** pour afficher les noms des fonctions et des paramètres, le profileur doit avoir accès aux fichiers de symboles (.*pdb*) des fichiers binaires profilés. Ces fichiers doivent inclure les fichiers de symboles pour le système d’exploitation Microsoft et les applications que vous voulez visualiser dans votre analyse. Vous pouvez utiliser le serveur de symboles Microsoft public pour vérifier que vous disposez des fichiers .*pdb* appropriés pour les fichiers binaires Microsoft. | -   [Comment : Spécifier les emplacements des fichiers de symboles de la ligne de commande](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md) |
| **Profiler votre application :** les outils en ligne de commande et les options que vous utilisez pour profiler une application cible varient selon le type de l’application, la méthode de profilage et si la cible est une application managée ou native. | -   [Utiliser des méthodes de profilage à partir de la ligne de commande](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md)<br />-   [Applications de profil autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)<br />-   [Profil ASP.NET applications Web](../profiling/command-line-profiling-of-aspnet-web-applications.md)<br />-   [Services de profil](../profiling/command-line-profiling-of-services.md) |
| **Créer des rapports .xml et .csv :** le profilage à l’invite de commande crée des fichiers de données qui peuvent être visualisés dans l’interface pour [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Vous pouvez également générer des fichiers de données .*xml* ou de valeurs séparées par des virgules (.*csv*) à l’aide de l’outil en ligne de commande VSPerfReport. | -   [Créez des rapports de profileur à partir de la ligne de commandement](../profiling/creating-profiler-reports-from-the-command-line.md)<br />-   [VSPerfReport](../profiling/vsperfreport.md) |
| **Profiler du code sur des ordinateurs sans Visual Studio :** vous pouvez utiliser le profileur autonome des outils de profilage pour collecter des données pour les applications sur des ordinateurs où [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] n’est pas installé. | -   [Comment : Installer le profileur autonome](../profiling/how-to-install-the-stand-alone-profiler.md) |

## <a name="reference"></a>Informations de référence
- [Référence des outils de profilage de ligne de commandement](../profiling/command-line-profiling-tools-reference.md)

## <a name="see-also"></a>Voir aussi
- [Explorateur de performances](../profiling/performance-explorer.md)
