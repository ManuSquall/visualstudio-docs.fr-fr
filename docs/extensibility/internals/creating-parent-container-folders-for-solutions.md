---
title: Création de dossiers de conteneur Parent pour les Solutions | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, creating parent containers
- source control plug-ins, creating parent containers
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b9b48cb7862b23df325b35bba0cb3e197573e3c0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62910696"
---
# <a name="create-parent-container-folders-for-solutions"></a>Créer des dossiers pour les solutions de conteneur parent
Dans la Source de contrôle plug-in API Version 1.2, un utilisateur peut spécifier une destination de contrôle de source de racine unique pour tous les projets web dans la solution. Cette racine unique est appelée une racine d’unifiée Super (Sud).

 Dans la Source de contrôle plug-in API Version 1.1, si l’utilisateur ajouté une solution multiprojet au contrôle de code source, l’utilisateur a été invité à spécifier une destination de contrôle de code source pour chaque projet web.

## <a name="new-capability-flags"></a>Nouveaux indicateurs de capacité
 `SCC_CAP_CREATESUBPROJECT`

 `SCC_CAP_GETPARENTPROJECT`

## <a name="new-functions"></a>Nouvelles fonctions
- [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)

- [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)

 Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE crée presque toujours un dossier SUR lors de l’ajout d’une solution au contrôle de code source. Plus précisément, il le fait dans les cas suivants :

- Le projet est un projet web de partage de fichiers.

- Il existe des lecteurs différents pour le projet et le fichier solution.

- Il existe des partages différents pour le projet et le fichier solution.

- Projets ont été ajoutés séparément (dans une solution sous contrôle de code source).

Dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], il est recommandé que le nom du dossier SUR être le même que le nom de la solution sans l’extension. Le tableau suivant récapitule le comportement dans les deux versions.

|Fonctionnalité|API de plug-in Version 1.1 de contrôle de code source|API de plug-in Version 1.2 de contrôle de code source|
|-------------| - | - |
|Ajoutez la solution au contrôle de code source|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccGetProjPath()<br /><br /> SccOpenProject()|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccCreateSubProject()<br /><br /> SccCreateSubProject()<br /><br /> SccOpenProject()|
|Ajouter un projet à la solution sous contrôle de code source|SccGetProjPath()<br /><br /> OpenProject()|SccGetParentProjectPath()<br /><br /> SccOpenProject()<br /><br />  **Remarque :**  Visual Studio suppose qu’une solution est un enfant direct de le SUR.|

## <a name="examples"></a>Exemples
 Le tableau suivant répertorie les deux exemples. Dans les deux cas, le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilisateur est invité à entrer un emplacement de destination pour la solution sous contrôle de code source jusqu'à ce que le *user_choice* est spécifié en tant que destination. Lorsque l’user_choice est spécifié, la solution et deux projets sont ajoutés sans solliciter l’utilisateur pour les destinations de contrôle de code source.

|Contient de la solution|Sur les emplacements de disque|Structure de base de données par défaut|
|-----------------------|-----------------------|--------------------------------|
|*sln1.sln*<br /><br /> Web1<br /><br /> Web2|*C:\Solutions\sln1*<br /><br /> *C:\Inetpub\wwwroot\Web1*<br /><br /> \\\server\wwwroot$\Web2|$/<user_choice>/sln1<br /><br /> $/ < user_choice >/C/Web1<br /><br /> $/<user_choice>/Web2|
|*sln1.sln*<br /><br /> Web1<br /><br /> Win1|*C:\Solutions\sln1*<br /><br /> *D:\Inetpub\wwwroot\Web1*<br /><br /> *C:\solutions\sln1\Win1*|$/<user_choice>/sln1<br /><br /> $/<user_choice>/D/web1<br /><br /> $/<user_choice>/sln1/win1|

 Le dossier du Sud et les sous-dossiers sont créés indépendamment de si l’opération est annulée ou échoue en raison d’une erreur. Ils ne sont pas supprimés automatiquement dans les conditions d’annuler ou d’erreur.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] comportement de la Version 1.1 par défaut si le plug-in de contrôle de code source ne renvoie pas `SCC_CAP_CREATESUBPROJECT` et `SCC_CAP_GETPARENTPROJECT` indicateurs de capacité. En outre, les utilisateurs de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] peut choisir de restaurer le comportement de la Version 1.1 en définissant la valeur de la clé suivante à *DWORD : 00000001*:

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] DoNotCreateSolutionRootFolderInSourceControl** = *dword:00000001*

## <a name="see-also"></a>Voir aussi
- [Nouveautés de la Version 1.2 des API de plug-in de contrôle Source](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)