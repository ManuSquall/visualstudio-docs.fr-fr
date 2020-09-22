---
title: Paramètres du point d’entrée de Shell isolé (C++) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Shell [Visual Studio], isolated mode%2C Start entry point
- Visual Studio shell, isolated mode%2C Start entry point
ms.assetid: 18f4b18b-2173-4afa-ba0a-42fe33e61118
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9e736343212c4bf6acd833f5740b996c6c032c3f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840073"
---
# <a name="isolated-shell-entry-point-parameters-c"></a>Paramètres de point d’entrée du Shell isolé (C++)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quand une application basée sur un shell Visual Studio démarre, elle appelle le point d’entrée de démarrage du shell Visual Studio. Les paramètres suivants peuvent être substitués dans l’appel au point d’entrée de début de l’interpréteur de commandes. Pour obtenir une description de chaque paramètre, consultez [. Fichiers pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
- AddinsAllowed  
  
- AllowsDroppedFilesOnMainWindow  
  
- AppName  
  
- CommandLineLogo  
  
- DefaultHomePage  
  
- DefaultProjectsLocation  
  
- DefaultSearchPage  
  
- DefaultUserFilesFolderRoot  
  
- DisableOutputWindow  
  
- HideMiscellaneousFilesByDefault  
  
- HideSolutionConcept  
  
- NewProjDlgInstalledTemplatesHdr  
  
- NewProjDlgSlnTreeNodeTitle  
  
- SolutionFileCreatorIdentifier  
  
- SolutionFileExt  
  
- UserFilesSubFolderName  
  
- UserOptsFileExt  
  
  Le modèle isolé Visual Studio Shell crée un fichier source, *NomSolution*. cpp, où *SolutionName* est le nom de la solution pour l’application. Ce fichier définit le point d’entrée principal pour l’application, la fonction _tWinMain. Cette fonction appelle le point d’entrée de démarrage de l’interpréteur de commandes.  
  
  Vous pouvez modifier le comportement de l’application en modifiant ces paramètres au démarrage de l’application.  
  
## <a name="parameters"></a>Paramètres  
 Le point d’entrée de début du shell Visual Studio définit cinq paramètres. Ne modifiez pas les quatre premiers paramètres. Le cinquième paramètre accepte une liste de remplacement de paramètres. Le point d’entrée de départ de l’interpréteur de commandes est appelé à partir du point d’entrée principal d’une application.  
  
 Le point d’entrée de démarrage de l’interpréteur de commandes a la signature suivante.  
  
```  
typedef int (__cdecl *STARTFCN)(LPSTR, LPWSTR, int, GUID *, WCHAR *pszSettings);  
```  
  
 Si vous ne souhaitez pas remplacer les paramètres d’application, laissez la valeur du paramètre de remplacement des paramètres en tant que pointeur null.  
  
 Pour remplacer un ou plusieurs paramètres, transmettez une chaîne Unicode qui contient les paramètres à substituer. La chaîne est une liste de paires nom-valeur séparées par des points-virgules. Chaque paire contient le nom du paramètre à remplacer, suivi d’un signe égal (=), suivi de la valeur à appliquer au paramètre.  
  
> [!NOTE]
> N’incluez pas d’espace blanc dans les chaînes Unicode.  
  
 Pour les paramètres booléens, les chaînes suivantes représentent la valeur true ; toutes les autres chaînes représentent la valeur false. Ces chaînes ne respectent pas la casse.  
  
- \+  
  
- 1  
  
- -1  
  
- on  
  
- true  
  
- Oui  
  
## <a name="example"></a> Exemple  
 Pour désactiver les compléments et changer l’emplacement des projets par défaut de votre application, vous pouvez définir le dernier paramètre sur « AddinsAllowed = false ; DefaultProjectsLocation =%USERPROFILE%\temp ».  
  
## <a name="see-also"></a>Voir aussi  
 [Personnalisation de l’interpréteur de commandes isolé](../extensibility/customizing-the-isolated-shell.md)   
 [Fichiers .Pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)
