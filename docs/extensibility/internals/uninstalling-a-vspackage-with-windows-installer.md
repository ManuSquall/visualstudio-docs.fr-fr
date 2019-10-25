---
title: Désinstallation d’un VSPackage avec Windows Installer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a8e92937e848d124c18dc91b9bdfa0f020f27f20
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722129"
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>Désinstallation d’un VSPackage avec Windows Installer
Pour l’essentiel, Windows Installer pouvez désinstaller votre VSPackage simplement en « annulant » ce qu’il a fait pour installer votre VSPackage. Les actions personnalisées présentées dans les [commandes qui doivent être exécutées après l’installation](../../extensibility/internals/commands-that-must-be-run-after-installation.md) doivent également être exécutées après une désinstallation. Étant donné que les appels à devenv. exe se produisent juste avant l’action standard InstallFinalize pour l’installation et la désinstallation, les entrées CustomAction et InstallExecuteSequence table sont les deux cas.

> [!NOTE]
> Exécutez `devenv /setup` après la désinstallation d’un package MSI.

 En règle générale, si vous ajoutez des actions personnalisées à un package Windows Installer, vous devez gérer ces actions lors de la désinstallation et de la restauration. Si vous ajoutez des actions personnalisées pour inscrire automatiquement votre VSPackage, par exemple, vous devez ajouter des actions personnalisées pour annuler son inscription.

> [!NOTE]
> Il est possible pour un utilisateur d’installer votre VSPackage, puis de désinstaller les versions de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] avec lesquelles il est intégré. Vous pouvez vous assurer que la désinstallation de votre VSPackage fonctionne dans ce scénario en éliminant les actions personnalisées qui exécutent du code avec des dépendances sur les [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="handling-launch-conditions-at-uninstall-time"></a>Gestion des conditions de lancement au moment de la désinstallation
 L’action standard LaunchConditions lit les lignes de la table LaunchCondition pour afficher les messages d’erreur si les conditions ne sont pas remplies. Comme les conditions de lancement sont généralement utilisées pour s’assurer que la configuration requise est respectée, vous pouvez généralement ignorer les conditions de lancement lors de la désinstallation en ajoutant la condition, `NOT Installed`, à la ligne LaunchConditions de la table LaunchCondition.

 Une alternative consiste à ajouter `OR Installed` à des conditions de lancement qui ne sont pas importantes lors de la désinstallation. Cela garantit que la condition sera toujours vraie lors de la désinstallation et, par conséquent, n’affichera pas le message d’erreur de condition de lancement.

> [!NOTE]
> `Installed` est la propriété Windows Installer définit lorsqu’il détecte que votre VSPackage a déjà été installé sur le système.

## <a name="see-also"></a>Voir aussi
- [Windows Installer](https://msdn.microsoft.com/library/187d8965-c79d-4ecb-8689-10930fa8b3b5)
- [Détection de la configuration système requise](../../extensibility/internals/detecting-system-requirements.md)