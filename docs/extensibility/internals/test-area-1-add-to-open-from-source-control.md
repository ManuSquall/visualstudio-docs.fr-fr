---
title: "Zone de test 1&#160;: Ajouter &#224; ouvrir &#224; partir du contr&#244;le de code Source | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "contrôle de code source (Visual Studio SDK), ajouter et ouvrir des solutions"
  - "contrôle plug-ins de source, ajout et ouvrir des solutions"
ms.assetid: 5b3b5b08-5e9b-41be-ac72-c63957faed22
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# Zone de test 1&#160;: Ajouter / ouvrir &#224; partir du contr&#244;le de code Source
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ce contrôle de code source du plug\-in de test couvre zone placer les solutions ou projets sous contrôle de code source et de les récupérer à partir du contrôle de code source.  
  
## Accès au Menu de commande  
 Les éléments suivants [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] menu chemins d’environnement de développement intégré sont utilisés dans les cas de test :  
  
-   Pour [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)], ouvrir à partir du contrôle de code source : **fichier**, **Ouvrir**, **projet**\/**Solution**; recherchez dans le [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] emplacement.  
  
-   Pour les autres contrôle plug\-ins de source, ouvrez à partir du contrôle de code source : **fichier**, **contrôle de code Source**, **Ouvrir à partir du contrôle de code Source**.  
  
-   Ajouter au contrôle de code source : **fichier**, **contrôle de code Source**, **Ajouter la Solution au fichier de contrôle de code Source**, **contrôle de code Source**, **Ajouter les projets sélectionnés au contrôle de code Source**.  
  
-   Menu contextuel \(projet\/Solution\), **Ajouter la Solution au contrôle de code Source**.  
  
-   Ajouter à partir du contrôle de code source : **fichier**, **contrôle de code Source**, **Ajouter un projet à partir du contrôle de code Source**.  
  
-   Pour [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)], ajouter à partir de la source de contrôle est également disponible à partir de **fichier**, **Ajouter**, **projet existant**; recherchez dans le [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] emplacement.  
  
    > [!NOTE]
    >  Un chemin d’accès d’un fichier local ou un serveur IIS local \(serveur web\) peut être utilisé dans ce test.  
  
## Comportement attendu  
  
-   Pour chaque type de projet pris en charge, un utilisateur doit être en mesure de « Ajouter » et « Ouvrir à partir de « contrôle de code Source.  
  
-   Lorsqu’un projet est ajouté au contrôle de code Source, un correspondant \<*nom\_projet*\> .vspscc \(projet indicateur fichier\) est créé. Il contient des informations de connexion et de la liste de fichier d’exclusion. Ne supprimez pas ce fichier, car il contient des informations spécifiques au projet.  
  
-   Lorsqu’une solution est ajoutée au contrôle de code source, un correspondant \<*SolutionName*\> .vssscc \(triple S\) fichier est créé. Le fichier texte contient des informations de connexion et une liste de fichiers d’exclusion, semblable au fichier projet indicateur. Ce fichier est temporaire et existe uniquement dans la base de données de contrôle de code source.  
  
-   Lorsqu’une solution est ouverte à partir du contrôle de code source, un \<*SolutionName*\> fichier .vsscc \(double S\) qui existe uniquement dans la base de données de contrôle de code source est créée localement dans un fichier temporaire. Ce fichier contient le chemin d’accès du dossier de connexion de solution pour le fichier de solution. Ce fichier est temporaire et la copie locale est supprimée lors de l’opération « Ouvrir à partir du contrôle Source ».  
  
-   Après avoir ajouté un projet au contrôle de source, vous pouvez effectuer toutes les actions de contrôle de code source sur celui\-ci \(extraction, Get et ainsi de suite\).  
  
## Cas de test  
 Voici les cas de test spécifiques pour l’ajouter \/ ouvrir à partir de la zone de test de contrôle de code Source.  
  
### Cas 1 : ajouter la Solution au contrôle de code Source  
 Ce cas de test se concentre sur l’ajout de solutions au contrôle de code source.  
  
|Action|Étapes de test|Résultats attendus à vérifier|  
|------------|--------------------|-----------------------------------|  
|Ajouter une solution contenant un projet de client de contrôle de code source|1.  Créer un projet client.<br />2.  Ajouter la solution au contrôle de code source \(**fichier**, **contrôle de code Source**, **Ajouter la Solution au contrôle de code Source**\).|Projet\/solution a été ajouté au contrôle de code source.|  
|Ajouter une solution contenant un système de fichiers ou un projet Web IIS local au contrôle de code source|1.  Créez un projet Web IIS local ou un système de fichiers \(utilisez le bouton Parcourir pour pointer vers l’emplacement du projet, le chemin d’accès détermine le type de projet Web est créé\).<br />2.  Ajouter la solution au contrôle de code source \(**fichier**, **contrôle de code Source**, **Ajouter la Solution au contrôle de code Source**\).|Projet\/solution a été ajouté au contrôle de code source.|  
|Ajouter une solution contenant un projet Web Site distant pour le contrôle de code source|1.  Créez un projet Web de Site distant.<br />2.  Ajouter la solution au contrôle de code source \(**fichier**, **contrôle de code Source**, **Ajouter la Solution au contrôle de code Source**\).<br />3.  Cliquez sur **OK** dans la boîte de dialogue d’avertissement accès FrontPage.|Solution a été ajoutée au contrôle de code source.<br /><br /> Projet de Site distant n’est pas sous contrôle de code source. \(Les projets de Site distant doivent être contrôlés à partir de son propre serveur IIS.\)|  
|Ajouter une solution de projet au contrôle de code source à l’aide **Ajouter les projets sélectionnés au contrôle de code Source**.|1.  Créer une solution de projet unique.<br />2.  Ajouter uniquement solution au contrôle de code source comme une sélection \(**fichier**, **contrôle de code Source**, **Ajouter les projets sélectionnés au contrôle de code Source**\). Si cette étape réussit, passez à l’étape suivante.<br />3.  Ajout d’un projet au contrôle de code source en tant que sélection \(**fichier**, **contrôle de code Source**, **Ajouter les projets sélectionnés au contrôle de code Source**\).<br />4.  Cliquez sur **Oui** pour ajouter le projet au même emplacement.<br />5.  Cliquez sur **Check Out** dans **Extraire pour modification** boîte de dialogue.|`Result from Step 2:`<br /><br /> Le projet et tous les fichiers du projet ont un des indicateurs de contrôle de code source, et une info\-bulle affiche « pas sous contrôle de code source ».<br /><br /> `Result from Step 5:`<br /><br /> Fichiers projet et solution sont dans le même dossier de contrôle de code source.|  
|Annuler l’ajout d’une solution au contrôle de code source|1.  Créer une solution de projet unique.<br />2.  Tentative d’ajout de projet et solution au contrôle de code source. Si cette étape réussit, passez à l’étape suivante.<br />3.  Annuler une fois que vous vous trouvez dans le système de contrôle de code source.|`Result from Step 2:`<br /><br /> La boîte de dialogue ensemble projet emplacement source apparaît une seule fois.<br /><br /> `Result from Step 3:`<br /><br /> Projet Ajout annulé, projet\/solution n’est pas sous contrôle de code source et tous les ajouter aux menus du contrôle source reste disponibles.|  
  
### 1 b cas. Ouvrir une Solution à partir du contrôle de code Source  
 Ce cas de test se concentre sur l’ouverture de solutions à partir du contrôle de code source.  
  
|Action|Étapes de test|Résultats attendus à vérifier|  
|------------|--------------------|-----------------------------------|  
|Ouvrir une solution contenant un projet de client de contrôle de code source|1.  Créer un projet client.<br />2.  Ajouter la solution au contrôle de code source.<br />3.  Fermez la solution.<br />4.  Ouvrez la solution de contrôle de code source vers un nouvel emplacement.|Solution de projet ouvert à partir du contrôle de code source.|  
|Ouvrir une solution contenant un local ou un projet Web IIS à partir du contrôle de code source|1.  Créez un local ou un projet Web IIS.<br />2.  Ajouter la solution au contrôle de code source.<br />3.  Fermez la solution.<br />4.  Ouvrez la solution de contrôle de code source vers un nouvel emplacement.|Solution de projet ouvert à partir du contrôle de code source.|  
|Ouvrir une solution contenant un projet Web de Site à distance à partir du contrôle de code source|1.  Créez un projet Web de Site distant.<br />2.  Ajouter la solution au contrôle de code source. Si cette étape réussit, passez à l’étape suivante.<br />3.  Fermez la solution.<br />4.  Ouvrez la solution de contrôle de code source vers un nouvel emplacement.|`Result from Step 2:`<br /><br /> Web Site distant n’est pas sous contrôle de code source.<br /><br /> `Result from Step 4:`<br /><br /> Solution ouverte à partir du contrôle de code source.<br /><br /> Projet de Site distant est chargé, mais il n’est pas sous contrôle de code source.|  
  
### Cas 1c : ajouter la Solution à partir du contrôle de code Source  
 Ce cas de test se concentre sur l’ajout de solutions à partir du contrôle de code source.  
  
|Action|Étapes de test|Résultats attendus à vérifier|  
|------------|--------------------|-----------------------------------|  
|Ajouter à une solution vide, une solution de projet unique|1.  Créer une solution de projet unique.<br />2.  Ajouter la solution au contrôle de code source.<br />3.  Fermez la solution.<br />4.  Créez une deuxième solution vide.<br />5.  Ajouter la solution précédemment contrôlée à partir du contrôle de code source \(**fichier**, **contrôle de code Source**, **Ajouter un projet à partir du contrôle de code Source**\).|Le projet ajouté apparaît dans **l’Explorateur de solutions** et est archivé.|  
|Ajouter à la solution avec un seul projet, projet unique|1.  Créer une solution avec un seul projet.<br />2.  Ajouter la solution au contrôle de code source.<br />3.  Fermez la solution.<br />4.  Créez une deuxième solution vide.<br />5.  Ajouter la solution précédemment contrôlée à partir du contrôle de code source \(**fichier**, **contrôle de code Source**, **Ajouter un projet à partir du contrôle de code Source**\).|Le projet ajouté apparaît dans **l’Explorateur de solutions** et est archivé.|  
|Ajouter à la solution, ajoutée au contrôle de code source par sélection de solution|1.  Créer une solution avec un projet.<br />2.  Ajoutez uniquement des solutions au contrôle de code source en tant que sélection. Si cette étape réussit, passez à l’étape suivante.<br />3.  Fermez la solution.<br />4.  Créer une nouvelle solution.<br />5.  Ajouter la solution précédemment contrôlée à partir du contrôle de code source \(**fichier**, **contrôle de code Source**, **Ajouter un projet à partir du contrôle de code Source**\).|`Result from Step 2:`<br /><br /> Projet n’est pas sous contrôle de code source.<br /><br /> `Result from Step 5:`<br /><br /> Si la première solution avait des éléments de solution, ils ne peuvent pas être ajoutés à partir du contrôle de code source, afin qu’ils n’apparaissent pas.<br /><br /> Projet à partir de la première solution apparaît comme étant indisponible.|  
  
## Voir aussi  
 [Guide d'évaluation pour les Plug\-ins de contrôle de code Source](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)