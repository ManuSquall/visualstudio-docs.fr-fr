---
title: Création de dossiers de conteneurs pour les parents pour les solutions ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, creating parent containers
- source control plug-ins, creating parent containers
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3e5481e20a12fc05ccba97eef55173e5ce9b30d6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709100"
---
# <a name="create-parent-container-folders-for-solutions"></a>Créer des dossiers de conteneurs parent pour trouver des solutions
Dans la version API 1.2 de contrôle source, un utilisateur peut spécifier une seule destination de contrôle de source racine pour tous les projets Web de la solution. Cette racine unique est appelée une racine super unifiée (SUR).

 Dans la version API 1.1 de contrôle source, si l’utilisateur a ajouté une solution multiprojet au contrôle source, l’utilisateur a été invité à spécifier une destination de contrôle source pour chaque projet web.

## <a name="new-capability-flags"></a>Nouveaux drapeaux de capacité
 `SCC_CAP_CREATESUBPROJECT`

 `SCC_CAP_GETPARENTPROJECT`

## <a name="new-functions"></a>Nouvelles fonctions
- [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)

- [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)

 L’IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] crée presque toujours un dossier SUR lors de l’ajout d’une solution au contrôle des sources. Plus précisément, il le fait dans les cas suivants :

- Le projet est un projet web de partage de fichiers.

- Il existe différents moteurs pour le projet et le fichier de solution.

- Il existe différentes actions pour le projet et le fichier de solution.

- Les projets ont été ajoutés séparément (dans une solution contrôlée par source).

Dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], il est suggéré que le nom pour le dossier SUR être le même que le nom de solution sans l’extension. Le tableau suivant résume le comportement dans les deux versions.

|Fonctionnalité|Source Control Plug-in Version API 1.1|Source Control Plug-in Version API 1.2|
|-------------| - | - |
|Ajouter une solution à SCC|SccInitialiser ()<br /><br /> SccGetProjPath ()<br /><br /> SccGetProjPath ()<br /><br /> SccOpenProject ()|SccInitialiser ()<br /><br /> SccGetProjPath ()<br /><br /> SccCreateSubProject()<br /><br /> SccCreateSubProject()<br /><br /> SccOpenProject ()|
|Ajouter un projet à une solution contrôlée par la source|SccGetProjPath ()<br /><br /> OpenProject()|SccGetParentProjectPath()<br /><br /> SccOpenProject ()<br /><br />  **Note:**  Visual Studio suppose qu’une solution est un enfant direct du SUR.|

## <a name="examples"></a>Exemples
 Le tableau suivant énumère deux exemples. Dans les deux [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] cas, l’utilisateur est invité à un emplacement de destination pour la solution sous contrôle source jusqu’à ce que le *user_choice* est spécifié comme une destination. Lorsque la user_choice est spécifiée, la solution et deux projets sont ajoutés sans inciter l’utilisateur à trouver des destinations de contrôle à la source.

|La solution contient|Sur les emplacements de disque|Structure par défaut de base de données|
|-----------------------|-----------------------|--------------------------------|
|*sln1.sln*<br /><br /> Web1<br /><br /> Web2 (en)|*C : Solutions-sln1*<br /><br /> *C : 'Inetpub’wwwroot-Web1*<br /><br /> \\'server’wwwroot$'Web2|$/<user_choice>/sln1<br /><br /> $/<user_choice>/C/Web1<br /><br /> $/<user_choice>/Web2|
|*sln1.sln*<br /><br /> Web1<br /><br /> Win1 (en)|*C : Solutions-sln1*<br /><br /> *D : Inetpub-wwwroot-Web1*<br /><br /> *C : solutions-sln1-Win1*|$/<user_choice>/sln1<br /><br /> $/<user_choice>/D/web1<br /><br /> $/<user_choice>/sln1/win1|

 Le dossier et les sous-dossiers SUR sont créés, que l’opération soit annulée ou qu’elle échoue en raison d’une erreur. Ils ne sont pas automatiquement supprimés dans des conditions d’annulation ou d’erreur.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]par défaut au comportement de la version 1.1 `SCC_CAP_CREATESUBPROJECT` si `SCC_CAP_GETPARENTPROJECT` le plug-in de contrôle source ne retourne pas et les indicateurs de capacité. En outre, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] les utilisateurs de peuvent choisir de revenir au comportement de la version 1.1 en définissant la valeur de la clé suivante pour *dword:00000001*:

 **[HKEY_CURRENT_USER-Software-Microsoft-VisualStudio-8.0-SourceControl] DoNotCreateSolutionRootFolderInSourceControl** = *dword:00000001*

## <a name="see-also"></a>Voir aussi
- [Nouveauté dans la version API 1.2 du contrôle source](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
