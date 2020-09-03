---
title: 'Zone de test 1 : ajouter à-ouvrir à partir du contrôle de code source | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], adding and opening solutions
- source control plug-ins, adding and opening solutions
ms.assetid: 5b3b5b08-5e9b-41be-ac72-c63957faed22
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ac7b8e5a60fe25ac22272cc28fc3ed6f903b058
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80704681"
---
# <a name="test-area-1-add-toopen-from-source-control"></a>Zone de test 1 : Ajouter à/Ouvrir à partir du contrôle de code source
Cette zone de test du plug-in de contrôle de code source traite le placement de solutions ou de projets sous contrôle de code source et leur récupération à partir du contrôle de code source.

## <a name="command-menu-access"></a>Accès au menu commande
 Les [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] chemins d’accès au menu de l’environnement de développement intégré suivants sont utilisés dans les cas de test :

- Pour [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] , ouvrez à partir du contrôle de code source : **fichier**, **ouvrir**, **Project** / **solution**de projet ; recherchez dans l' [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] emplacement.

- Pour d’autres plug-ins de contrôle de code source, ouvrez à partir du contrôle de code source : **fichier**, **contrôle de code source**, **ouvrir à partir du contrôle de code source**.

- Ajouter au contrôle de code source : **fichier**, **contrôle de code source**, **Ajouter la solution au fichier de contrôle de code source**, **contrôle de code**source, **Ajouter les projets sélectionnés au contrôle de code**source.

- Menu contextuel (projet/solution), **Ajouter la solution au contrôle de code source**.

- Ajouter à partir du contrôle de code source : **fichier**, **contrôle de code source**, **Ajouter un projet à partir du contrôle de code source**.

- Pour [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] , la commande Ajouter à partir du contrôle de code source est également disponible à partir de **fichier**, **Ajouter**, **projet existant**, Rechercher dans l' [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] emplacement.

  > [!NOTE]
  > Un chemin d’accès à un fichier local ou à un serveur IIS local (serveur Web) peut être utilisé dans ce test.

## <a name="expected-behavior"></a>Comportement attendu

- Pour chaque type de projet pris en charge, un utilisateur doit pouvoir « ajouter à » et « ouvrir à partir de » le contrôle de code source.

- Lorsqu’un projet est ajouté au contrôle de code source, un \<*ProjectName*> fichier. vspscc correspondant (fichier hint du projet) est créé. Il contient les informations de connexion et de liste des fichiers d’exclusion. Ne supprimez pas ce fichier, car il contient des informations spécifiques au projet.

- Quand une solution est ajoutée au contrôle de code source, un \<*SolutionName*> fichier. vssscc (triple S) correspondant est créé. Le fichier texte contient des informations de connexion et une liste de fichiers d’exclusion, similaire au fichier d’indication de projet. Ce fichier est temporaire et existe uniquement dans la base de données de contrôle de code source.

- Quand une solution est ouverte à partir du contrôle de code source, un \<*SolutionName*> fichier. vsscc (double S) qui existe uniquement dans la base de données de contrôle de code source est créé localement dans un fichier temporaire. Ce fichier contient le chemin d’accès du dossier de connexion de solution au fichier solution. Ce fichier est temporaire et la copie locale est supprimée lorsque l’opération « ouvrir à partir du contrôle de code source » est terminée.

- Après l’ajout d’un projet au contrôle de code source, vous pouvez effectuer toutes les actions de contrôle de code source sur celui-ci (extraire, obtenir, etc.).

## <a name="test-cases"></a>Cas de test
 Les éléments suivants sont des cas de test spécifiques pour la zone de test ajouter à/ouvrir à partir du contrôle de code source.

### <a name="case-1a-add-solution-to-source-control"></a>Cas 1a : ajouter la solution au contrôle de code source
 Ce cas de test se concentre sur l’ajout de solutions au contrôle de code source.

|Action|Étapes de test|Résultats attendus à vérifier|
|------------|----------------|--------------------------------|
|Ajouter la solution contenant un projet client au contrôle de code source|1. Créez un projet client.<br />2. Ajoutez la solution au contrôle de code source (**fichier**, **contrôle de code source**, **Ajoutez la solution au contrôle de code source**).|La solution/le projet a été ajouté au contrôle de code source.|
|Ajouter la solution contenant un système de fichiers ou un projet Web IIS local au contrôle de code source|1. Créez un système de fichiers ou un projet Web IIS local (utilisez le bouton Parcourir pour pointer vers l’emplacement du projet. le chemin d’accès détermine le type de projet Web créé).<br />2. Ajoutez la solution au contrôle de code source (**fichier**, **contrôle de code source**, **Ajoutez la solution au contrôle de code source**).|La solution/le projet a été ajouté au contrôle de code source.|
|Ajouter la solution contenant un projet Web de site distant au contrôle de code source|1. Créez un projet Web de site distant.<br />2. Ajoutez la solution au contrôle de code source (**fichier**, **contrôle de code source**, **Ajoutez la solution au contrôle de code source**).<br />3. cliquez sur **OK** dans la boîte de dialogue Avertissement d’accès à FrontPage.|La solution a été ajoutée au contrôle de code source.<br /><br /> Le projet de site distant n’est pas sous contrôle de code source. (Les projets de site distants doivent être contrôlés à partir de leur propre serveur IIS.)|
|Ajoutez une solution de projet unique au contrôle de code source à l’aide de l’option **Ajouter les projets sélectionnés au contrôle de code source**.|1. Créez une solution de projet unique.<br />2. Ajoutez uniquement la solution au contrôle de code source en tant que sélection (**fichier**, **contrôle de code source**, **Ajouter les projets sélectionnés au contrôle de code source**). Si cette étape se déroule correctement, passez à l’étape suivante.<br />3. Ajoutez le projet au contrôle de code source en tant que sélection (**fichier**, **contrôle de code source**, **Ajoutez les projets sélectionnés au contrôle de code source**).<br />4. cliquez sur **Oui** pour ajouter le projet au même emplacement.<br />5. cliquez sur **extraire** dans la boîte de dialogue Extraire **pour modification** .|`Result from Step 2:`<br /><br /> Le projet et tous les fichiers du projet ont un indicateur de contrôle de code source extrait et une info-bulle affiche « pas sous contrôle de code source ».<br /><br /> `Result from Step 5:`<br /><br /> Le fichier projet et la solution se trouvent dans le même dossier dans le contrôle de code source.|
|Annuler l’ajout d’une solution au contrôle de code source|1. Créez une solution de projet unique.<br />2. tentative d’ajout d’un projet et d’une solution au contrôle de code source. Si cette étape se déroule correctement, passez à l’étape suivante.<br />3. annulez l’opération une fois que vous êtes dans le système de contrôle de code source.|`Result from Step 2:`<br /><br /> La boîte de dialogue définir le contrôle de code source d’emplacement du projet n’apparaît qu’une seule fois.<br /><br /> `Result from Step 3:`<br /><br /> L’ajout du projet a été annulé, le projet/la solution n’est pas sous contrôle de code source et tous les menus ajouter aux contrôles de code source sont toujours disponibles.|

### <a name="case-1b-open-solution-from-source-control"></a>Cas 1b. Ouvrir une solution à partir du contrôle de code source
 Ce cas de test se concentre sur l’ouverture de solutions à partir du contrôle de code source.

|Action|Étapes de test|Résultats attendus à vérifier|
|------------|----------------|--------------------------------|
|Ouvrir une solution contenant un projet client à partir du contrôle de code source|1. Créez un projet client.<br />2. Ajoutez la solution au contrôle de code source.<br />3. Fermez la solution.<br />4. Ouvrez la solution à partir du contrôle de code source vers un nouvel emplacement.|Solution/projet ouvert à partir du contrôle de code source.|
|Ouvrir une solution contenant un projet Web local ou IIS à partir du contrôle de code source|1. Créez un projet Web local ou IIS.<br />2. Ajoutez la solution au contrôle de code source.<br />3. Fermez la solution.<br />4. Ouvrez la solution à partir du contrôle de code source vers un nouvel emplacement.|Solution/projet ouvert à partir du contrôle de code source.|
|Ouvrir une solution contenant un projet Web de site distant à partir du contrôle de code source|1. Créez un projet Web de site distant.<br />2. Ajoutez la solution au contrôle de code source. Si cette étape se déroule correctement, passez à l’étape suivante.<br />3. Fermez la solution.<br />4. Ouvrez la solution à partir du contrôle de code source vers un nouvel emplacement.|`Result from Step 2:`<br /><br /> Le site Web distant n’est pas sous contrôle de code source.<br /><br /> `Result from Step 4:`<br /><br /> Solution ouverte à partir du contrôle de code source.<br /><br /> Le projet de site distant est chargé, mais il n’est pas sous contrôle de code source.|

### <a name="case-1c-add-solution-from-source-control"></a>Cas 1C : ajouter la solution à partir du contrôle de code source
 Ce cas de test se concentre sur l’ajout de solutions à partir du contrôle de code source.

|Action|Étapes de test|Résultats attendus à vérifier|
|------------|----------------|--------------------------------|
|Ajouter à la solution vide : une solution de projet unique|1. Créez une solution de projet unique.<br />2. Ajoutez la solution au contrôle de code source.<br />3. Fermez la solution.<br />4. Créez une deuxième solution vide.<br />5. Ajoutez la solution contrôlée précédemment à partir du contrôle de code source (**fichier**, **contrôle de code source**, **Ajouter un projet à partir du contrôle de code source**).|Le projet ajouté s’affiche dans **Explorateur de solutions** et est archivé.|
|Ajouter à la solution avec un projet unique : projet unique|1. Créez une solution avec un seul projet.<br />2. Ajoutez la solution au contrôle de code source.<br />3. Fermez la solution.<br />4. Créez une deuxième solution vide.<br />5. Ajoutez la solution contrôlée précédemment à partir du contrôle de code source (**fichier**, **contrôle de code source**, **Ajouter un projet à partir du contrôle de code source**).|Le projet ajouté s’affiche dans **Explorateur de solutions** et est archivé.|
|Ajouter à la solution : solution ajoutée au contrôle de code source par sélection|1. Créez une solution avec un projet.<br />2. Ajoutez uniquement la solution au contrôle de code source en tant que sélection. Si cette étape se déroule correctement, passez à l’étape suivante.<br />3. Fermez la solution.<br />4. Créez une nouvelle solution.<br />5. Ajoutez la solution contrôlée précédemment à partir du contrôle de code source (**fichier**, **contrôle de code source**, **Ajouter un projet à partir du contrôle de code source**).|`Result from Step 2:`<br /><br /> Le projet n’est pas sous contrôle de code source.<br /><br /> `Result from Step 5:`<br /><br /> Si la première solution contient des éléments de solution, ils ne peuvent pas être ajoutés à partir du contrôle de code source et ne s’affichent donc pas.<br /><br /> Le projet de la première solution apparaît comme étant non disponible.|

## <a name="see-also"></a>Voir aussi
- [Guide de test pour les plug-ins de contrôle de code source](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
