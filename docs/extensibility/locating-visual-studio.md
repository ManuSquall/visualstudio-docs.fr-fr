---
title: Recherche de Visual Studio | Microsoft Docs
description: Vous pouvez installer plusieurs instances de la même version de Visual Studio. Découvrez comment utiliser une API de requête COM pour Rechercher l’instance de votre choix.
ms.custom: SEO-VS-2020
ms.date: 08/21/2017
ms.topic: conceptual
helpviewer_keywords:
- deployment, VSIX
ms.assetid: 680c3b25-7901-4768-8363-6d1fcd1ea636
author: leslierichardson95
ms.author: lerich
ms.workload:
- vssdk
ms.openlocfilehash: cd0fcd294983d6a6567676f06703b4bd1dd376c4
ms.sourcegitcommit: b4cc3dee59421f7089112becf128a369acadaf61
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2021
ms.locfileid: "112990504"
---
# <a name="locate-visual-studio"></a>Localiser Visual Studio

À compter de Visual Studio 2017, vous pouvez installer plusieurs instances de la même version ou même édition. Cela est utile lorsque vous souhaitez afficher un aperçu de nouvelles fonctionnalités sur votre ordinateur de développement principal tout en conservant votre installation précédente. En raison de ces modifications, il n’existe pas de variable d’environnement ou de valeur de Registre unique que vous pouvez utiliser pour localiser une instance. Au lieu de cela, vous pouvez utiliser une [API de requête com](/dotnet/api/microsoft.visualstudio.setup.configuration) pour rechercher des instances en fonction de critères relatifs à votre extension.

Il s’agit d’une API rapide en lecture seule avec des packages NuGet disponibles pour du code natif et managé.

| Code | Package |
| ---- | --- |
| Natif | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Native |
| Géré | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Interop |

Vous pouvez rechercher une seule instance en fonction d’un chemin d’accès ou du processus en cours, ou d’énumérer toutes les instances. Consultez [nos exemples](https://github.com/Microsoft/vs-setup-samples) pour obtenir des exemples complets sur la façon de localiser Visual Studio.

## <a name="tools"></a>Outils

Pour trouver Visual Studio et d’autres outils dans des environnements de génération, des scripts PowerShell, des programmes d’installation et d’autres scénarios, il existe un certain nombre d’outils open source que vous pouvez utiliser directement ou redistribuer avec vos propres scripts.

| Projet | Description |
| ------- | ----------- |
| [vswhere](https://github.com/Microsoft/vswhere) | Exécutable natif à fichier unique pour localiser des instances de critères tels que la mise en production ou la version préliminaire, le produit installé et les charges de travail installées. Prend également en charge la recherche de Visual Studio 2010 et versions ultérieures, bien que moins d’informations soient retournées pour Visual Studio 2017 et versions ultérieures. Pour obtenir des exemples, consultez le [wiki](https://github.com/Microsoft/vswhere/wiki) . |
| [Applets de commande VSSetup](https://github.com/Microsoft/vssetup.powershell) | Les applets de commande PowerShell prenait en charge 2,0 et versions ultérieures, qui retournent des informations enrichies sous forme d’objets que vous pouvez utiliser pour rechercher des instances basées sur les mêmes critères que _vswhere_ et pour découvrir encore plus de propriétés sur les instances. Pour obtenir des exemples, consultez le [wiki](https://github.com/Microsoft/vssetup.powershell/wiki) . |
| [VSIXBootstrapper](https://github.com/Microsoft/vsixbootstrapper) | Localise automatiquement _VSIXInstaller_ et passe la ligne de commande à pour installer un fichier **. vsix* . Cette fonctionnalité peut être utile dans les programmes d’installation qui n’ont pas de prise en charge directe des API de requête. Pour obtenir des exemples, consultez le [wiki](https://github.com/Microsoft/vsixbootstrapper/wiki) . |

## <a name="see-also"></a>Voir aussi

* [Modifications apportées au programme d’installation de Visual Studio 2017](https://devblogs.microsoft.com/setup/changes-to-visual-studio-15-setup/)
* [Lancer Visual Studio à l’aide de DTE](launch-visual-studio-dte.md)
