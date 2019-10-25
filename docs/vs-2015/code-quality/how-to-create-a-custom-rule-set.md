---
title: 'Procédure : Créer un ensemble de règles personnalisé | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.addremoverulesets
helpviewer_keywords:
- Development Edition, rule sets
ms.assetid: bcc42508-9592-4802-9f66-a50111641d73
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6e4aef02a2bb320112d7d268da28cf66b1ec6751
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657447"
---
# <a name="how-to-create-a-custom-rule-set"></a>Procédure : Créer un ensemble de règles personnalisé
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)], [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] et [!INCLUDE[vsPro](../includes/vspro-md.md)], vous pouvez créer et modifier un ensemble de *règles* personnalisé pour répondre à des besoins de projet spécifiques associés à l’analyse du code. Pour créer un ensemble de règles personnalisé, vous ouvrez un ou plusieurs ensembles de règles standard dans l’éditeur d’ensembles de règles. Vous pouvez ensuite ajouter ou supprimer des règles spécifiques, et vous pouvez modifier l’action qui se produit lorsque l’analyse du code détermine qu’une règle a été violée.

 Pour créer un ensemble de règles personnalisé, enregistrez-le à l’aide d’un nouveau nom de fichier. L’ensemble de règles personnalisé est automatiquement affecté au projet.

## <a name="opening-the-rule-set-editor"></a>Ouverture de l’éditeur d’ensembles de règles

#### <a name="to-open-an-empty-rule-set-file-in-the-rule-set-editor"></a>Pour ouvrir un fichier d’ensemble de règles vide dans l’éditeur d’ensembles de règles

1. Dans le menu **fichier** de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], pointez sur **nouveau** , puis cliquez sur **fichier**.

2. Dans la boîte de dialogue **nouveau fichier** , cliquez sur **général** dans la liste **modèles installés** , puis sélectionnez **ensemble de règles d’analyse du code**.

3. L’éditeur d’ensembles de règles s’affiche. Aucune règle n’est sélectionnée dans la liste de l’éditeur.

#### <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>Pour créer une règle personnalisée à partir d’un seul ensemble de règles existant

1. Dans Explorateur de solutions, cliquez avec le bouton droit sur le projet, puis sélectionnez **Propriétés**.

2. Sous l’onglet **Propriétés** , cliquez sur **analyse du code**.

3. Dans la liste déroulante **ensemble de règles** , effectuez l’une des opérations suivantes :

   - Sélectionnez l’ensemble de règles que vous souhaitez personnaliser.

     \- ou -

   - Sélectionner **\<Browse... >** pour spécifier un ensemble de règles existant qui ne figure pas dans la liste.

4. Cliquez sur **ouvrir** pour afficher les règles dans l’éditeur d’ensembles de règles.

#### <a name="to-create-a-custom-rule-set-from-multiple-existing-rule-sets"></a>Pour créer un ensemble de règles personnalisé à partir de plusieurs ensembles de règles existants

1. Dans Explorateur de solutions, cliquez avec le bouton droit sur le projet, puis sélectionnez **Propriétés**.

2. Sous l’onglet **Propriétés** , cliquez sur **analyse du code**.

3. Sélectionner **\<Choose plusieurs ensembles de règles... >** de **l’exécution de cet ensemble de règles**.

4. Dans la boîte de dialogue **Ajouter ou supprimer des ensembles de règles** , sélectionnez les ensembles de règles sur lesquels vous souhaitez baser votre nouvel ensemble de règles, puis cliquez sur **OK**.

5. Enregistrez le nouvel ensemble de règles.

     Le nom du nouvel ensemble de règles est sélectionné dans la liste **exécuter cet ensemble de règles** . Vous pouvez modifier le nom complet de l’ensemble de règles à l’étape suivante.

6. Facultatif Pour modifier le nom complet de l’ensemble de règles, dans le menu **affichage** , cliquez sur **fenêtre Propriétés**. Tapez le nom d’affichage dans la zone **nom** .

7. Pour ajouter, supprimer ou modifier des règles d’analyse du code spécifiques dans le nouvel ensemble de règles, cliquez sur **ouvrir**.

## <a name="modifying-a-rule-set"></a>Modification d’un ensemble de règles

#### <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>Pour modifier un ensemble de règles dans l’éditeur d’ensembles de règles

- Pour modifier le nom complet de l’ensemble de règles, dans le menu **affichage** , cliquez sur **fenêtre Propriétés**. Entrez le nom d’affichage dans la zone **nom** . Notez que le nom d’affichage peut être différent du nom de fichier.

- Pour ajouter toutes les règles du groupe à un ensemble de règles personnalisé, activez la case à cocher du groupe. Pour supprimer toutes les règles du groupe, désactivez la case à cocher.

- Pour ajouter une règle spécifique à l’ensemble de règles personnalisé, activez la case à cocher de la règle. Pour supprimer la règle de l’ensemble de règles, désactivez la case à cocher.

- Pour modifier l’action entreprise lorsqu’une règle est violée dans une analyse du code, cliquez dans le champ **action** de la règle, puis sélectionnez l’une des valeurs suivantes :

     **WARN** -génère un avertissement.

     **Erreur** : génère une erreur.

     **None** : désactive la règle. Cette action revient à supprimer la règle de l’ensemble de règles.

## <a name="changing-the-rule-set-editor-display"></a>Modification de l’affichage de l’éditeur d’ensembles de règles

#### <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>Pour regrouper, filtrer ou modifier les champs de l’éditeur d’ensembles de règles à l’aide de la barre d’outils Éditeur d’ensemble de règles

- Pour développer les règles de tous les groupes, cliquez sur **développer tout**.

- Pour réduire les règles de tous les groupes, cliquez sur **réduire tout**.

- Pour modifier le champ par lequel les règles sont regroupées, sélectionnez le champ dans la liste **regrouper par** . Pour afficher les règles non groupées, sélectionnez **\<None >** .

- Pour ajouter ou supprimer des champs dans les colonnes de règle, cliquez sur **options de colonne**.

- Pour masquer les règles qui ne s’appliquent pas à la solution actuelle, **masquez les règles qui ne s’appliquent pas à la solution actuelle**.

- Pour basculer entre l’affichage et le masquage des règles affectées par l’action d’erreur, cliquez sur **afficher les règles qui peuvent générer des erreurs d’analyse du code**.

- Pour basculer entre l’affichage et le masquage des règles affectées par l’action d’avertissement, cliquez sur **afficher les règles qui peuvent générer des avertissements d’analyse du code**.

- Pour basculer entre l’affichage et le masquage des règles affectées par l’action **aucun** , cliquez sur **afficher les règles qui ne sont pas activées**.

- Pour ajouter ou supprimer des ensembles de règles par défaut Microsoft pour l’ensemble de règles actuel, cliquez sur **Ajouter ou supprimer des ensembles de règles enfants**.

## <a name="see-also"></a>Voir aussi
 [Guide pratique : Configurer l’analyse du code pour un projet de code managé ](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md) référence de l' [ensemble de règles d’analyse du code](../code-quality/code-analysis-rule-set-reference.md)
