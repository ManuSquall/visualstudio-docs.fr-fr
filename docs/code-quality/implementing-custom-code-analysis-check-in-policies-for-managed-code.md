---
title: "Implémentation de Code personnalisé Analysis stratégies d’archivage pour le Code managé | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.code.analysis.selecttfsrulesets
- vs.code.analysis.browsefortfsruleset
- vs.code.analysis.policyeditor
ms.assetid: fd029003-5671-4b24-8b6f-032e0a98b2e8
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5c2853d06bf7dcf2ffd894ee3ae1a90e78e61c6d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="implementing-custom-code-analysis-check-in-policies-for-managed-code"></a>Implémentation de stratégies d'archivage de l'analyse du code personnalisées pour le code managé
Une stratégie d’archivage spécifie un ensemble de règles que les membres d’un projet d’équipe doivent exécuter sur le code source avant l’analyse du code est archivée au contrôle de version. Microsoft fournit un ensemble de la norme *ensembles de règles* cette analyse de code de groupe de règles dans des zones fonctionnelles. *Les ensembles de règles de stratégie d’archivage personnalisée* spécifier un ensemble de règles d’analyse du code qui sont spécifiques à un projet d’équipe. Un ensemble de règles est stocké dans un fichier .ruleset.  
  
 Stratégies d’archivage sont définies au niveau du projet d’équipe et spécifiés par l’emplacement d’un fichier .ruleset dans l’arborescence de contrôle de version. Il n’existe aucune restriction sur l’emplacement du contrôle de version de l’ensemble de règles personnalisé stratégie équipe.  
  
 Analyse du code est configurée pour les projets de code individuels dans la fenêtre Propriétés pour chaque projet. Une règle personnalisée définie pour un projet de code spécifiée par l’emplacement physique du fichier .ruleset sur l’ordinateur local. Lorsqu’un fichier .ruleset est spécifié qui se trouve sur le même lecteur que le projet de code, Visual Studio utilise un chemin d’accès relatif au fichier dans la configuration du projet.  
  
 Il est conseillé pour la création d’un ensemble de règles personnalisé de projet équipe pour stocker le fichier .ruleset de stratégie d’archivage dans un dossier spécial qui ne fait pas partie d’un projet de code. Si vous stockez le fichier dans un dossier dédié, vous pouvez appliquer des autorisations qui limitent ce qui peuvent modifier le fichier de règles, vous pouvez déplacer facilement la structure de répertoire qui contient le projet vers un autre répertoire ou ordinateur.  
  
## <a name="creating-the-team-project-custom-check-in-rule-set"></a>Création de l’ensemble des règles d’archivage personnalisées projet d’équipe  
 Pour créer une règle personnalisée définie pour un projet d’équipe, vous créez tout d’abord un dossier spécial pour la règle de stratégie d’archivage **Explorateur du contrôle de code Source**. Ensuite, vous créez le fichier d’ensemble de règles et ajoutez le fichier au contrôle de version. Enfin, vous spécifiez la règle définie en tant que la stratégie de vérification d’analyse du code pour le projet d’équipe.  
  
> [!NOTE]
>  Pour créer un dossier dans un projet d’équipe, vous devez d’abord mapper la racine du projet d’équipe vers un emplacement sur l’ordinateur local. Pour plus d’informations, consultez [créer et utiliser des espaces de travail (ancien)](http://msdn.microsoft.com/en-us/db4d5692-179a-44fe-ad31-0c1c900c9cb2).  
  
#### <a name="to-create-the-version-control-folder-for-the-check-in-policy-rule-set"></a>Pour créer le dossier de contrôle de version pour l’ensemble de règles de stratégie d’archivage  
  
1.  Dans [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)], développez le nœud de projet d’équipe, puis cliquez sur **contrôle de code Source**.  
  
2.  Dans le **dossiers** volet, cliquez sur le projet d’équipe, puis **nouveau dossier**.  
  
3.  Dans le volet principal de contrôle de code Source, cliquez sur **nouveau dossier**, cliquez sur **renommer**et tapez un nom pour la règle de définie le dossier.  
  
#### <a name="to-create-the-check-in-policy-rule-set"></a>Pour créer l’ensemble de règles de stratégie d’archivage  
  
1.  Sur le **fichier** menu, pointez sur **nouveau**, puis cliquez sur **fichier**.  
  
2.  Dans le **catégories** , cliquez sur **général**.  
  
3.  Dans le **modèles** , double-cliquez sur **ensemble de règles d’analyse de Code**.  
  
4.  Spécifiez les règles à inclure dans l’ensemble de règles, puis enregistrez le fichier d’ensemble de règles dans le dossier d’ensemble de règles que vous avez créé.  
  
     Pour plus d’informations, consultez [création d’ensembles de règles personnalisés](../code-quality/creating-custom-code-analysis-rule-sets.md)  
  
#### <a name="to-add-the-rule-set-file-to-version-control"></a>Pour ajouter la règle de définie le fichier au contrôle de version  
  
1.  Dans **Explorateur du contrôle de code Source**, cliquez sur le nouveau dossier, puis cliquez sur **ajouter des éléments au dossier**.  
  
     Pour plus d’informations, consultez [utiliser le contrôle de version](http://msdn.microsoft.com/Library/33267cee-fe5f-4aa3-b2cd-6d22ceace314).  
  
2.  Cliquez sur la règle de fichier que vous avez créé, puis cliquez sur **Terminer**.  
  
     Le fichier est ajouté au contrôle de code source et extrait pour vous.  
  
3.  Dans le **Explorateur du contrôle de code Source** fenêtre de détails, cliquez sur le nom de fichier, puis **archiver des modifications en attente**.  
  
4.  Dans le **archivage** boîte de dialogue, vous pouvez ajouter un commentaire, puis cliquez sur **archiver**.  
  
    > [!NOTE]
    >  Si vous avez déjà configuré une stratégie d’archivage de l’analyse du code pour votre projet d’équipe et vous avez sélectionné le **appliquer l’archivage pour qu’il contienne uniquement les fichiers qui font partie de la solution actuelle**, vous déclenchera un avertissement d’échec de stratégie. Dans la boîte de dialogue d’échec de la stratégie, sélectionnez **substituer l’échec de stratégie et poursuivre l’archivage**. Ajouter un commentaire requis, puis cliquez sur **OK**.  
  
#### <a name="to-specify-the-rule-set-file-as-the-check-in-policy"></a>Pour spécifier la règle de fichier d’ensemble de la stratégie d’archivage  
  
1.  Sur le **équipe** menu, pointez sur **paramètres du projet d’équipe**, puis cliquez sur **contrôle de code Source**.  
  
2.  Cliquez sur **stratégie d’archivage**, puis cliquez sur **ajouter**.  
  
3.  Dans le **stratégie d’archivage** , double-cliquez sur **l’analyse du Code**et vous assurer que le **appliquer l’analyse du Code pour le Code managé** case à cocher est activée.  
  
4.  Dans le **exécuter cet ensemble de règles** , cliquez sur  **\<sélectionner l’ensemble de règles de contrôle de code Source >**.  
  
5.  Tapez le chemin d’accès du fichier de jeu de règle de stratégie d’archivage dans le contrôle de version.  
  
     Le chemin d’accès doit être conforme à la syntaxe suivante :  
  
     **$/** `TeamProjectName` **/** `VersionControlPath`  
  
    > [!NOTE]
    >  Vous pouvez copier le chemin d’accès à l’aide d’une des procédures suivantes dans **Explorateur du contrôle de code Source**:  
  
    -   Dans le **dossiers** volet, cliquez sur le dossier qui contient le fichier d’ensemble de règles. Copiez le chemin d’accès du contrôle de version du dossier qui s’affiche dans le **Source** , puis tapez le nom du fichier de jeu de règles manuellement.  
  
    -   Dans la fenêtre de détails, cliquez sur le fichier d’ensemble de règles, puis cliquez sur **propriétés**. Sur le **général** onglet, copiez la valeur dans **nom du serveur**.  
  
## <a name="synchronizing-code-projects-to-the-check-in-policy-rule-set"></a>Synchroniser des projets de Code à l’ensemble de règles de stratégie d’archivage  
 Vous spécifiez une règle de stratégie d’archivage de projet équipe comme ensemble de règles de l’analyse de code d’une configuration de projet de code dans la boîte de dialogue Propriétés du projet de code. Si l’ensemble de règles se trouve sur le même lecteur que le projet de code, un chemin d’accès relatif est utilisé pour spécifier l’ensemble de règles lorsque le chemin d’accès est sélectionné dans la boîte de dialogue de fichier. Structures de contrôle du chemin d’accès relatif permet les paramètres de propriétés de projet pour être transposables à d’autres ordinateurs qui utilisent la même version locale.  
  
#### <a name="to-specify-a-team-project-rule-set-as-the-rule-set-of-a-code-project"></a>Pour spécifier une règle de projet d’équipe défini en tant que l’ensemble de règles d’un projet de code  
  
1.  Si nécessaire, vous devez récupérer le dossier de jeu de règles de stratégie d’archivage et le fichier du contrôle de version.  
  
     Vous pouvez effectuer cette étape dans **Explorateur du contrôle de code Source** en double-cliquant sur la règle définie puis cliquer sur **obtenir la dernière Version**.  
  
2.  Dans **l’Explorateur de solutions**, cliquez sur le projet de code, puis cliquez sur **propriétés**.  
  
3.  **Cliquez sur l’analyse du Code**.  
  
4.  Si nécessaire, cliquez sur les options appropriées dans le **Configuration** et **plateforme** répertorie.  
  
5.  Pour exécuter l’analyse du code chaque fois que le projet de code est généré à l’aide de la configuration spécifiée, sélectionnez le **activer analyse du Code sur la Build (définit la constante CODE_ANALYSIS)** case à cocher.  
  
6.  Pour ignorer le code dans les composants d’autres sociétés, sélectionnez le **supprimer les résultats du code généré** case à cocher.  
  
7.  Dans le **exécuter cet ensemble de règles** , cliquez sur  **\<Parcourir... >**.  
  
8.  Spécifiez la version locale du fichier de jeu de règle de stratégie d’archivage.