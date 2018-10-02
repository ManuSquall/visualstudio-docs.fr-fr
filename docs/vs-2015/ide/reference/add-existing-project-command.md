---
title: Ajouter un projet existant, commande | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- file.addexistingproject
helpviewer_keywords:
- Add Existing Project command
- File.AddExistingProject
ms.assetid: 71cf3e31-c76b-405b-ad6a-1b1bc654bd40
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 048ba8e43b66ac5ad4bbc1d0c09adb75a2d61e1d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47493886"
---
# <a name="add-existing-project-command"></a>Ajouter un projet existant, commande
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Ajouter projet existant, commande](https://docs.microsoft.com/visualstudio/ide/reference/add-existing-project-command).  
  
  
Ajoute un projet existant à la solution actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
File.AddExistingProject filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Facultatif. Chemin complet et nom (extension comprise) du projet à ajouter à la solution.  
  
 Si l’argument `filename` comprend des espaces, il doit être placé entre guillemets.  
  
 Si aucun nom de fichier n’est spécifié, la commande ouvre la boîte de dialogue Fichier pour que l’utilisateur puisse sélectionner un projet.  
  
## <a name="remarks"></a>Notes  
 La saisie semi-automatique tente de deviner le chemin et le nom de fichier à mesure que vous tapez.  
  
## <a name="example"></a>Exemple  
 Cet exemple ajoute le projet [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] (TestProject1) à la solution actuelle.  
  
```  
>File.AddExistingProject "c:\visual studio projects\TestProject1.vbproj"  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Fenêtre Commande](../../ide/reference/command-window.md)   
 [Zone Rechercher/Commande](../../ide/find-command-box.md)   
 [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)



