---
title: -Build (devenv.exe) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- builds [Team System], command-line
- /build Devenv switch
- Devenv, /build switch
- build Devenv switch
ms.assetid: ced21627-7653-455b-8821-3e31c6a448cf
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 070dcb383b25315e363b822da87409eb953a9ac7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49186402"
---
# <a name="build-devenvexe"></a>/Build (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Génère une solution à l’aide d’un fichier de configuration de solution spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Devenv SolutionName /build SolnConfigName [/project ProjName [/projectconfig ProjConfigName]]  
```  
  
## <a name="arguments"></a>Arguments  
 `SolutionName`  
 Obligatoire. Chemin complet et nom du fichier solution.  
  
 `SolnConfigName`  
 Obligatoire. Nom de la configuration de solution à utiliser pour générer la solution nommée dans `SolutionName`.  
  
 /project `ProjName`  
 Facultatif. Chemin et nom d’un fichier projet dans la solution. Vous pouvez entrer un chemin relatif du dossier `SolutionName` vers le fichier projet, le nom d’affichage du projet ou encore le chemin complet et le nom du fichier projet.  
  
 /projectconfig `ProjConfigName`  
 Facultatif. Nom d’une configuration de génération de projet à utiliser lors de la génération du `/project` nommé.  
  
## <a name="remarks"></a>Notes  
 Ce commutateur exécute la même fonction que la commande de menu **Générer la solution** dans l’environnement de développement intégré (IDE).  
  
 Placez entre guillemets doubles les chaînes contenant des espaces.  
  
 Vous pouvez afficher des informations récapitulatives sur les générations, notamment sur les erreurs, dans la fenêtre **Commande** ou dans tout fichier journal spécifié avec le commutateur `/out`.  
  
 Cette commande génère uniquement des projets qui ont été modifiés depuis la dernière génération. Pour générer tous les projets dans une solution, utilisez [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md).  
  
## <a name="example"></a>Exemple  
 Cet exemple génère le projet `CSharpConsoleApp` en utilisant la configuration de génération de projet `Debug` présente dans la configuration de solution `Debug` de `MySolution`.  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug   
```  
  
## <a name="see-also"></a>Voir aussi  
 [Génération et nettoyage de solutions et de projets dans Visual Studio](../../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)   
 [Commutateurs de la ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)   
 [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)   
 [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)



