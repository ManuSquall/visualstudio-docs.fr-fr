---
title: Création de dossiers de conteneur parents pour les solutions | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solutions, creating parent containers
- source control plug-ins, creating parent containers
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b756da118943dd94bfd3bc5220dfc398c60e2a9e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196931"
---
# <a name="creating-parent-container-folders-for-solutions"></a>Création de dossiers de conteneur parent pour les solutions
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dans la version 1,2 de l’API de plug-in de contrôle de code source, un utilisateur peut spécifier une destination de contrôle de source racine unique pour tous les projets Web de la solution. Cette racine unique est appelée racine super unifiée (sur).  
  
 Dans la version 1,1 de l’API de plug-in de contrôle de code source, si l’utilisateur a ajouté une solution multiprojet au contrôle de code source, l’utilisateur a été invité à spécifier une destination de contrôle de code source pour chaque projet Web.  
  
## <a name="new-capability-flags"></a>Nouveaux indicateurs de capacité  
 `SCC_CAP_CREATESUBPROJECT`  
  
 `SCC_CAP_GETPARENTPROJECT`  
  
## <a name="new-functions"></a>Nouvelles fonctions  
 [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)  
  
 [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)  
  
 L' [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE crée presque toujours un dossier sur lorsque vous ajoutez une solution au contrôle de code source. En particulier, il le fait dans les cas suivants :  
  
- Le projet est un projet Web de partage de fichiers.  
  
- Il existe différents lecteurs pour le projet et le fichier solution.  
  
- Il existe différents partages pour le projet et le fichier solution.  
  
- Les projets ont été ajoutés séparément (dans une solution sous contrôle de code source).  
  
  Dans, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] il est recommandé que le nom du dossier sur soit le même que le nom de la solution sans l’extension. Le tableau suivant résume le comportement des deux versions.  
  
|Fonctionnalité|API de plug-in de contrôle tSource version 1,1|API de plug-in de contrôle de code source version 1,2|  
|-------------|----------------------------------------------|---------------------------------------------|  
|Ajouter la solution à SCC|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccGetProjPath()<br /><br /> SccOpenProject()|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccCreateSubProject()<br /><br /> SccCreateSubProject()<br /><br /> SccOpenProject()|  
|Ajouter un projet à une solution sous contrôle de code source|SccGetProjPath()<br /><br /> OpenProject ()|SccGetParentProjectPath()<br /><br /> SccOpenProject () **Remarque :**  Visual Studio suppose qu’une solution est un enfant direct du sur.|  
  
## <a name="examples"></a>Exemples  
 Le tableau suivant répertorie deux exemples. Dans les deux cas, l' [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] utilisateur est invité à fournir un emplacement de destination pour la solution sous contrôle de code source jusqu’à ce que le  *user_choice* soit spécifié comme destination. Lorsque le user_choice est spécifié, la solution et les deux projets sont ajoutés sans inviter l’utilisateur à fournir des destinations de contrôle de code source.  
  
|La solution contient|Sur les emplacements des disques|Structure par défaut de la base de données|  
|-----------------------|-----------------------|--------------------------------|  
|sln1. sln<br /><br /> Web1<br /><br /> Web2|C:\Solutions\sln1<br /><br /> C:\Inetpub\wwwroot\Web1<br /><br /> \\\server\wwwroot $ \web2|$/*user_choice*/sln1<br /><br /> $/*user_choice*/C/web1<br /><br /> $/*user_choice*/web2|  
|sln1. sln<br /><br /> Web1<br /><br /> Win1|C:\Solutions\sln1<br /><br /> D:\Inetpub\wwwroot\Web1<br /><br /> C:\solutions\sln1\Win1|$/*user_choice*/sln1<br /><br /> $/*user_choice*/D/web1<br /><br /> $/*user_choice*/sln1/win1|  
  
 Le dossier sur et les sous-dossiers sont créés, que l’opération soit annulée ou échoue en raison d’une erreur. Ils ne sont pas automatiquement supprimés dans les conditions d’annulation ou d’erreur.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] la valeur par défaut est le comportement de la version 1,1 si le plug-in de contrôle de code source ne retourne pas les `SCC_CAP_CREATESUBPROJECT` `SCC_CAP_GETPARENTPROJECT` indicateurs de capacité et. En outre, les utilisateurs de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] peuvent choisir de rétablir le comportement de la Version 1,1 en définissant la valeur de la clé suivante sur DWORD : 00000001 :  
  
 [HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl" = dword : 00000001  
  
## <a name="see-also"></a>Voir aussi  
 [Nouveautés de l’API de plug-in de contrôle de code source version 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
