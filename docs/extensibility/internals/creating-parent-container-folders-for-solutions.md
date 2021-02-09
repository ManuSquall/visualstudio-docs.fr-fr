---
title: Création de dossiers de conteneur parents pour les solutions | Microsoft Docs
description: Découvrez comment utiliser l’API de plug-in de contrôle de code source version 1,2 pour spécifier une destination de contrôle de source racine unique pour tous les projets Web d’une solution.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, creating parent containers
- source control plug-ins, creating parent containers
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 39e61e3566f848e23fdea7b4fb4d0ea5bc181370
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903147"
---
# <a name="create-parent-container-folders-for-solutions"></a>Créer des dossiers de conteneur parents pour les solutions
Dans la version 1,2 de l’API de plug-in de contrôle de code source, un utilisateur peut spécifier une destination de contrôle de source racine unique pour tous les projets Web de la solution. Cette racine unique est appelée racine super unifiée (sur).

 Dans la version 1,1 de l’API de plug-in de contrôle de code source, si l’utilisateur a ajouté une solution multiprojet au contrôle de code source, l’utilisateur a été invité à spécifier une destination de contrôle de code source pour chaque projet Web.

## <a name="new-capability-flags"></a>Nouveaux indicateurs de capacité
 `SCC_CAP_CREATESUBPROJECT`

 `SCC_CAP_GETPARENTPROJECT`

## <a name="new-functions"></a>Nouvelles fonctions
- [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)

- [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)

 L' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE crée presque toujours un dossier sur lorsque vous ajoutez une solution au contrôle de code source. En particulier, il le fait dans les cas suivants :

- Le projet est un projet Web de partage de fichiers.

- Il existe différents lecteurs pour le projet et le fichier solution.

- Il existe différents partages pour le projet et le fichier solution.

- Les projets ont été ajoutés séparément (dans une solution sous contrôle de code source).

Dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , il est recommandé que le nom du dossier sur soit le même que le nom de la solution sans l’extension. Le tableau suivant résume le comportement des deux versions.

|Fonctionnalité|API de plug-in de contrôle de code source version 1,1|API de plug-in de contrôle de code source version 1,2|
|-------------| - | - |
|Ajouter la solution à SCC|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccGetProjPath()<br /><br /> SccOpenProject()|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccCreateSubProject()<br /><br /> SccCreateSubProject()<br /><br /> SccOpenProject()|
|Ajouter un projet à une solution sous contrôle de code source|SccGetProjPath()<br /><br /> OpenProject ()|SccGetParentProjectPath()<br /><br /> SccOpenProject()<br /><br />  **Remarque :**  Visual Studio suppose qu’une solution est un enfant direct du sur.|

## <a name="examples"></a>Exemples
 Le tableau suivant répertorie deux exemples. Dans les deux cas, l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilisateur est invité à fournir un emplacement de destination pour la solution sous contrôle de code source jusqu’à ce que le  *user_choice* soit spécifié comme destination. Lorsque le user_choice est spécifié, la solution et les deux projets sont ajoutés sans inviter l’utilisateur à fournir des destinations de contrôle de code source.

|La solution contient|Sur les emplacements des disques|Structure par défaut de la base de données|
|-----------------------|-----------------------|--------------------------------|
|*sln1. sln*<br /><br /> Web1<br /><br /> Web2|*C:\Solutions\sln1*<br /><br /> *C:\Inetpub\wwwroot\Web1*<br /><br /> \\\server\wwwroot $ \Web2|$/<user_choice>/sln1<br /><br /> $/<user_choice>/C/Web1<br /><br /> $/<user_choice>/web2|
|*sln1. sln*<br /><br /> Web1<br /><br /> Win1|*C:\Solutions\sln1*<br /><br /> *D:\Inetpub\wwwroot\Web1*<br /><br /> *C:\solutions\sln1\Win1*|$/<user_choice>/sln1<br /><br /> $/<user_choice>/D/web1<br /><br /> $/<user_choice>/sln1/win1|

 Le dossier sur et les sous-dossiers sont créés, que l’opération soit annulée ou qu’elle échoue en raison d’une erreur. Ils ne sont pas automatiquement supprimés dans les conditions d’annulation ou d’erreur.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] la valeur par défaut est le comportement de la version 1,1 si le plug-in de contrôle de code source ne retourne pas les `SCC_CAP_CREATESUBPROJECT` `SCC_CAP_GETPARENTPROJECT` indicateurs de capacité et. En outre, les utilisateurs de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] peuvent choisir de rétablir le comportement de la Version 1,1 en définissant la valeur de la clé suivante sur *DWORD : 00000001*:

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] DoNotCreateSolutionRootFolderInSourceControl**  =  *DWORD : 00000001*

## <a name="see-also"></a>Voir aussi
- [Nouveautés de l’API de plug-in de contrôle de code source version 1,2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
