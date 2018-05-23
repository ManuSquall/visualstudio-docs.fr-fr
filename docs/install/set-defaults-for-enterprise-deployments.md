---
title: Définir les valeurs par défaut des déploiements d’entreprise de Visual Studio
description: Découvrez les stratégies de domaine et autres opérations de configuration disponibles pour les déploiements en entreprise de Visual Studio.
ms.date: 05/05/2017
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- gpo
- policy
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9B7B4608-7A3F-4FF4-BDCE-42D9F7CE6DBA
author: heaths
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ffae38ca7fb57fcda26c87f3a8a866f8baf2827d
ms.sourcegitcommit: 56018fb1f52f17bf35ae2ce71c50c763486e6173
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="set-defaults-for-enterprise-deployments-of-visual-studio"></a>Définir les valeurs par défaut des déploiements d’entreprise de Visual Studio

Vous pouvez définir des stratégies de Registre qui affectent le déploiement de Visual Studio. Ces stratégies sont globales pour le nouveau programme d’installation et affectent :

- l’emplacement où certains packages partagés avec d’autres versions ou instances sont installés ;
- l’emplacement où les packages sont mis en cache ;
- l’emplacement où tous les packages sont mis en cache.

Vous pouvez définir certaines de ces stratégies à l’aide des [options de ligne de commande](use-command-line-parameters-to-install-visual-studio.md), définir des valeurs de Registre sur votre ordinateur ou même les distribuer à l’aide d’une stratégie de groupe dans une organisation.

## <a name="registry-keys"></a>Clés de Registre

Il existe plusieurs emplacements où vous pouvez définir des valeurs par défaut d’entreprise pour permettre leur contrôle via une stratégie de groupe ou directement dans le Registre. Visual Studio effectue des recherches dans l’ordre pour déterminer si des stratégies d’entreprise ont été définies ; dès qu’une valeur de stratégie est détectée dans l’ordre ci-dessous, les clés restantes sont ignorées.

1. `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\Setup`
2. `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup`
3. `HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\VisualStudio\Setup` (sur les systèmes d’exploitation 64 bits)

> [!IMPORTANT]
> Si vous ne définissez pas la clé `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\Setup`, mais l’une des autres clés, vous devez définir les deux clés restantes sur les systèmes d’exploitation 64 bits. Ce problème sera corrigé dans une prochaine mise à jour.

Certaines valeurs de Registre sont définies automatiquement la première fois qu’elles sont utilisées (si elles n’ont pas été déjà définies). De cette façon, les installations suivantes utiliseront les mêmes valeurs. Ces valeurs sont stockées dans la deuxième clé de Registre (`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup`).

Vous pouvez définir les valeurs de Registre suivantes :

| **Name** | **Type** | **Default** | **Description** |
| -------- | -------- | ----------- | --------------- |
| `CachePath` | `REG_SZ` ou `REG_EXPAND_SZ` | %ProgramData%\Microsoft\ VisualStudio\Packages | Répertoire dans lequel les manifestes de package et, éventuellement, les charges utiles sont stockés. Pour plus d’informations, consultez [Désactiver ou déplacer le cache du package](disable-or-move-the-package-cache.md). |
| `KeepDownloadedPayloads` | `REG_DWORD` | 1 | Conservation des charges utiles de package même après leur installation. Vous pouvez modifier la valeur à tout moment. La désactivation de la stratégie supprime les charges utiles de package en cache pour l’instance que vous réparez ou modifiez. Pour plus d’informations, consultez [Désactiver ou déplacer le cache du package](disable-or-move-the-package-cache.md). |
| `SharedInstallationPath` | `REG_SZ` ou `REG_EXPAND_SZ` | %ProgramFiles(x86)%\Microsoft Visual Studio\Shared | Répertoire dans lequel des packages partagés entre les versions ou instances de Visual Studio sont installés. Vous pouvez modifier la valeur à tout moment, mais cela n’affectera que les installations futures. Les produits déjà installés à l’ancien emplacement ne doivent pas être déplacés ou ils risquent de ne pas fonctionner correctement. |

> [!IMPORTANT]
> Si vous modifiez la stratégie de Registre `CachePath` après une installation, vous devez déplacer le cache du package existant vers le nouvel emplacement et vérifier qu’il est sécurisée pour que `SYSTEM` et `Administrators` disposent d’un contrôle total et `Everyone` d’un accès en lecture.
> Si vous ne déplacez pas le cache existant ou ne le sécurisez pas, cela risque de poser des problèmes pour les installations futures.

## <a name="get-support"></a>Obtenir de l’aide

Parfois, des problèmes peuvent se produire. Si votre installation de Visual Studio échoue, consultez la page [Résolution des problèmes d’installation et de mise à niveau de Visual Studio 2017](troubleshooting-installation-issues.md). Si aucune étape de résolution des problèmes ne vous aide, vous pouvez nous contacter pour une conversation en direct sur une assistance à l’installation (en anglais uniquement). Pour plus de détails, consultez la [page du support Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Voici d’autres options de support :

* Vous pouvez nous signaler des problèmes au niveau d’un produit via l’outil [Signaler un problème](../ide/how-to-report-a-problem-with-visual-studio-2017.md) qui s’affiche dans le programme d’installation de Visual Studio et dans l’IDE de Visual Studio.
* Vous pouvez nous faire part d’une suggestion de produit via [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Vous pouvez suivre les problèmes au niveau d’un produit et obtenir des réponses dans la [Communauté des développeurs Visual Studio](https://developercommunity.visualstudio.com/).
* Vous pouvez également communiquer avec nous et d’autres développeurs Visual Studio en prenant part à notre [conversation Visual Studio dans la communauté Gitter](https://gitter.im/Microsoft/VisualStudio). (Cette option nécessite un compte [GitHub](https://github.com/).)

## <a name="see-also"></a>Voir aussi

 * [Installer Visual Studio](install-visual-studio.md)
 * [Désactiver ou déplacer le cache du package](disable-or-move-the-package-cache.md)
 * [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
