---
title: Désinstallation d’un VSPackage avec Windows Installer | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d8a62692003b26afcd5b7814bdc03320fa1c453a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>Désinstallation d’un VSPackage avec Windows Installer
Dans la plupart des cas, Windows Installer peut désinstaller votre VSPackage simplement par « annulation » qu’elle a pour installer votre VSPackage. Les actions personnalisées présentées dans [commandes que doit être exécuté après l’Installation](../../extensibility/internals/commands-that-must-be-run-after-installation.md) doit être exécuté après une désinstallation ainsi. Étant donné que les appels à devenv.exe se produisent juste avant l’action standard de InstallFinalize pour l’installation et la désinstallation, les entrées de table CustomAction et InstallExecuteSequence dessert les deux cas.  
  
> [!NOTE]
>  Exécutez `devenv /setup` après la désinstallation d’un package MSI.  
  
 En règle générale, si vous ajoutez des actions personnalisées à un package Windows Installer, vous devez gérer ces actions pendant la désinstallation et la restauration. Par exemple, si vous ajoutez des actions personnalisées pour s’inscrire automatiquement à votre VSPackage, vous devez ajouter des actions personnalisées pour annuler l’inscription, trop.  
  
> [!NOTE]
>  Il est possible pour un utilisateur à installer votre VSPackage, puis désinstallez les versions de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] avec lequel il est intégré. Vous pouvez vous assurer que la désinstallation du VSPackage fonctionne dans ce scénario en éliminant les actions personnalisées qui s’exécutent du code avec des dépendances sur [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="handling-launch-conditions-at-uninstall-time"></a>Gestion des Conditions de lancement au moment de la désinstallation  
 L’action standard LaunchConditions lit les lignes de la table LaunchCondition pour afficher l’erreur messages si les conditions ne sont pas remplies. Conditions de lancement sont généralement utilisés pour garantir que les exigences système, vous pouvez généralement ignorer des conditions de lancement lors de la désinstallation en ajoutant la condition, `NOT Installed`, à la ligne LaunchConditions de la table LaunchCondition.  
  
 Une alternative consiste à ajouter `OR Installed` pour lancer des conditions qui ne sont pas importantes lors de la désinstallation. Cela garantit que la condition sera toujours true lors de la désinstallation et par conséquent, n’affiche pas le message de condition de lancement.  
  
> [!NOTE]
>  `Installed` est la propriété de que Windows Installer définit lorsqu’elle détecte que votre VSPackage a déjà été installé sur le système.  
  
## <a name="see-also"></a>Voir aussi  
 [Programme d’installation de Windows](http://msdn.microsoft.com/en-us/187d8965-c79d-4ecb-8689-10930fa8b3b5)   
 [Détection de la configuration système requise](../../extensibility/internals/detecting-system-requirements.md)