---
title: "Définir les valeurs par défaut des déploiements d’entreprise de Visual Studio | Microsoft Docs"
description: "Stratégies de domaine et autres opérations de configuration pour le déploiement d’entreprise de Visual Studio."
ms.date: 05/05/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- gpo
- policy
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9B7B4608-7A3F-4FF4-BDCE-42D9F7CE6DBA
author: heaths
ms.author: heaths
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 8f38b2707376d4bee8852ad107980fa925114d99
ms.openlocfilehash: 05c5fd9e4be4cbf7d40e27c7c97793bc2466efe3
ms.contentlocale: fr-fr
ms.lasthandoff: 05/05/2017

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

Certaines valeurs de Registre sont définies automatiquement la première fois qu’elles sont utilisées si ce n’est pas déjà fait. Cela garantit que les installations suivantes utilisent les mêmes valeurs. Celles-ci sont stockées dans la deuxième clé de Registre, `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup`.

Vous pouvez définir les valeurs de Registre suivantes.

| **Nom** | **Type** | **Default** | **Description** |
| -------- | -------- | ----------- | --------------- |
| `CachePath` | `REG_SZ` ou `REG_EXPAND_SZ` | %ProgramData%\Microsoft\VisualStudio\Packages | Répertoire dans lequel les manifestes de package et, éventuellement, les charges utiles sont stockés. Pour plus d’informations, consultez [Désactiver ou déplacer le cache du package](disable-or-move-the-package-cache.md). |
| `KeepDownloadedPayloads` | `REG_DWORD` | 1 | Conservation des charges utiles de package même après leur installation. Vous pouvez modifier la valeur à tout moment. La désactivation de la stratégie supprime les charges utiles de package en cache pour l’instance que vous réparez ou modifiez. Pour plus d’informations, consultez [Désactiver ou déplacer le cache du package](disable-or-move-the-package-cache.md). |
| `SharedInstallationPath` | `REG_SZ` ou `REG_EXPAND_SZ` | %ProgramFiles(x86)%\Microsoft Visual Studio\Shared | Répertoire dans lequel des packages partagés entre les versions ou instances de Visual Studio sont installés. Vous pouvez modifier la valeur à tout moment, mais cela n’affectera que les installations futures. Les produits déjà installés à l’ancien emplacement ne doivent pas être déplacés ou ils risquent de ne pas fonctionner correctement. |

> [!IMPORTANT]
> Si vous modifiez la stratégie de Registre `CachePath` après une installation, vous devez déplacer le cache du package existant vers le nouvel emplacement et vérifier qu’il est sécurisée pour que `SYSTEM` et `Administrators` disposent d’un contrôle total et `Everyone` d’un accès en lecture.
> Si vous ne déplacez pas le cache existant ou ne le sécurisez pas, cela risque de poser des problèmes pour les installations futures.

## <a name="see-also"></a>Voir aussi

 * [Installer Visual Studio](install-visual-studio.md)
 * [Désactiver ou déplacer le cache du package](disable-or-move-the-package-cache.md)
 * [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
 * [Signaler un problème avec Visual Studio](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

