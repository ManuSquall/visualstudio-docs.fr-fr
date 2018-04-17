---
title: 'Zone de test 1 : Ajouter à ouvrir à partir du contrôle de code Source | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], adding and opening solutions
- source control plug-ins, adding and opening solutions
ms.assetid: 5b3b5b08-5e9b-41be-ac72-c63957faed22
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6e95ef13a3d8f7a61c53c9938564479adf362a2c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="test-area-1-add-toopen-from-source-control"></a>Zone de test 1 : Ajouter / ouvrir à partir du contrôle de code Source
Ce contrôle de code source du plug-in de test couvre zone placement des solutions ou projets sous contrôle de code source et de les récupérer à partir du contrôle de code source.  
  
## <a name="command-menu-access"></a>Accès au Menu de commande  
 Les éléments suivants [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] menu chemins d’environnement de développement intégré sont utilisés dans les cas de test :  
  
-   Pour [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)], ouvrir à partir du contrôle de code source : **fichier**, **ouvrir**, **projet**/**Solution**; recherchez dans le [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] emplacement.  
  
-   Pour les autres sources plug-ins de contrôle, ouvrez à partir du contrôle de code source : **fichier**, **contrôle de code Source**, **ouvrir à partir du contrôle de code Source**.  
  
-   Ajouter au contrôle de code source : **fichier**, **contrôle de code Source**, **ajouter la Solution au fichier de contrôle de code Source**, **contrôle de code Source**, **ajouter Projets au contrôle de code Source sélectionnés**.  
  
-   Le Menu contextuel (projet/Solution), **ajouter la Solution au contrôle de code Source**.  
  
-   Ajouter à partir du contrôle de code source : **fichier**, **contrôle de code Source**, **ajouter un projet à partir du contrôle de code Source**.  
  
-   Pour [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)], ajouter à partir de la source de contrôle est également disponible à partir de **fichier**, **ajouter**, **projet existant**; recherchez dans le [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] emplacement.  
  
    > [!NOTE]
    >  Un chemin d’accès d’un fichier local ou d’un serveur IIS local (serveur web) peut être utilisé dans ce test.  
  
## <a name="expected-behavior"></a>Comportement attendu  
  
-   Pour chaque type de projet pris en charge, un utilisateur doit être en mesure de « Ajouter à » et « Ouvrir à partir de « contrôle de code Source.  
  
-   Lorsqu’un projet est ajouté au contrôle de code Source, correspondante \< *nom_projet*> .vspscc (projet indicateur fichier) sont créé. Il contient des informations de connexion et de la liste de fichier d’exclusion. Ne supprimez pas ce fichier, car il contient des informations spécifiques au projet.  
  
-   Lorsqu’une solution est ajoutée au contrôle de code source, correspondante \< *SolutionName*> .vssscc (triple S) fichier est créé. Le fichier texte contient des informations de connexion et une liste de fichiers d’exclusion, semblable au fichier projet indicateur. Ce fichier est temporaire et existe uniquement dans la base de données de contrôle de code source.  
  
-   Lorsqu’une solution est ouverte à partir du contrôle de code source, un \< *SolutionName*> .vsscc (double S) fichier qui existe uniquement dans la base de données de contrôle de code source, est créé localement dans un fichier temporaire. Ce fichier contient le chemin d’accès à partir du dossier de connexion de solution pour le fichier solution. Ce fichier est temporaire et la copie locale est supprimée lorsque l’opération « Ouvrir à partir de contrôle de code Source » est terminée.  
  
-   Une fois un projet est ajouté au contrôle de source, vous pouvez effectuer toutes les actions de contrôle de code source sur celui-ci (extraction, Get et ainsi de suite).  
  
## <a name="test-cases"></a>Cas de test  
 Voici les cas de test spécifiques pour l’ajouter à / Open à partir de la zone de test de contrôle de code Source.  
  
### <a name="case-1a-add-solution-to-source-control"></a>Cas 1 : ajouter la Solution au contrôle de code Source  
 Ce cas de test se concentre sur l’ajout de solutions au contrôle de code source.  
  
|Action|Étapes de test|Résultats attendus à vérifier|  
|------------|----------------|--------------------------------|  
|Ajouter une solution contenant un projet de client de contrôle de code source|1.  Créez un projet de client.<br />2.  Ajouter la solution au contrôle de code source (**fichier**, **contrôle de code Source**, **ajouter la Solution au contrôle de code Source**).|Solution/projet a été ajouté au contrôle de code source.|  
|Ajouter une solution contenant un système de fichiers ou d’un projet Web IIS local au contrôle de code source|1.  Créez un système de fichiers ou d’un projet Web IIS local (utilisez le bouton Parcourir pour pointer vers l’emplacement du projet ; le chemin d’accès détermine le type de projet Web est créé).<br />2.  Ajouter la solution au contrôle de code source (**fichier**, **contrôle de code Source**, **ajouter la Solution au contrôle de code Source**).|Solution/projet a été ajouté au contrôle de code source.|  
|Ajouter une solution contenant un projet Web à distance de Site pour le contrôle de code source|1.  Créez un projet Web Site distant.<br />2.  Ajouter la solution au contrôle de code source (**fichier**, **contrôle de code Source**, **ajouter la Solution au contrôle de code Source**).<br />3.  Cliquez sur **OK** dans la boîte de dialogue d’avertissement accès FrontPage.|Solution a été ajoutée au contrôle de code source.<br /><br /> Projet de Site distant n’est pas sous contrôle de code source. (Les projets de Site distant doivent être contrôlés à partir de leur propre serveur IIS.)|  
|Ajouter une solution de projet unique au contrôle de code source à l’aide **ajouter les projets sélectionnés au contrôle de code Source**.|1.  Créer une solution de projet unique.<br />2.  Ajoutez uniquement des solutions au contrôle de code source en tant que sélection (**fichier**, **contrôle de code Source**, **ajouter les projets sélectionnés au contrôle de code Source**). Si cette étape est exécutée correctement, passez à l’étape suivante.<br />3.  Ajouter un projet au contrôle de code source en tant que sélection (**fichier**, **contrôle de code Source**, **ajouter les projets sélectionnés au contrôle de code Source**).<br />4.  Cliquez sur **Oui** pour ajouter le projet au même emplacement.<br />5.  Cliquez sur **Check Out** dans **extraire pour modification** boîte de dialogue.|`Result from Step 2:`<br /><br /> Le projet et tous les fichiers dans le projet d’un des indicateurs de contrôle de code source et une info-bulle affiche « pas sous contrôle de code source ».<br /><br /> `Result from Step 5:`<br /><br /> Fichiers projet et solution sont dans le même dossier de contrôle de code source.|  
|Annuler l’ajout d’une solution au contrôle de code source|1.  Créer une solution de projet unique.<br />2.  Tentative d’ajout de projet et une solution au contrôle de code source. Si cette étape est exécutée correctement, passez à l’étape suivante.<br />3.  Annuler une fois que vous êtes dans le système de contrôle de code source.|`Result from Step 2:`<br /><br /> La boîte de dialogue ensemble projet emplacement source s’affiche qu’une seule fois.<br /><br /> `Result from Step 3:`<br /><br /> Projet Ajouter annulé, projet ou la solution n’est pas sous contrôle de code source et tous les ajouter aux menus du contrôle source toujours disponibles.|  
  
### <a name="case-1b-open-solution-from-source-control"></a>1 b de cas. Ouvrir une Solution à partir du contrôle de code Source  
 Ce cas de test se concentre sur l’ouverture de solutions à partir du contrôle de code source.  
  
|Action|Étapes de test|Résultats attendus à vérifier|  
|------------|----------------|--------------------------------|  
|Ouvrez une solution contenant un projet de client à partir du contrôle de code source|1.  Créez un projet de client.<br />2.  Ajouter la solution au contrôle de code source.<br />3.  Fermez la solution.<br />4.  Ouvrez la solution à partir du contrôle de code source vers un nouvel emplacement.|Solution/projet ouvert à partir du contrôle de code source.|  
|Ouvrez une solution contenant un local ou un projet Web IIS à partir du contrôle de code source|1.  Créez un local ou un projet Web IIS.<br />2.  Ajouter la solution au contrôle de code source.<br />3.  Fermez la solution.<br />4.  Ouvrez la solution à partir du contrôle de code source vers un nouvel emplacement.|Solution/projet ouvert à partir du contrôle de code source.|  
|Ouvrez une solution contenant un projet Web à distance de Site à partir du contrôle de code source|1.  Créez un projet Web Site distant.<br />2.  Ajouter la solution au contrôle de code source. Si cette étape est exécutée correctement, passez à l’étape suivante.<br />3.  Fermez la solution.<br />4.  Ouvrez la solution à partir du contrôle de code source vers un nouvel emplacement.|`Result from Step 2:`<br /><br /> Web Site distant n’est pas sous contrôle de code source.<br /><br /> `Result from Step 4:`<br /><br /> Solution ouverte à partir du contrôle de code source.<br /><br /> Projet de Site distant est chargé, mais il n’est pas sous contrôle de code source.|  
  
### <a name="case-1c-add-solution-from-source-control"></a>Cas 1c : ajouter la Solution à partir du contrôle de code Source  
 Ce cas de test se concentre sur l’ajout de solutions à partir du contrôle de code source.  
  
|Action|Étapes de test|Résultats attendus à vérifier|  
|------------|----------------|--------------------------------|  
|Ajouter à une solution vide, une solution de projet unique|1.  Créer une solution de projet unique.<br />2.  Ajouter la solution au contrôle de code source.<br />3.  Fermez la solution.<br />4.  Créez une deuxième solution vide.<br />5.  Ajouter la solution précédemment contrôlée à partir du contrôle de code source (**fichier**, **contrôle de code Source**, **ajouter un projet à partir du contrôle de code Source**).|Le projet ajouté apparaît dans **l’Explorateur de solutions** et est archivé.|  
|Ajouter à la solution avec un seul projet, seul projet|1.  Créer une solution avec un seul projet.<br />2.  Ajouter la solution au contrôle de code source.<br />3.  Fermez la solution.<br />4.  Créez une deuxième solution vide.<br />5.  Ajouter la solution précédemment contrôlée à partir du contrôle de code source (**fichier**, **contrôle de code Source**, **ajouter un projet à partir du contrôle de code Source**).|Le projet ajouté apparaît dans **l’Explorateur de solutions** et est archivé.|  
|Ajouter à la solution, solution ajoutée au contrôle de code source par sélection|1.  Créez une solution avec un projet.<br />2.  Ajoutez uniquement des solutions au contrôle de code source en tant que sélection. Si cette étape est exécutée correctement, passez à l’étape suivante.<br />3.  Fermez la solution.<br />4.  Créer une nouvelle solution.<br />5.  Ajouter la solution précédemment contrôlée à partir du contrôle de code source (**fichier**, **contrôle de code Source**, **ajouter un projet à partir du contrôle de code Source**).|`Result from Step 2:`<br /><br /> Projet n’est pas sous contrôle de code source.<br /><br /> `Result from Step 5:`<br /><br /> Si la première solution avait des éléments de solution, ils ne peuvent pas être ajoutés à partir du contrôle de code source, afin qu’ils n’apparaissent pas.<br /><br /> Projet à partir de la première solution apparaît comme étant non disponible.|  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de test pour les plug-ins de contrôle de code source](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)