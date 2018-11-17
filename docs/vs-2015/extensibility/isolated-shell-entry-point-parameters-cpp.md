---
title: Isolé des paramètres de Point d’entrée interpréteur de commandes (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Shell [Visual Studio], isolated mode%2C Start entry point
- Visual Studio shell, isolated mode%2C Start entry point
ms.assetid: 18f4b18b-2173-4afa-ba0a-42fe33e61118
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 270a5c932429a518447d0029b05d3c9522db7387
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51749176"
---
# <a name="isolated-shell-entry-point-parameters-c"></a>Paramètres de Point d’entrée Shell isolé (C++)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Lorsqu’une application basée sur l’interpréteur de commandes de Visual Studio démarre, il appelle le point d’entrée de démarrage de l’interpréteur de commandes de Visual Studio. Les paramètres suivants peuvent être remplacés dans l’appel au point d’entrée de démarrage de l’interpréteur de commandes. Pour obtenir une description de chaque paramètre, consultez [. Fichiers pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
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
  
  Le modèle Visual Studio Shell isolé crée un fichier source, *solutionName*.cpp, où *solutionName* est le nom de la solution pour l’application. Ce fichier définit le point d’entrée principal pour l’application, la fonction _tWinMain. Cette fonction appelle le point d’entrée de démarrage de l’interpréteur de commandes.  
  
  Vous pouvez modifier le comportement de l’application en modifiant ces paramètres lorsque l’application démarre.  
  
## <a name="parameters"></a>Paramètres  
 Le point d’entrée de démarrage de l’interpréteur de commandes de Visual Studio définit cinq paramètres. Ne modifiez pas les quatre premiers paramètres. Le cinquième paramètre prend une liste de remplacement de paramètres. Le point d’entrée de démarrage de l’interpréteur de commandes est appelé à partir du point d’entrée principal d’une application.  
  
 Le point d’entrée de démarrage de l’interpréteur de commandes a la signature suivante.  
  
```  
typedef int (__cdecl *STARTFCN)(LPSTR, LPWSTR, int, GUID *, WCHAR *pszSettings);  
```  
  
 Si vous ne souhaitez pas remplacer les paramètres d’application, laissez la valeur des paramètres de remplacer le paramètre comme un pointeur null.  
  
 Pour substituer un ou plusieurs paramètres, passez une chaîne Unicode qui contient les paramètres de substitution. La chaîne est une liste délimitée par des points-virgules de paires nom-valeur. Chaque paire contient le nom du paramètre à remplacer, suivie d’un signe égal (=), suivi de la valeur à appliquer au paramètre.  
  
> [!NOTE]
>  N’incluez pas les espaces blancs dans les chaînes Unicode.  
  
 Pour les paramètres booléens, les chaînes suivantes représentent la valeur true ; toutes les autres chaînes représentent la valeur false. Ces chaînes respectent la casse.  
  
-   \+  
  
-   1  
  
-   -1  
  
-   actif  
  
-   true  
  
-   oui  
  
## <a name="example"></a>Exemple  
 Pour désactiver les compléments et modifier l’emplacement de projets par défaut pour votre application, vous pouvez définir le dernier paramètre à « AddinsAllowed=false;DefaultProjectsLocation=%USERPROFILE%\temp ».  
  
## <a name="see-also"></a>Voir aussi  
 [Personnalisation du Shell isolé](../extensibility/customizing-the-isolated-shell.md)   
 [Fichiers .Pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)

