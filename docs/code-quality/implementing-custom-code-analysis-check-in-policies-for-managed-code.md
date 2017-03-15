---
title: "Impl&#233;mentation de strat&#233;gies d&#39;archivage de l&#39;analyse du code personnalis&#233;es pour le code manag&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "12/12/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.code.analysis.selecttfsrulesets"
  - "vs.code.analysis.browsefortfsruleset"
  - "vs.code.analysis.policyeditor"
ms.assetid: fd029003-5671-4b24-8b6f-032e0a98b2e8
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Impl&#233;mentation de strat&#233;gies d&#39;archivage de l&#39;analyse du code personnalis&#233;es pour le code manag&#233;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Une stratégie d'archivage d'analyse du code spécifie un ensemble de règles que les membres d'un projet d'équipe doivent exécuter sur le code source avant qu'il ne soit archivé dans le contrôle de version.  Microsoft fournit un jeu standard d'*ensembles de règles* qui regroupe les règles d'analyse du code dans des zones fonctionnelles.  Les *ensembles de règles de stratégie d'archivage personnalisés* spécifient un ensemble de règles d'analyse du code spécifiques à un projet d'équipe.  Un ensemble de règles est stocké dans un fichier .ruleset.  
  
 Les stratégies d'archivage sont définies au niveau du projet d'équipe et spécifiées par l'emplacement d'un fichier .ruleset dans l'arborescence de contrôle de version.  Il n'existe aucune restriction sur l'emplacement du contrôle de version de l'ensemble de règles personnalisé de la stratégie d'équipe.  
  
 L'analyse du code est configurée individuellement pour chaque projet de code dans la fenêtre de propriétés des projets.  Un ensemble de règles personnalisé pour un projet de code est spécifié par l'emplacement physique du fichier .ruleset sur l'ordinateur local.  Lorsqu'un fichier .ruleset est indiqué qu'il se trouve sur le même lecteur que le projet de code, Visual Studio utilise un chemin d'accès relatif au fichier dans la configuration de projet.  
  
 Une pratique suggérée pour la création d'un ensemble de règles personnalisé de  projet d'équipe consiste à stocker le fichier .ruleset de stratégie d'archivage dans un dossier spécial qui ne fait partie d'aucun projet de code.  Si vous stockez le fichier dans un dossier dédié, vous pouvez appliquer des autorisations qui restreignent les utilisateurs pouvant modifier le fichier de règles, et vous pouvez déplacer facilement la structure de répertoires qui contient le projet vers un autre répertoire ou ordinateur.  
  
## Création de l'ensemble de règles d'archivage personnalisé du projet d'équipe  
 Pour créer un ensemble de règles personnalisé pour un projet d'équipe, vous créez d'abord un dossier spécial pour l'ensemble de règles de stratégie d'archivage dans **Explorateur du contrôle de code source**.  Puis, vous créez le fichier d'ensemble de règles et vous ajoutez le fichier au contrôle de version.  Enfin, vous spécifiez l'ensemble de règles comme stratégie d'archivage d'analyse du code pour le projet d'équipe.  
  
> [!NOTE]
>  Pour créer un dossier dans un projet d'équipe, vous devez d'abord mapper la racine du projet d'équipe à un emplacement sur l'ordinateur local.  Pour plus d'informations, consultez [Create and work with workspaces \(old\)](http://msdn.microsoft.com/fr-fr/db4d5692-179a-44fe-ad31-0c1c900c9cb2).  
  
#### Pour créer le dossier de contrôle de version pour l'ensemble de règles de stratégie d'archivage  
  
1.  Dans [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)], développez le nœud de projet d'équipe, puis cliquez sur **Contrôle de code source**.  
  
2.  Dans le volet **Dossiers**, cliquez avec le bouton droit sur le projet d'équipe, puis cliquez sur **Nouveau dossier**.  
  
3.  Dans le volet principal de Contrôle de code source, cliquez avec le bouton droit sur **Nouveau dossier**, cliquez sur **Renommer** et tapez un nom pour le dossier d'ensemble de règles.  
  
#### Pour créer l'ensemble de règles de stratégie d'archivage  
  
1.  Dans le menu **Fichier**, pointez sur **Nouveau**, puis cliquez sur **Fichier**.  
  
2.  Dans la liste **Catégories**, cliquez sur **Général**.  
  
3.  Dans la liste **Modèles**, double\-cliquez sur **Ensemble de règles d'analyse du code**.  
  
4.  Spécifiez les règles à inclure dans l'ensemble de règles, puis enregistrez le fichier d'ensemble de règles dans le dossier d'ensemble de règles que vous avez créé.  
  
     Pour plus d’informations, consultez [Création d'ensembles de règles personnalisés](../code-quality/creating-custom-code-analysis-rule-sets.md)  
  
#### Pour ajouter le fichier d'ensemble de règles au contrôle de version  
  
1.  Dans **Explorateur du contrôle de code source**, cliquez avec le bouton droit sur le nouveau dossier, puis cliquez sur **Ajouter des éléments au dossier**.  
  
     Pour plus d'informations, consultez [Utiliser un contrôle de version](../Topic/Use%20version%20control.md).  
  
2.  Cliquez sur le fichier d'ensemble de règles que vous avez créé, puis sur **Terminer**.  
  
     Le fichier est ajouté au contrôle de code source et extrait à votre nom.  
  
3.  Dans la fenêtre de détails **Explorateur du contrôle de code source**, cliquez avec le bouton droit sur le nom de fichier, puis cliquez sur **Archiver les modifications en attente**.  
  
4.  Dans la boîte de dialogue **Archiver**, vous pouvez ajouter un commentaire, puis cliquer sur **Archiver**.  
  
    > [!NOTE]
    >  Si vous avez déjà configuré une stratégie d'archivage d'analyse du code pour votre projet d'équipe et si vous avez sélectionné l'option **Appliquer l'archivage uniquement aux fichiers de la solution actuelle**, vous déclencherez un avertissement d'échec de stratégie.  Dans la boîte de dialogue Échec de stratégie, sélectionnez **Substituer l'échec de stratégie et poursuivre l'archivage**.  Ajoutez un commentaire obligatoire, puis cliquez sur **OK**.  
  
#### Pour spécifier le fichier d'ensemble de règles comme stratégie d'archivage  
  
1.  Dans le menu **Équipe**, pointez sur **Paramètres du projet d'équipe**, puis cliquez sur **Contrôle de code source**.  
  
2.  Cliquez sur **Stratégie d'archivage**, puis sur **Ajouter**.  
  
3.  Dans la liste **Stratégie d'archivage**, double\-cliquez sur **Analyse du code**, et vérifiez que la case à cocher **Appliquer l'analyse du code managé** est activée.  
  
4.  Dans la liste **Exécuter cet ensemble de règles** , cliquez sur **\<Sélection d'un ensemble de règles à partir du contrôle de code source...\>**.  
  
5.  Tapez le chemin d'accès du fichier d'ensemble de règles de stratégie d'archivage dans le contrôle de version.  
  
     Le chemin d'accès doit respecter la syntaxe suivante :  
  
     **$\/** `TeamProjectName` **\/** `VersionControlPath`  
  
    > [!NOTE]
    >  Vous pouvez copier le chemin d'accès en utilisant l'une des procédures suivantes dans **Explorateur du contrôle de code source** :  
  
    -   Dans le volet **Dossiers**, cliquez sur le dossier qui contient le fichier d'ensemble de règles.  Copiez le chemin d'accès au contrôle de version du dossier qui s'affiche dans la zone **Source** et tapez manuellement le nom du fichier d'ensemble de règles.  
  
    -   Dans la fenêtre de détails, cliquez avec le bouton droit sur le fichier d'ensemble de règles, puis cliquez sur **Propriétés**.  Sous l'onglet **Général**, copiez la valeur dans **Nom du serveur**.  
  
## Synchronisation des projets de code avec l'ensemble de règles de stratégie d'archivage  
 Vous spécifiez un ensemble de règles de stratégie d'archivage de projet d'équipe comme ensemble de règles d'analyse du code d'une configuration de projet de code dans la boîte de dialogue de propriétés du projet de code.  Si l'ensemble de règles se trouve sur le même lecteur que le projet de code, un chemin d'accès relatif est utilisé pour spécifier l'ensemble de règles lorsque le chemin d'accès est sélectionné à partir de la boîte de dialogue Fichier.  Le chemin d'accès relatif permet aux paramètres de propriétés du projet d'être portables afin d'être utilisés sur d'autres ordinateurs qui utilisent des structures de contrôle de version locales similaires.  
  
#### Pour spécifier un ensemble de règles de projet d'équipe comme ensemble de règles d'un projet de code  
  
1.  Si nécessaire, extrayez le dossier et le fichier d'ensemble de règles de stratégie d'archivage à partir du contrôle de version.  
  
     Vous pouvez exécuter cette étape dans **Explorateur du contrôle de code source** en cliquant avec le bouton droit sur le dossier d'ensemble de règles, puis en cliquant sur **Obtenir la dernière version**.  
  
2.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le projet de code, puis cliquez sur **Propriétés**.  
  
3.  Cliquez sur **Analyse du code**.  
  
4.  Si nécessaire, cliquez sur les options appropriées dans les listes **Configuration** et **Plateforme**.  
  
5.  Pour exécuter une analyse du code chaque fois que le projet de code est généré à l'aide de la configuration spécifiée, activez la case à cocher **Activer l'analyse du code sur la build \(définit la constante CODE\_ANALYSIS\)**.  
  
6.  Pour ignorer le code dans les composants d'autres sociétés, activez la case à cocher **Supprimer les résultats du code généré**.  
  
7.  Dans la liste **Exécuter cet ensemble de règles** , cliquez sur **\<Parcourir...\>**.  
  
8.  Spécifiez la version locale du fichier d'ensemble de règles de stratégie d'archivage.