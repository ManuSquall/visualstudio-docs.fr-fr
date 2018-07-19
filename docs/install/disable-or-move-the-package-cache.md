---
title: Désactiver ou déplacer le cache du package | Microsoft Docs
description: Découvrez comment désactiver, activer ou déplacer le cache de packages pour les déploiements de Visual Studio.
ms.date: 04/14/2017
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- cache
- nocache
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 2429993A-3F0E-41C5-9562-FEA6AE994440
author: heaths
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9c8d5ddfdc521e2c383f5f67a31f42f70f528161
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/20/2018
ms.locfileid: "36282679"
---
# <a name="disable-or-move-the-package-cache"></a>Désactiver ou déplacer le cache du package

Le cache du package fournit une source de packages installés au cas où vous devriez réparer Visual Studio ou d’autres produits connexes quand vous ne disposez d’aucune connexion Internet. Avec certains lecteurs ou certaines configurations du système, toutefois, vous pouvez décider de ne pas conserver tous ces packages.
Comme le programme d’installation les télécharge en cas de besoin, si vous souhaitez les enregistrer ou récupérer de l’espace disque, vous pouvez désactiver ou déplacer le cache du package.

## <a name="disable-the-package-cache"></a>Désactiver le cache du package

Avant d’installer, de modifier ou de réparer Visual Studio ou d’autres produits avec le nouveau programme d’installation, vous pouvez démarrer celui-ci avec le commutateur `--nocache`.

```cmd
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" --nocache
```

Toute opération que vous effectuez sur n’importe quel produit entraîne la suppression des packages existants de ce produit et évite l’enregistrement des packages après leur installation. Si vous modifiez ou réparez Visual Studio et que les packages sont nécessaires, ils sont téléchargés automatiquement et supprimés après leur installation.

Si vous souhaitez réactiver le cache, transmettez `--cache` à la place. Comme seuls les packages requis sont mis en cache, si vous devez restaurer tous les packages, vous devez réparer Visual Studio avant de vous déconnecter du réseau.

```cmd
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" repair --passive --norestart --cache
```

Vous pouvez également définir la [stratégie du Registre](set-defaults-for-enterprise-deployments.md) `KeepDownloadedPayloads` pour désactiver le cache avant d’installer, de modifier ou de réparer Visual Studio.

## <a name="move-the-package-cache"></a>Déplacer le cache du package

Une configuration du système courante consiste à installer Windows sur un disque SSD avec un plus grand disque dur (ou plusieurs) pour répondre aux besoins de développement, comme le code source, les fichiers binaires de programme, etc. Si vous souhaitez travailler hors connexion, vous pouvez plutôt déplacer le cache du package.

Vous ne pouvez le faire pour l’instant que si vous définissez la [stratégie du Registre](set-defaults-for-enterprise-deployments.md) `CachePath` avant d’installer, de modifier ou de réparer Visual Studio.

## <a name="get-support"></a>Obtenir de l’aide

Parfois, des problèmes peuvent se produire. Si votre installation de Visual Studio échoue, consultez la page [Résolution des problèmes d’installation et de mise à niveau de Visual Studio 2017](troubleshooting-installation-issues.md). Si aucune étape de résolution des problèmes ne vous aide, vous pouvez nous contacter pour une conversation en direct sur une assistance à l’installation (en anglais uniquement). Pour plus de détails, consultez la [page du support Visual Studio](https://visualstudio.microsoft.com/vs/support/#talktous).

Voici d’autres options de support :

* Vous pouvez nous signaler des problèmes au niveau d’un produit via l’outil [Signaler un problème](../ide/how-to-report-a-problem-with-visual-studio-2017.md) qui s’affiche dans le programme d’installation de Visual Studio et dans l’IDE de Visual Studio.
* Vous pouvez nous faire part d’une suggestion de produit via [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Vous pouvez suivre les problèmes au niveau d’un produit et obtenir des réponses dans la [Communauté des développeurs Visual Studio](https://developercommunity.visualstudio.com/).
* Vous pouvez également communiquer avec nous et d’autres développeurs Visual Studio en prenant part à notre [conversation Visual Studio dans la communauté Gitter](https://gitter.im/Microsoft/VisualStudio). (Cette option nécessite un compte [GitHub](https://github.com/).)

## <a name="see-also"></a>Voir aussi

* [Installer Visual Studio](install-visual-studio.md)
* [Définir les valeurs par défaut des déploiements d’entreprise](set-defaults-for-enterprise-deployments.md)
* [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
