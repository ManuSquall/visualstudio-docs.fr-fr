---
title: -Upgrade (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- /upgrade Devenv switch
- Devenv, /upgrade switch
- upgrade Devenv switch
ms.assetid: 3468045c-5cc9-4157-9a9d-622452145d27
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 464846eaf76761008ffc351db53d92669812f691
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="upgrade-devenvexe"></a>/Upgrade (devenv.exe)
Met à jour le fichier solution et tous ses fichiers projet, ou le fichier projet spécifié, aux formats [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] actuels pour ces fichiers.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
devenv SolutionFile | ProjectFile /upgrade  
```  
  
## <a name="arguments"></a>Arguments  
 `SolutionFile`  
 Requis si vous mettez à niveau une solution entière avec ses projets. Chemin et nom d’un fichier solution. Vous pouvez entrer uniquement le nom du fichier solution, ou un chemin complet et le nom du fichier solution. Si le dossier ou le fichier nommé n’existe pas encore, il sera créé.  
  
 `ProjectFile`  
 Requis si vous mettez à niveau un projet seul. Chemin et nom d’un fichier projet dans la solution. Vous pouvez entrer uniquement le nom du fichier projet, ou un chemin complet et le nom du fichier projet. Si le dossier ou le fichier nommé n’existe pas encore, il sera créé.  
  
## <a name="remarks"></a>Remarques  
 Les sauvegardes sont créées et copiées automatiquement vers un répertoire nommé Backup, créé dans le répertoire actif.  
  
 Les solutions ou projets sous contrôle de code source doivent être extraits avant de pouvoir être mis à niveau.  
  
 L’utilisation du commutateur `/upgrade` ne démarre pas [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Les résultats de la mise à niveau peuvent être vus dans le rapport de mise à niveau pour le langage de développement de la solution ou du projet. Aucune information d’erreur ni d’utilisation n’est retournée. Pour plus d’informations sur la mise à niveau de projets dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], consultez [Porter, migrer et mettre à niveau des projets Visual Studio](../../porting/port-migrate-and-upgrade-visual-studio-projects.md).  
  
## <a name="example"></a>Exemple  
 Cet exemple met à niveau un fichier solution nommé « MyProject.sln » dans votre dossier par défaut des solutions [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
```  
devenv "MyProject.sln" /upgrade  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Commutateurs de la ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)