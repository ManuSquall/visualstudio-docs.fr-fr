---
title: Désinstaller un VSPackage avec installateur Windows (fr) Microsoft Docs
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
ms.openlocfilehash: fee88e895d40d42114eaf53422503524594b485f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704281"
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>Désinstallation d’un VSPackage avec Windows Installer
Pour la plupart, Windows Install peut désinstaller votre VSPackage simplement en « défaire » ce qu’il a fait pour installer votre VSPackage. Les actions [personnalisées discutées dans les commandes qui doivent être exécutées après l’installation](../../extensibility/internals/commands-that-must-be-run-after-installation.md) doivent être exécutées après un désinstallation ainsi. Parce que les appels à devenv.exe se produisent juste avant l’action standard InstallFinalize pour l’installation et la non-réinstallation, les entrées de table CustomAction et InstallExecuteSequence servent les deux cas.

> [!NOTE]
> Exécutez `devenv /setup` après avoir désinstaller un paquet MSI.

 En règle générale, si vous ajoutez des actions personnalisées à un package d’installateur Windows, vous devez gérer ces actions lors de la désinstallation et de la restauration. Si vous ajoutez des actions personnalisées pour vous auto-enregistrer votre VSPackage, par exemple, vous devez ajouter des actions personnalisées pour le désenregistrer, aussi.

> [!NOTE]
> Il est possible pour un utilisateur d’installer votre VSPackage, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] puis de désinstaller les versions avec lesquelles il est intégré. Vous pouvez vous assurer que la non-réinstallation de votre VSPackage fonctionne dans ce scénario [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]en éliminant les actions personnalisées qui exécutent le code avec dépendances sur .

## <a name="handling-launch-conditions-at-uninstall-time"></a>Gérer les conditions de lancement à l’heure de l’insall
 L’action standard LaunchConditions lit les lignes de la table LaunchCondition pour afficher les messages d’erreur si les conditions ne sont pas remplies. Comme les conditions de lancement sont généralement utilisées pour s’assurer que les exigences du `NOT Installed`système sont remplies, vous pouvez généralement sauter les conditions de lancement pendant la désinstallation en ajoutant la condition, , à la ligne LaunchConditions de la table LaunchCondition.

 Une alternative est `OR Installed` d’ajouter à des conditions de lancement qui ne sont pas importantes lors de la désinstallation. Cela garantit que la condition sera toujours vrai pendant la désinstallation et donc n’affichera pas le message d’erreur de l’état de lancement.

> [!NOTE]
> `Installed`est la propriété Windows Installer définit quand il détecte que votre VSPackage a déjà été installé sur le système.

## <a name="see-also"></a>Voir aussi
- [Installateur Windows](https://msdn.microsoft.com/library/187d8965-c79d-4ecb-8689-10930fa8b3b5)
- [Détection de la configuration système requise](../../extensibility/internals/detecting-system-requirements.md)
