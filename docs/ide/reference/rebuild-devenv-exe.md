---
title: -Rebuild (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Devenv, /rebuild switch
- rebuild Devenv switch (/rebuild)
- projects [Visual Studio], rebuilding
- /rebuild Devenv switch
- applications [Visual Studio], rebuilding
ms.assetid: c5a8a4bf-0e2b-46eb-a44a-8aeb29b92c32
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: fcabe7b1ce4130eb52369ff9f16900b1979b8582
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="rebuild-devenvexe"></a>/Rebuild (devenv.exe)
Nettoie, puis génère la configuration de solution spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
devenv SolutionName /rebuild SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]  
```  
  
## <a name="arguments"></a>Arguments  
 `SolnConfigName`  
 Obligatoire. Nom de la configuration de solution à utiliser pour regénérer la solution nommée dans `SolutionName`.  
  
 `SolutionName`  
 Obligatoire. Chemin complet et nom du fichier solution.  
  
 /project `ProjName`  
 Facultatif. Chemin et nom d’un fichier projet dans la solution. Vous pouvez entrer un chemin relatif du dossier `SolutionName` vers le fichier projet, le nom d’affichage du projet ou encore le chemin complet et le nom du fichier projet.  
  
 /projectconfig `ProjConfigName`  
 Facultatif. Nom d’une configuration de build de projet à utiliser lors de la regénération du `/project` nommé.  
  
## <a name="remarks"></a>Remarques  
  
-   Ce commutateur exécute la même fonction que la commande de menu **Regénérer la solution** dans l’environnement de développement intégré (IDE).  
  
-   Placez entre guillemets doubles les chaînes contenant des espaces.  
  
-   Les informations résumées pour les nettoyages et les builds, notamment les erreurs, peuvent être affichées dans la fenêtre **Commande**, ou dans tout fichier journal spécifié avec le commutateur `/out`.  
  
## <a name="example"></a>Exemple  
 Cet exemple nettoie et regénère le projet `CSharpWinApp` en utilisant la configuration de build de projet `Debug` présente dans la configuration de solution `Debug` de `MySolution`.  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /rebuild Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug   
```  
  
## <a name="see-also"></a>Voir aussi  
 [Commutateurs de la ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)   
 [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)   
 [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)