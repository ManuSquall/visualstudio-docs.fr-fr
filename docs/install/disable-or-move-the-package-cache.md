---
title: Désactiver ou déplacer le cache du package
description: Découvrez comment désactiver, activer ou déplacer le cache de packages pour les déploiements de Visual Studio.
ms.date: 04/14/2017
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- cache
- nocache
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 2429993A-3F0E-41C5-9562-FEA6AE994440
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 0584673880a56bbde0ef44ad14c24acca252c5a2
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307477"
---
# <a name="disable-or-move-the-package-cache"></a>Désactiver ou déplacer le cache du package

Le cache du package fournit une source de packages installés au cas où vous devriez réparer Visual Studio ou d’autres produits connexes quand vous ne disposez d’aucune connexion Internet. Avec certains lecteurs ou certaines configurations du système, vous pouvez cependant décider de ne pas conserver tous ces packages.
Comme le programme d’installation les télécharge en cas de besoin, si vous voulez économiser ou récupérer de l’espace disque, vous pouvez désactiver ou déplacer le cache du package.

## <a name="disable-the-package-cache"></a>Désactiver le cache du package

Avant d’installer, de modifier ou de réparer Visual Studio ou d’autres produits avec le nouveau programme d’installation, vous pouvez démarrer celui-ci avec le commutateur `--nocache`.

```shell
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" --nocache
```

Toute opération que vous effectuez sur n’importe quel produit entraîne la suppression des packages existants de ce produit et évite l’enregistrement des packages après leur installation. Si vous modifiez ou réparez Visual Studio et que les packages sont nécessaires, ils sont téléchargés automatiquement et supprimés après leur installation.

Si vous souhaitez réactiver le cache, transmettez `--cache` à la place. Comme seuls les packages nécessaires sont mis en cache, si vous devez restaurer tous les packages, vous devez réparer Visual Studio avant de vous déconnecter du réseau.

```shell
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" repair --passive --norestart --cache
```

Vous pouvez également définir la  [stratégie du Registre](set-defaults-for-enterprise-deployments.md)`KeepDownloadedPayloads` pour désactiver le cache avant d’installer, de modifier ou de réparer Visual Studio.

## <a name="move-the-package-cache"></a>Déplacer le cache du package

Une configuration du système courante consiste à installer Windows sur un disque SSD avec un plus grand disque dur (ou plusieurs) pour répondre aux besoins de développement, comme le code source, les fichiers binaires de programme, etc. Si vous voulez travailler hors connexion, vous pouvez au lieu de cela déplacer le cache du package.

Vous ne pouvez le faire pour l’instant que si vous définissez la  [stratégie du Registre](set-defaults-for-enterprise-deployments.md)`CachePath` avant d’installer, de modifier ou de réparer Visual Studio.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Voir aussi

* [Installer Visual Studio](install-visual-studio.md)
* [Définir les valeurs par défaut des déploiements d’entreprise](set-defaults-for-enterprise-deployments.md)
* [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
