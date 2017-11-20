---
title: "Comment : créer un ensemble de règles personnalisé | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.addremoverulesets
helpviewer_keywords: Development Edition, rule sets
ms.assetid: bcc42508-9592-4802-9f66-a50111641d73
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7e9cba33565af81a76d043a3fc3f63eef831e1ce
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-a-custom-rule-set"></a>Comment : créer un ensemble de règles personnalisé
Dans [!INCLUDE[vsUltShort](../code-quality/includes/vsultshort_md.md)], [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)], et [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)], vous pouvez créer et modifier une personnalisée *ensemble de règles* pour répondre aux besoins de projet spécifique associés à l’analyse du code. Pour créer une règle personnalisée définie, vous ouvrez un, ou ensembles de règles plus standard dans l’éditeur d’ensemble de règles. Vous pouvez ensuite ajouter ou supprimer des règles spécifiques, et vous pouvez modifier l’action qui se produit lorsque l’analyse du code détermine qu’une règle a été violée.  
  
 Pour créer une nouvelle règle personnalisée définie, vous l’enregistrez à l’aide d’un nouveau nom de fichier. L’ensemble de règles personnalisé est automatiquement attribué au projet.  
  
## <a name="opening-the-rule-set-editor"></a>Éditeur d’ensembles de l’ouverture de la règle  
  
#### <a name="to-open-an-empty-rule-set-file-in-the-rule-set-editor"></a>Pour ouvrir vide ensemble de règles fichier dans l’éditeur d’ensemble de règles  
  
1.  Sur le **fichier** menu de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], pointez sur **nouveau** puis cliquez sur **fichier**.  
  
2.  Dans le **nouveau fichier** boîte de dialogue, cliquez sur **général** dans les **modèles installés** liste, puis sélectionnez **ensemble de règles d’analyse de Code**.  
  
3.  L’éditeur d’ensemble de règles s’affiche. Aucune règle n’est sélectionnés dans la liste de l’éditeur.  
  
#### <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>Pour créer une règle personnalisée à partir d’un seul ensemble de règles existant  
  
1.  Dans l’Explorateur de solutions, cliquez sur le projet, puis sélectionnez **propriétés**.  
  
2.  Sur le **propriétés** , cliquez sur **l’analyse du Code**.  
  
3.  Dans le **l’ensemble de règles** liste déroulante, effectuez l’une des opérations suivantes :  
  
    -   Sélectionnez l’ensemble de règles que vous souhaitez personnaliser.  
  
     \- ou -  
  
    -   Sélectionnez  **\<Parcourir... >** pour spécifier une règle existante du jeu qui n’est pas dans la liste.  
  
4.  Cliquez sur **ouvrir** pour afficher les règles dans l’éditeur d’ensemble de règles.  
  
#### <a name="to-create-a-custom-rule-set-from-multiple-existing-rule-sets"></a>Pour créer une règle personnalisée définie à partir de plusieurs ensembles de règles existant  
  
1.  Dans l’Explorateur de solutions, cliquez sur le projet, puis sélectionnez **propriétés**.  
  
2.  Sur le **propriétés** , cliquez sur **l’analyse du Code**.  
  
3.  Sélectionnez  **\<choisir plusieurs règle définit... >** de **exécuter cet ensemble de règles**.  
  
4.  Dans le **ajouter ou supprimer des ensembles de règles** boîte de dialogue, sélectionnez les ensembles de règles sur lequel vous souhaitez baser votre nouvel ensemble de règles, puis cliquez sur **OK**.  
  
5.  Enregistrez le nouvel ensemble de règles.  
  
     Le nom du nouvel ensemble de règles est sélectionné dans le **exécuter cet ensemble de règles** liste. Vous pouvez modifier le nom complet de l’ensemble de règles dans l’étape suivante.  
  
6.  (Facultatif) Pour modifier le nom complet de l’ensemble de règles, dans le **vue** menu, cliquez sur **fenêtre Propriétés**. Tapez le nom complet dans le **nom** boîte.  
  
7.  Pour ajouter, supprimer, ou modifier des règles d’analyse du code spécifique dans le nouvel ensemble de règles, cliquez sur **ouvrir**.  
  
## <a name="modifying-a-rule-set"></a>Modification d’un ensemble de règles  
  
#### <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>Pour modifier une règle définie dans l’éditeur d’ensemble de règles  
  
-   Pour modifier le nom complet de l’ensemble de règles, dans le **vue** menu, cliquez sur **fenêtre Propriétés**. Entrez le nom d’affichage dans le **nom** boîte. Notez que le nom complet peut différer du nom de fichier.  
  
-   Pour ajouter toutes les règles du groupe à un ensemble de règles personnalisé, sélectionnez la case à cocher du groupe. Pour supprimer toutes les règles du groupe, désactivez la case à cocher.  
  
-   Pour ajouter une règle spécifique à l’ensemble de règles personnalisé, sélectionnez la case à cocher de la règle. Pour supprimer la règle de l’ensemble de règles, désactivez la case à cocher.  
  
-   Pour modifier l’action effectuée lorsqu’une règle est violée dans une analyse du code, cliquez dans le **Action** champ pour la règle, puis sélectionnez une des valeurs suivantes :  
  
     **Avertir** -génère un avertissement.  
  
     **Erreur** -génère une erreur.  
  
     **Aucun** -désactive la règle. Cette action est le même que la suppression de la règle de l’ensemble de règles.  
  
## <a name="changing-the-rule-set-editor-display"></a>Modification de la règle de jeu d’affichage de l’éditeur  
  
#### <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>Pour regrouper, filtrer ou modifier les champs dans l’éditeur d’ensemble de règles à l’aide de la barre d’outils Éditeur de règle ensemble  
  
-   Pour développer les règles dans tous les groupes, cliquez sur **développer tout**.  
  
-   Pour réduire les règles dans tous les groupes, cliquez sur **réduire tout**.  
  
-   Pour modifier le champ règles sont regroupées par, sélectionnez le champ à partir de la **Group By** liste. Pour afficher les règles non groupés, sélectionnez  **\<aucun >**.  
  
-   Pour ajouter ou supprimer des champs dans les colonnes de la règle, cliquez sur **Options de colonne**.  
  
-   Pour masquer des règles qui ne s’appliquent pas à la solution actuelle, **masquer des règles qui ne s’appliquent pas à la solution actuelle**.  
  
-   Pour basculer entre l’affichage et masquage des règles qui sont affectés à l’action d’erreur, cliquez sur **afficher les règles qui peuvent générer des erreurs d’analyse du Code**.  
  
-   Pour basculer entre l’affichage et masquage des règles qui sont affectés à l’action de l’avertissement, cliquez sur **afficher les règles qui peuvent générer des avertissements d’analyse du Code**.  
  
-   Pour basculer entre l’affichage et masquage des règles qui sont affectés les **aucun** action, cliquez sur **afficher les règles qui ne sont pas activées**.  
  
-   Pour ajouter ou supprimer des ensembles de règle par défaut pour l’ensemble de règles actuel Microsoft, cliquez sur **des ensembles de règles enfants Add ou remove**.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : configurer l’analyse du Code pour un projet de Code managé](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)   
 [Informations de référence sur l’ensemble de règles d’analyse du code](../code-quality/code-analysis-rule-set-reference.md)