---
title: "D&#233;sinstallation d&#39;un VSPackage avec Windows Installer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "désinstallation des packages"
  - "VSPackages, désinstallation"
  - "désinstallation des packages VS"
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# D&#233;sinstallation d&#39;un VSPackage avec Windows Installer
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Pour l'essentiel, Windows Installer peut désinstaller votre VSPackage simplement en « annulation » qu'il l'a fait pour installer votre VSPackage. Les actions personnalisées abordés dans [Commandes doivent être exécutés après l'Installation](../../extensibility/internals/commands-that-must-be-run-after-installation.md) doit être exécuté après une désinstallation ainsi. Étant donné que les appels à devenv.exe se produisent avant l'action standard InstallFinalize pour l'installation et la désinstallation, les entrées de table CustomAction et InstallExecuteSequence servent les deux cas.  
  
> [!NOTE]
>  Exécutez `devenv /setup` après la désinstallation d'un package MSI.  
  
 En règle générale, si vous ajoutez des actions personnalisées à un package Windows Installer, vous devez gérer ces actions pendant la désinstallation et la restauration. Par exemple, si vous ajoutez des actions personnalisées pour inscrire votre package VS, vous devez ajouter des actions personnalisées pour annuler son inscription, trop.  
  
> [!NOTE]
>  Il est possible pour un utilisateur d'installer votre VSPackage, puis désinstallez les versions de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] avec lequel il est intégré. Vous pouvez vous assurer que la désinstallation de votre VSPackage fonctionne dans ce scénario en éliminant les actions personnalisées qui exécutent le code avec des dépendances sur [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## Gestion des Conditions de lancement au moment de la désinstallation  
 L'action standard LaunchConditions lit les lignes du tableau pour afficher l'erreur LaunchCondition messages si les conditions ne sont pas remplies. Conditions de lancement sont généralement utilisés pour garantir que les exigences système, vous pouvez généralement ignorer des conditions de lancement lors de la désinstallation en ajoutant la condition, `NOT Installed`, à la ligne LaunchConditions de la table LaunchCondition.  
  
 Une alternative consiste à ajouter `OR Installed` pour lancer des conditions qui ne sont pas importantes lors de la désinstallation. Cela garantit que la condition sera toujours true lors de la désinstallation et par conséquent n'affichera le message d'erreur launch condition.  
  
> [!NOTE]
>  `Installed` est la propriété de que Windows Installer définit lorsqu'elle détecte que votre VSPackage a déjà été installé sur le système.  
  
## Voir aussi  
 [Windows Installer](http://msdn.microsoft.com/fr-fr/187d8965-c79d-4ecb-8689-10930fa8b3b5)   
 [Détecter la configuration système requise](../../extensibility/internals/detecting-system-requirements.md)