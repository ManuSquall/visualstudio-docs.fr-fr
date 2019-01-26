---
title: Recherche de Visual Studio | Microsoft Docs
ms.date: 08/21/2017
ms.topic: conceptual
helpviewer_keywords:
- deployment, VSIX
ms.assetid: 680c3b25-7901-4768-8363-6d1fcd1ea636
ms.author: heaths
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b57150a7a2ad94b4e0706f3dd21d2fe410ed813d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54944382"
---
# <a name="locate-visual-studio"></a>Localisez Visual Studio

À partir de Visual Studio 2017, vous pouvez installer plusieurs instances de la même version ou de la même édition. Cela est utile lorsque vous souhaitez afficher un aperçu des nouvelles fonctionnalités sur votre ordinateur de développement principal tout en conservant votre installation précédente. En raison de ces modifications, il n’existe aucune valeur de variable ou de Registre unique environnement que vous pouvez utiliser pour localiser une instance. Au lieu de cela, vous pouvez utiliser un [API de requête COM](https://msdn.microsoft.com/library/microsoft.visualstudio.setup.configuration.aspx) pour rechercher des instances en fonction de critères pertinents pour votre extension.

Il s’agit d’une API rapide, en lecture seule avec les packages NuGet disponibles pour le code natif et managé.

| Code | Package |
| ---- | --- |
| Natif | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Native |
| Managé | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Interop |

Vous pouvez localiser une seule instance avec un chemin d’accès ou le processus en cours ou énumérer toutes les instances. Consultez [nos exemples](https://github.com/Microsoft/vs-setup-samples) pour obtenir des exemples complets de la localisation de Visual Studio.

## <a name="tools"></a>Outils

Pour trouver Visual Studio et autres outils dans les environnements de génération, les scripts PowerShell, les programmes d’installation et les scénarios plus, il existe de nombreux outils open source vous pouvez utiliser directement ou redistribuer, ainsi que vos propres scripts.

| Projet | Description |
| ------- | ----------- |
| [vswhere](https://github.com/Microsoft/vswhere) | Seul fichier exécutable natif pour localiser les instances répondent aux critères tels que la mise en production ou en version préliminaire, quel produit est installé, et les charges de travail sont installés. Prend également en charge recherche Visual Studio 2010 et versions ultérieures, bien que moins d’informations sont retournées que pour Visual Studio 2017 et versions ultérieures. Consultez le [wiki](https://github.com/Microsoft/vswhere/wiki) pour obtenir des exemples. |
| [Applets de commande VSSetup](https://github.com/Microsoft/vssetup.powershell) | Applets de commande PowerShell prises en charge 2.0 et versions ultérieures qui retournent des informations enrichies en tant qu’objets que vous pouvez utiliser pour rechercher des instances basées sur les mêmes critères que _vswhere_ et pour découvrir les propriétés davantage sur les instances. Consultez le [wiki](https://github.com/Microsoft/vssetup.powershell/wiki) pour obtenir des exemples. |
| [VSIXBootstrapper](https://github.com/Microsoft/vsixbootstrapper) | Localise automatiquement _VSIXInstaller_ et transmet via la ligne de commande pour installer un **.vsix* fichier. Cette fonctionnalité peut être utile dans les programmes d’installation qui n’ont pas de prise en charge directe pour l’API de requête. Consultez le [wiki](https://github.com/Microsoft/vsixbootstrapper/wiki) pour obtenir des exemples. |

## <a name="see-also"></a>Voir aussi

* [Modifications apportées au programme d’installation de Visual Studio 2017](https://blogs.msdn.microsoft.com/heaths/2016/09/15/changes-to-visual-studio-15-setup/)
