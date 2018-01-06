---
title: Localisation de Visual Studio | Documents Microsoft
ms.custom: 
ms.date: 08/21/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: deployment, VSIX
ms.assetid: 680c3b25-7901-4768-8363-6d1fcd1ea636
ms.author: heaths
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5623ea382266fdbcd59bbe57b71522a7a1f4a31e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="locating-visual-studio"></a>Localisation de Visual Studio

À partir de Visual Studio 2017, vous pouvez installer plusieurs instances de la même version ou la même édition. Cela est utile lorsque vous souhaitez afficher un aperçu des nouvelles fonctionnalités sur votre ordinateur de développement principal tout en conservant votre installation précédente. Aucune valeur de variable ou de Registre seul environnement que vous pouvez utiliser pour localiser une instance est en raison de ces modifications. Au lieu de cela, vous pouvez utiliser un [API de requête COM](https://msdn.microsoft.com/library/microsoft.visualstudio.setup.configuration.aspx) pour rechercher des instances en fonction de critères pertinents pour votre extension.

Il s’agit d’une API rapide, en lecture seule avec les packages NuGet disponibles pour le code natif et managé.

| Code | Package |
| ---- | --- |
| Natif | https://NuGet.org/packages/Microsoft.VisualStudio.Setup.Configuration.native |
| Managé | https://NuGet.org/packages/Microsoft.VisualStudio.Setup.Configuration.Interop |

Vous pouvez localiser une seule instance donnée d’un chemin d’accès ou le processus en cours, ou énumérer toutes les instances. Consultez [nos exemples](https://github.com/Microsoft/vs-setup-samples) pour obtenir des exemples complets de la localisation de Visual Studio.

## <a name="tools"></a>Outils

Pour rechercher de Visual Studio et autres outils dans les environnements de build, les scripts PowerShell, les programmes d’installation et davantage de scénarios, nous avons un nombre d’outils open source vous pouvez utiliser directement ou redistribuer avec vos propres scripts.

| Projet | Description |
| ------- | ----------- |
| [vswhere](https://github.com/Microsoft/vswhere) | Seul fichier exécutable natif pour rechercher les instances correspondant aux critères d’ou en version préliminaire, le produit est installé et la publication des charges de travail sont installés. Prend également en charge recherche Visual Studio 2010 et versions ultérieures, bien que moins d’informations sont retournées que pour Visual Studio 2017 et les versions ultérieures. Consultez le [wiki](https://github.com/Microsoft/vswhere/wiki) pour obtenir des exemples. |
| [Applets de commande VSSetup](https://github.com/Microsoft/vssetup.powershell) | Applets de commande PowerShell prises en charge 2.0 et ultérieures qui retournent des informations détaillées en tant qu’objets que vous pouvez utiliser pour rechercher des instances basées sur les mêmes critères que _vswhere_ et pour découvrir d’autres propriétés sur les instances. Consultez le [wiki](https://github.com/Microsoft/vssetup.powershell/wiki) pour obtenir des exemples. |
| [VSIXBootstrapper](https://github.com/Microsoft/vsixbootstrapper) | Localise automatiquement _VSIXInstaller_ et transmet via la ligne de commande pour installer un _*.vsix_ fichier. Cela peut être utile dans les programmes d’installation qui n’ont pas de prise en charge l’API de requête directe. Consultez le [wiki](https://github.com/Microsoft/vsixbootstrapper/wiki) pour obtenir des exemples. |

## <a name="see-also"></a>Voir aussi

* [Modifications apportées au programme d’installation de Visual Studio 2017](https://blogs.msdn.microsoft.com/heaths/2016/09/15/changes-to-visual-studio-15-setup)
