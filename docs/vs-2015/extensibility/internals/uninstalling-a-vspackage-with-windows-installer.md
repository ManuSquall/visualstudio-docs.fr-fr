---
title: Désinstallation d’un VSPackage avec Windows Installer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9a309779850dd33b77b426beb5627f61c40c2c4f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675241"
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>Désinstallation d’un VSPackage avec Windows Installer
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pour l’essentiel, Windows Installer pouvez désinstaller votre VSPackage simplement en « annulant » ce qu’il a fait pour installer votre VSPackage. Les actions personnalisées présentées dans les [commandes qui doivent être exécutées après l’installation](../../extensibility/internals/commands-that-must-be-run-after-installation.md) doivent également être exécutées après une désinstallation. Étant donné que les appels à devenv.exe se produisent juste avant l’action standard InstallFinalize pour l’installation et la désinstallation, les entrées CustomAction et InstallExecuteSequence table répondent aux deux cas.  
  
> [!NOTE]
> Exécuter `devenv /setup` après la désinstallation d’un package MSI.  
  
 En règle générale, si vous ajoutez des actions personnalisées à un package Windows Installer, vous devez gérer ces actions lors de la désinstallation et de la restauration. Si vous ajoutez des actions personnalisées pour inscrire automatiquement votre VSPackage, par exemple, vous devez ajouter des actions personnalisées pour annuler son inscription.  
  
> [!NOTE]
> Il est possible pour un utilisateur d’installer votre VSPackage, puis de désinstaller les versions de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] avec lesquelles il est intégré. Vous pouvez vous assurer que la désinstallation de votre VSPackage fonctionne dans ce scénario en éliminant les actions personnalisées qui exécutent du code avec des dépendances sur [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="handling-launch-conditions-at-uninstall-time"></a>Gestion des conditions de lancement au moment de la désinstallation  
 L’action standard LaunchConditions lit les lignes de la table LaunchCondition pour afficher les messages d’erreur si les conditions ne sont pas remplies. Comme les conditions de lancement sont généralement utilisées pour s’assurer que la configuration requise est respectée, vous pouvez généralement ignorer les conditions de lancement lors de la désinstallation en ajoutant la condition, `NOT Installed` , à la ligne LaunchConditions de la table LaunchCondition.  
  
 Une alternative consiste à ajouter `OR Installed` à des conditions de lancement qui ne sont pas importantes lors de la désinstallation. Cela garantit que la condition sera toujours vraie lors de la désinstallation et, par conséquent, n’affichera pas le message d’erreur de condition de lancement.  
  
> [!NOTE]
> `Installed` la propriété Windows Installer se définit lorsqu’elle détecte que votre VSPackage a déjà été installé sur le système.  
  
## <a name="see-also"></a>Voir aussi  
 [Windows Installer](https://msdn.microsoft.com/187d8965-c79d-4ecb-8689-10930fa8b3b5)   
 [Détection de la configuration système requise](../../extensibility/internals/detecting-system-requirements.md)
