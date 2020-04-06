---
title: 'Zone d’essai 1 : Ajouter à l’open du contrôle des sources (fr) Microsoft Docs'
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704681"
---
# <a name="test-area-1-add-toopen-from-source-control"></a>Zone d’essai 1 : Ajouter à/ouvrir à partir du contrôle source
Cette zone d’essai plug-in de contrôle des sources couvre le fait de placer des solutions ou des projets sous contrôle source et de les récupérer du contrôle des sources.

## <a name="command-menu-access"></a>Accès au menu de commande
 Les [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] parcours de menu intégrés suivants sont utilisés dans les cas d’essai :

- Pour [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)], ouvert à partir du contrôle source: **Fichier**, **Open**, **Project**/**Solution**; regardez dans [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] l’emplacement.

- Pour d’autres plug-ins de contrôle source, ouvert à partir du contrôle source: **Fichier**, **Contrôle source**, Open from **Source Control**.

- Ajouter au contrôle source: **Fichier**, **Contrôle source**, Ajouter la solution au fichier de contrôle **des sources**, contrôle des **sources**, Ajouter **des projets sélectionnés à la source de contrôle**.

- Menu raccourci (Projet/Solution), **Ajouter la solution au contrôle des sources**.

- Ajouter à partir du contrôle source: **Fichier**, **Contrôle source**, Ajouter le projet de contrôle **source**.

- Pour [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)], ajouter à partir du contrôle source est également disponible à partir de **fichier**, **Ajouter**, **Projet existant;** regardez dans [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] l’emplacement.

  > [!NOTE]
  > Un parcours d’un fichier local ou d’un IIS local (serveur web) peut être utilisé dans ce test.

## <a name="expected-behavior"></a>Comportement attendu

- Pour chaque type de projet pris en charge, un utilisateur doit être en mesure d’ajouter à " et de « ouvrir à partir de » contrôle de source.

- Lorsqu’un projet est ajouté à \<Source Control, un fichier *ProjectName* correspondant>.vspscc (fichier d’indice de projet) est créé. Il contient des informations de liste de fichiers d’exclusion et de connexion. Ne supprimez pas ce fichier car il contient des informations spécifiques au projet.

- Lorsqu’une solution est ajoutée au \<contrôle de la source, un fichier *SolutionName* correspondant>.vssscc (triple S) est créé. Le fichier texte contient des informations de connexion et une liste de fichiers d’exclusion, similaire au fichier d’indice du projet. Ce fichier est temporaire et n’existe que dans la base de données de contrôle source.

- Lorsqu’une solution est ouverte \<à partir du contrôle source, un fichier *SolutionName*>.vsscc (double S) qui n’existe que dans la base de données de contrôle source, est créé localement dans un fichier temporaire. Ce fichier contient le chemin du dossier de connexion de solution au fichier de solution. Ce fichier est temporaire et la copie locale est supprimée lorsque l’opération « Open from Source Control » est terminée.

- Après qu’un projet est ajouté au contrôle source, vous pouvez effectuer toutes les actions de contrôle source sur elle (Vérifiez, Get, et ainsi de suite).

## <a name="test-cases"></a>Cas de test
 Ce qui suit sont des cas de test spécifiques pour la zone d’essai Add To/Open From Source Control.

### <a name="case-1a-add-solution-to-source-control"></a>Cas 1a : Ajouter la solution au contrôle des sources
 Ce cas de test se concentre sur l’ajout de solutions au contrôle des sources.

|Action|Étapes d’essai|Résultats attendus pour vérifier|
|------------|----------------|--------------------------------|
|Ajouter une solution contenant un projet client pour le contrôle de source|1. Créer un projet client.<br />2. Ajouter la solution au contrôle de source (**Fichier**, **Contrôle source**, Ajouter la solution au contrôle **des sources**).|Solution/Projet a été ajouté au contrôle des sources.|
|Ajouter une solution contenant un système de fichiers ou un projet Web local de l’IIS pour le contrôle des sources|1. Créer un système de fichiers ou un projet Web local de l’IIS (utiliser le bouton Parcourir pour indiquer l’emplacement du projet; le chemin détermine le type de projet Web créé).<br />2. Ajouter la solution au contrôle de source (**Fichier**, **Contrôle source**, Ajouter la solution au contrôle **des sources**).|Solution/Projet a été ajouté au contrôle des sources.|
|Ajouter une solution contenant un projet Web de site à distance pour le contrôle des sources|1. Créer un projet Web de site à distance.<br />2. Ajouter la solution au contrôle de source (**Fichier**, **Contrôle source**, Ajouter la solution au contrôle **des sources**).<br />3. Cliquez **SUR OK** dans la boîte de dialogue d’avertissement d’accès FrontPage.|La solution a été ajoutée au contrôle des sources.<br /><br /> Le projet Remote Site n’est PAS sous contrôle source. (Les projets de sites à distance doivent être contrôlés à partir de leur propre serveur IIS.)|
|Ajoutez une solution de projet unique au contrôle de source à l’aide **d’Add Selected Projects to Source Control**.|1. Créer une solution de projet unique.<br />2. Ajouter uniquement la solution au contrôle de source en tant que sélection (**Fichier**, **Contrôle source**, Ajouter **des projets sélectionnés au contrôle des sources**). Si cette étape réussit, continuez à passer à l’étape suivante.<br />3. Ajouter le projet au contrôle source en tant que sélection (**Fichier**, **Contrôle source**, Ajouter **des projets sélectionnés au contrôle des sources**).<br />4. Cliquez **oui** pour ajouter le projet au même endroit.<br />5. Cliquez sur **Check Out** in Check Out **For Edit** boîte de dialogue.|`Result from Step 2:`<br /><br /> Le projet et tous les fichiers du projet ont un indicateur de contrôle des sources vérifié, et un ToolTip affiche "Pas sous contrôle source".<br /><br /> `Result from Step 5:`<br /><br /> Le fichier de projet et de solution est dans le même dossier dans le contrôle source.|
|Annuler l’ajout d’une solution au contrôle des sources|1. Créer une solution de projet unique.<br />2. Essayez d’ajouter le projet et la solution au contrôle des sources. Si cette étape réussit, continuez à passer à l’étape suivante.<br />3. Annuler après que vous êtes dans le système de contrôle source.|`Result from Step 2:`<br /><br /> La boîte de dialogue de contrôle de la source de localisation du projet Set n’apparaît qu’une seule fois.<br /><br /> `Result from Step 3:`<br /><br /> L’ajout de projet annulé, le projet/solution n’est PAS sous contrôle source et tous les menus de contrôle d’add to source toujours disponibles.|

### <a name="case-1b-open-solution-from-source-control"></a>Affaire 1b. Solution ouverte à partir du contrôle des sources
 Ce cas de test se concentre sur l’ouverture de solutions à partir du contrôle source.

|Action|Étapes d’essai|Résultats attendus pour vérifier|
|------------|----------------|--------------------------------|
|Ouvrez une solution contenant un projet client à partir du contrôle source|1. Créer un projet client.<br />2. Ajouter la solution au contrôle des sources.<br />3. Fermez la solution.<br />4. Ouvrez la solution du contrôle source à un nouvel emplacement.|Solution/Projet ouvert à partir du contrôle source.|
|Ouvrez une solution contenant un projet Web local ou IIS à partir du contrôle des sources|1. Créer un projet Web local ou IIS.<br />2. Ajouter la solution au contrôle des sources.<br />3. Fermez la solution.<br />4. Ouvrez la solution du contrôle source à un nouvel emplacement.|Solution/Projet ouvert à partir du contrôle source.|
|Ouvrez une solution contenant un projet Web de site à distance à partir du contrôle source|1. Créer un projet Web de site à distance.<br />2. Ajouter la solution au contrôle des sources. Si cette étape réussit, continuez à passer à l’étape suivante.<br />3. Fermez la solution.<br />4. Ouvrez la solution du contrôle source à un nouvel emplacement.|`Result from Step 2:`<br /><br /> Remote Site Web n’est PAS sous contrôle source.<br /><br /> `Result from Step 4:`<br /><br /> Solution ouverte à partir du contrôle source.<br /><br /> Le projet De site à distance est chargé, mais il n’est pas sous contrôle source.|

### <a name="case-1c-add-solution-from-source-control"></a>Cas 1c : Ajouter la solution à partir du contrôle des sources
 Ce cas de test se concentre sur l’ajout de solutions à partir du contrôle des sources.

|Action|Étapes d’essai|Résultats attendus pour vérifier|
|------------|----------------|--------------------------------|
|Ajouter à la solution Vide — une solution de projet unique|1. Créer une solution de projet unique.<br />2. Ajouter la solution au contrôle des sources.<br />3. Fermez la solution.<br />4. Créer une deuxième solution vide.<br />5. Ajouter la solution précédemment contrôlée à partir du contrôle source (**Fichier**, **Contrôle source**, Ajouter le projet de contrôle **source**).|Le projet ajouté apparaît dans **Solution Explorer** et est enregistré.|
|Ajouter à la solution avec un seul projet — un projet unique|1. Créer une solution avec un seul projet.<br />2. Ajouter la solution au contrôle des sources.<br />3. Fermez la solution.<br />4. Créer une deuxième solution vide.<br />5. Ajouter la solution précédemment contrôlée à partir du contrôle source (**Fichier**, **Contrôle source**, Ajouter le projet de contrôle **source**).|Le projet ajouté apparaît dans **Solution Explorer** et est enregistré.|
|Ajouter à la solution — solution ajoutée au contrôle source par sélection|1. Créer une solution avec un projet.<br />2. Ajouter la seule solution au contrôle de source comme sélection. Si cette étape réussit, continuez à passer à l’étape suivante.<br />3. Fermez la solution.<br />4. Créer une nouvelle solution.<br />5. Ajouter la solution précédemment contrôlée à partir du contrôle source (**Fichier**, **Contrôle source**, Ajouter le projet de contrôle **source**).|`Result from Step 2:`<br /><br /> Le projet n’est pas sous contrôle source.<br /><br /> `Result from Step 5:`<br /><br /> Si la première solution avait des éléments de solution, ils ne peuvent pas être ajoutés à partir du contrôle source, de sorte qu’ils n’apparaissent pas.<br /><br /> Le projet de première solution apparaît comme indisponible.|

## <a name="see-also"></a>Voir aussi
- [Guide de test pour les plug-ins de contrôle de code source](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
