---
title: Désinstallation d’un VSPackage avec Windows Installer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6cdf9023512f4225e2a8edcadcf589cb61547e24
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90011812"
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>Désinstallation d’un VSPackage avec Windows Installer
Pour l’essentiel, Windows Installer pouvez désinstaller votre VSPackage simplement en « annulant » ce qu’il a fait pour installer votre VSPackage. Les actions personnalisées présentées dans les [commandes qui doivent être exécutées après l’installation](../../extensibility/internals/commands-that-must-be-run-after-installation.md) doivent également être exécutées après une désinstallation. Étant donné que les appels à devenv.exe se produisent juste avant l’action standard InstallFinalize pour l’installation et la désinstallation, les entrées CustomAction et InstallExecuteSequence table répondent aux deux cas.

> [!NOTE]
> Exécuter `devenv /setup` après la désinstallation d’un package MSI.

 En règle générale, si vous ajoutez des actions personnalisées à un package Windows Installer, vous devez gérer ces actions lors de la désinstallation et de la restauration. Si vous ajoutez des actions personnalisées pour inscrire automatiquement votre VSPackage, par exemple, vous devez ajouter des actions personnalisées pour annuler son inscription.

> [!NOTE]
> Il est possible pour un utilisateur d’installer votre VSPackage, puis de désinstaller les versions de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] avec lesquelles il est intégré. Vous pouvez vous assurer que la désinstallation de votre VSPackage fonctionne dans ce scénario en éliminant les actions personnalisées qui exécutent du code avec des dépendances sur [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="handling-launch-conditions-at-uninstall-time"></a>Gestion des conditions de lancement au moment de la désinstallation
 L’action standard LaunchConditions lit les lignes de la table LaunchCondition pour afficher les messages d’erreur si les conditions ne sont pas remplies. Comme les conditions de lancement sont généralement utilisées pour s’assurer que la configuration requise est respectée, vous pouvez généralement ignorer les conditions de lancement lors de la désinstallation en ajoutant la condition, `NOT Installed` , à la ligne LaunchConditions de la table LaunchCondition.

 Une alternative consiste à ajouter `OR Installed` à des conditions de lancement qui ne sont pas importantes lors de la désinstallation. Cela garantit que la condition sera toujours vraie lors de la désinstallation et, par conséquent, n’affichera pas le message d’erreur de condition de lancement.

> [!NOTE]
> `Installed` la propriété Windows Installer se définit lorsqu’elle détecte que votre VSPackage a déjà été installé sur le système.

## <a name="see-also"></a>Voir aussi
- [Windows Installer](/previous-versions/ee231230(v=vs.100))
- [Détection de la configuration système requise](../../extensibility/internals/detecting-system-requirements.md)