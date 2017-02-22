---
title: "Comment&#160;: cr&#233;er un ensemble de r&#232;gles personnalis&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.addremoverulesets"
helpviewer_keywords: 
  - "Development Edition, ensembles de règles"
ms.assetid: bcc42508-9592-4802-9f66-a50111641d73
caps.latest.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 24
---
# Comment&#160;: cr&#233;er un ensemble de r&#232;gles personnalis&#233;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dans [!INCLUDE[vsUltShort](../code-quality/includes/vsultshort_md.md)], [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)], et [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)], créez et modifiez un *ensemble de règles* personnalisé pour satisfaire des besoins de projet spécifiques, associés à l'analyse du code.  Pour créer un ensemble de règles personnalisé, ouvrez un ou plusieurs ensembles de règles standard dans l'éditeur d'ensemble de règles.  Vous pouvez ensuite ajouter ou supprimer des règles spécifiques et modifier l'action qui se produit lorsque l'analyse du code détermine qu'une règle a été violée.  
  
 Pour créer un ensemble de règles personnalisé, il convient de l'enregistrer sous un nouveau nom de fichier.  L'ensemble de règles personnalisé est automatiquement assigné au projet.  
  
## Ouverture de l'éditeur d'ensemble de règles  
  
#### Pour ouvrir un fichier d'ensemble de règles vide dans l'éditeur d'ensembles de règles  
  
1.  Dans le menu **Fichier** de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], pointez sur **Nouveau**, puis cliquez sur **Fichier**.  
  
2.  Dans la boîte de dialogue **Nouveau fichier**, cliquez sur **Général** dans la liste **Modèles installés**, puis sélectionnez **Ensemble de règles d'analyse du code**.  
  
3.  L'éditeur d'ensembles de règles apparaît.  Aucune règle n'est sélectionnée dans la liste de l'éditeur.  
  
#### Pour créer une règle personnalisée à partir d'un seul ensemble de règles existant  
  
1.  Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le projet, puis sélectionnez **Propriétés**.  
  
2.  Dans l'onglet **Propriétés**, cliquez sur **Analyse du code**.  
  
3.  Dans la liste déroulante **Ensemble de règles**, effectuez l'une des opérations suivantes :  
  
    -   Sélectionnez l'ensemble de règles que vous voulez personnaliser.  
  
     \- ou \-  
  
    -   Sélectionnez **\<Parcourir...\>** pour spécifier un ensemble de règles existant qui ne figure pas dans la liste.  
  
4.  Cliquez sur **Ouvrir** pour afficher les règles dans l'éditeur d'ensemble de règles.  
  
#### Pour créer un ensemble de règles personnalisé à partir de plusieurs ensembles de règles existants  
  
1.  Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le projet, puis sélectionnez **Propriétés**.  
  
2.  Dans l'onglet **Propriétés**, cliquez sur **Analyse du code**.  
  
3.  Sélectionnez **\<Choisissez plusieurs ensembles de règles...\>** à partir de **Exécuter cet ensemble de règles**.  
  
4.  Dans la boîte de dialogue **Ajouter ou supprimer des ensembles de règles**, sélectionnez les ensembles de règles sur lesquels vous souhaitez baser votre nouvel ensemble de règles, puis cliquez sur **OK**.  
  
5.  Enregistrez le nouvel ensemble de règles.  
  
     Le nom du nouvel ensemble de règles est sélectionné dans la liste **Exécuter cet ensemble de règles**.  Vous pouvez modifier le nom complet de l'ensemble de règles lors de l'étape suivante.  
  
6.  \(Facultatif\) Pour modifier le nom complet de l'ensemble de règles, dans le menu **Affichage**, cliquez sur **Fenêtre Propriétés**.  Tapez le nom complet dans la zone **Nom**.  
  
7.  Pour ajouter, supprimer ou modifier des règles d'analyse du code particulières dans le nouvel ensemble de règles, cliquez sur **Ouvrir**.  
  
## Modification d'un ensemble de règles  
  
#### Pour modifier un ensemble de règles dans l'éditeur d'ensemble de règles  
  
-   Pour modifier le nom complet de l'ensemble de règles, dans le menu **Affichage**, cliquez sur **Fenêtre Propriétés**.  Entrez le nom complet dans la zone **Nom**.  Notez que le nom complet peut différer du nom de fichier.  
  
-   Pour ajouter toutes les règles du groupe à un ensemble de règles personnalisé, activez la case à cocher du groupe.  Pour supprimer toutes les règles du groupe, désactivez la case à cocher.  
  
-   Pour ajouter une règle spécifique à l'ensemble de règles personnalisé, activez la case à cocher de la règle.  Pour supprimer la règle de l'ensemble de règles, désactivez la case à cocher.  
  
-   Pour modifier l'action entreprise lorsqu'une règle est violée dans une analyse du code, cliquez dans le champ **Action** correspondant à la règle, puis sélectionnez l'une des valeurs suivantes :  
  
     **Warn** \- génère un avertissement.  
  
     **Error** \- génère une erreur.  
  
     **None** \- désactive la règle.  Cette action revient à supprimer la règle de l'ensemble de règles.  
  
## Modification de l'affichage de l'éditeur d'ensemble de règles  
  
#### Pour grouper, filtrer ou modifier les champs dans l'éditeur d'ensemble de règles au moyen de la barre d'outils de l'éditeur  
  
-   Pour développer les règles dans tous les groupes, cliquez sur **Développer tout**.  
  
-   Pour réduire les règles dans tous les groupes, cliquez sur **Réduire tout.**  
  
-   Pour modifier le champ selon lequel les règles sont groupées, sélectionnez\-le dans la liste **Grouper par**.  Pour afficher les règles sans les grouper, sélectionnez **\<Aucun\>**.  
  
-   Pour ajouter ou supprimer des champs dans les colonnes de règle, cliquez sur **Options de colonne**.  
  
-   Pour masquer des règles qui ne s'appliquent pas à la solution actuelle, sélectionnez **Masquer les règles qui ne s'appliquent pas à la solution actuelle**.  
  
-   Pour basculer entre l'affichage et le masquage des règles qui se sont vues assigner l'action Erreur, cliquez sur **Afficher les règles qui peuvent générer des erreurs d'analyse du code**.  
  
-   Pour basculer entre l'affichage et le masquage des règles qui se sont vues assigner l'action Avertissement, cliquez sur **Afficher les règles qui peuvent générer des avertissements d'analyse du code**.  
  
-   Pour basculer entre l'affichage et le masquage des règles qui se sont vues assigner l'action **Aucune**, cliquez sur **Afficher les règles qui ne sont pas activées**.  
  
-   Pour ajouter ou supprimer des ensembles de règles Microsoft par défaut dans l'ensemble de règles actuel, cliquez sur **Ajouter ou supprimer les ensembles de règles enfants**.  
  
## Voir aussi  
 [Procédure : configurer l’analyse du code pour un projet de code managé](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)   
 [Référence d’ensemble de règles d’analyse du code](../code-quality/code-analysis-rule-set-reference.md)