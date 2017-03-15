---
title: "Isolé du Shell paramètres du Point d’entrée (C++) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Shell [Visual Studio], isolated mode, Start entry point
- Visual Studio shell, isolated mode, Start entry point
ms.assetid: 18f4b18b-2173-4afa-ba0a-42fe33e61118
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 9044821c2bfee0dba8ffa91f3d91afd565b8d957
ms.openlocfilehash: 13f05a147f0d9ab36d49b93cc91bcbaa7b002c70
ms.lasthandoff: 02/22/2017

---
# <a name="isolated-shell-entry-point-parameters-c"></a>Paramètres du Point d’entrée Shell isolé (C++)
Lorsqu’une application Visual Studio shell démarre, il appelle le point d’entrée de démarrage de l’interpréteur de commandes de Visual Studio. Les paramètres suivants peuvent être remplacés dans l’appel vers le point d’entrée de démarrage de l’interpréteur de commandes. Pour obtenir une description de chaque paramètre, consultez la page [. Les fichiers pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
-   AddinsAllowed  
  
-   AllowsDroppedFilesOnMainWindow  
  
-   Nom_application  
  
-   CommandLineLogo  
  
-   DefaultHomePage  
  
-   DefaultProjectsLocation  
  
-   DefaultSearchPage  
  
-   DefaultUserFilesFolderRoot  
  
-   DisableOutputWindow  
  
-   HideMiscellaneousFilesByDefault  
  
-   HideSolutionConcept  
  
-   NewProjDlgInstalledTemplatesHdr  
  
-   NewProjDlgSlnTreeNodeTitle  
  
-   SolutionFileCreatorIdentifier  
  
-   SolutionFileExt  
  
-   UserFilesSubFolderName  
  
-   UserOptsFileExt  
  
 Le modèle Visual Studio Shell isolé crée un fichier source, *solutionName*.cpp, où *solutionName* est le nom de la solution pour l’application. Ce fichier définit le point d’entrée principal de l’application, la fonction _tWinMain. Cette fonction appelle le point d’entrée de démarrage de l’interpréteur de commandes.  
  
 Vous pouvez modifier le comportement de l’application en modifiant ces paramètres lorsque l’application démarre.  
  
## <a name="parameters"></a>Paramètres  
 Le point d’entrée de démarrage de l’interpréteur de commandes de Visual Studio définit cinq paramètres. Ne modifiez pas les quatre premiers paramètres. Le cinquième paramètre accepte une liste de substitution de paramètres. Le point d’entrée de démarrage de l’interface est appelé à partir du point d’entrée principal d’une application.  
  
 Le point d’entrée de démarrage de l’interpréteur de commandes a la signature suivante.  
  
```  
typedef int (__cdecl *STARTFCN)(LPSTR, LPWSTR, int, GUID *, WCHAR *pszSettings);  
```  
  
 Si vous ne souhaitez pas remplacer les paramètres de l’application, conservez la valeur des paramètres de remplacer le paramètre comme un pointeur null.  
  
 Pour substituer un ou plusieurs paramètres, passez une chaîne Unicode qui contient les paramètres de substitution. La chaîne est une liste délimitée par des points-virgules de paires nom-valeur. Chaque paire contient le nom du paramètre de remplacement, suivi par un signe égal (=), suivi de la valeur à appliquer au paramètre.  
  
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
 Pour désactiver des compléments et modifier l’emplacement par défaut des projets pour votre application, vous pouvez définir le dernier paramètre de « AddinsAllowed=false;DefaultProjectsLocation=%USERPROFILE%\temp ».  
  
## <a name="see-also"></a>Voir aussi  
 [Personnalisation de l’interpréteur de commandes isolé](../extensibility/customizing-the-isolated-shell.md)   
 [. Fichiers pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)
