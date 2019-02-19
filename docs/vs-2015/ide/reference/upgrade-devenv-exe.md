---
title: -Upgrade (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /upgrade Devenv switch
- Devenv, /upgrade switch
- upgrade Devenv switch
ms.assetid: 3468045c-5cc9-4157-9a9d-622452145d27
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 465c90736f5470f48d47336bc916ca3cb2c09b6a
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2019
ms.locfileid: "54779344"
---
# <a name="upgrade-devenvexe"></a>/Upgrade (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Met à jour le fichier solution et tous ses fichiers projet, ou le fichier projet spécifié, aux formats [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] actuels pour ces fichiers.  
  
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
  
 L’utilisation du commutateur `/upgrade` ne démarre pas [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Les résultats de la mise à niveau peuvent être vus dans le rapport de mise à niveau pour le langage de développement de la solution ou du projet. Aucune information d’erreur ni d’utilisation n’est retournée. Pour plus d’informations sur la mise à niveau des projets dans [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], consultez [Comment : résoudre les problèmes ayant échoué Visual Studio projet mises à niveau](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md).  
  
## <a name="example"></a>Exemple  
 Cet exemple met à niveau un fichier solution nommé « MyProject.sln » dans votre dossier par défaut des solutions [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
```  
devenv "MyProject.sln" /upgrade  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour dépanner les échecs de mise à niveau de projets Visual Studio](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md)   
 [Commutateurs de la ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)
