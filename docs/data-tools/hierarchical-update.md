---
title: Mise à jour hiérarchique
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- saving data, changed data
- data [Visual Basic], hierarchical update
- saving updated data
- datasets [Visual Basic], hierarchical update
- hierarchical update
- saving data, hierarchical update
- modified data saving
- updated data saving
- related tables, saving
ms.assetid: 68bae3f6-ec9b-45ee-a33a-69395029f54c
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 52225ba4801fcee92b3f68fd6ec1cf7cc6c63086
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305713"
---
# <a name="hierarchical-update"></a>Mise à jour hiérarchique

*Mise à jour hiérarchique* fait référence au processus d’enregistrement des données mises à jour (à partir d’un jeu de données avec deux ou plusieurs tables connexes) dans une base de données tout en conservant les règles d’intégrité référentielle. *L’intégrité référentielle* fait référence aux règles de cohérence fournies par les contraintes dans une base de données qui contrôlent le comportement de l’insertion, la mise à jour et suppression des enregistrements associés. Par exemple, il est l’intégrité référentielle impose la création d’un enregistrement de client avant d’autoriser des commandes doit être créé pour ce client.  Pour plus d’informations sur les relations dans les jeux de données, consultez [relations dans les datasets](../data-tools/relationships-in-datasets.md).

La fonctionnalité de mise à jour hiérarchique utilise un `TableAdapterManager` pour gérer le `TableAdapter`s dans un dataset typé. Le `TableAdapterManager` composant est une classe générée par Visual Studio, il est donc pas partie de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Lorsque vous faites glisser une table à partir de la **des Sources de données** fenêtre vers une page Windows Form ou WPF, Visual Studio ajoute une variable de type TableAdapterManager à la page ou le formulaire, et il apparaît dans le concepteur dans la barre d’état du composant. Pour plus d’informations sur la `TableAdapterManager` de classe, consultez la section de référence de TableAdapterManager de [TableAdapters](../data-tools/create-and-configure-tableadapters.md).

Par défaut, un jeu de données traite les tables associées « uniquement, pour les relations » ce qui signifie qu’il n’impose pas les contraintes de clé étrangères. Vous pouvez modifier ce paramètre au moment du design en utilisant la **Concepteur de Dataset**. Sélectionnez la ligne de relation entre deux tables pour afficher le **Relation** boîte de dialogue. Les modifications apportées ici détermine comment la `TableAdapterManager` se comporte quand il renvoyer les modifications dans les tables associées à la base de données.

## <a name="enable-hierarchical-update-in-a-dataset"></a>Activer la mise à jour hiérarchique dans un jeu de données

Par défaut, la mise à jour hiérarchique est activée pour tous les nouveaux jeux de données qui est ajoutés ou créés dans un projet. Activer ou désactiver les mises à jour hiérarchique en définissant le **mettre à jour hiérarchique** propriété d’un dataset typé dans le jeu de données **True** ou **False**:

![Paramètre de mise à jour hiérarchique](../data-tools/media/hierarchical-update-setting.png)

## <a name="create-a-new-relation-between-tables"></a>Créez une relation entre tables

Pour créer une nouvelle relation entre deux tables, dans le Concepteur de Dataset, sélectionnez la barre de titre de chaque table, avec le bouton droit et sélectionnez **ajouter une relation**.

![Relation menu Ajouter une mise à jour hiérarchique](../data-tools/media/hierarchical-update-add-relation-menu.png)

## <a name="understand-foreign-key-constraints-cascading-updates-and-deletes"></a>Comprendre les contraintes de clé étrangère, les mises à jour en cascade et les suppressions

Il est important de comprendre comment contraintes de clé étrangère et comportement en cascade dans la base de données sont créés dans le code généré du jeu de données.

Par défaut, les tables de données dans un jeu de données sont générées avec des relations (<xref:System.Data.DataRelation>) qui correspondent aux relations dans la base de données. Toutefois, la relation dans le jeu de données n’est pas générée comme une contrainte foreign key. Le <xref:System.Data.DataRelation> est configuré en tant que **Relation uniquement** sans <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> ou <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> en vigueur.

Par défaut, les mises à jour en cascade et les suppressions en cascade sont désactivées même si la relation de base de données est définie avec les mises à jour en cascade et/ou suppressions en cascade sous tension. Par exemple, création d’un nouveau client et une commande et tente d’enregistrer les données peuvent provoquer un conflit avec les contraintes de clé étrangère sont définies dans la base de données. Pour plus d’informations, consultez [désactiver les contraintes pendant le remplissage d’un jeu de données](turn-off-constraints-while-filling-a-dataset.md).

## <a name="set-the-order-to-perform-updates"></a>Définir l’ordre pour effectuer des mises à jour

Définition de l’ordre pour effectuer des mises à jour définit l’ordre de la personne insère, met à jour et les suppressions qui est requis pour enregistrer toutes les données modifiées dans toutes les tables d’un dataset. Lors de la mise à jour hiérarchique est activée, insertions sont exécutées en premier, puis met à jour, puis supprime. Le `TableAdapterManager` fournit un `UpdateOrder` propriété qui peut être ensemble pour effectuer des mises à jour tout d’abord, puis les insertions et suppressions.

> [!NOTE]
> Il est important de comprendre que l’ordre de mise à jour est exhaustive. Autrement dit, lorsque les mises à jour sont effectuées, insertions et suppressions sont effectuées pour toutes les tables dans le jeu de données.

Pour définir le `UpdateOrder` propriété, après avoir fait glisser des éléments à partir de la [fenêtre Sources de données](add-new-data-sources.md#data-sources-window) sur un formulaire, sélectionnez le `TableAdapterManager` dans la barre d’état du composant, puis définissez le `UpdateOrder` propriété dans le **propriétés** fenêtre.

## <a name="create-a-backup-copy-of-a-dataset-before-performing-a-hierarchical-update"></a>Créer une copie de sauvegarde d’un jeu de données avant d’effectuer une mise à jour hiérarchique

Lorsque vous enregistrez des données (en appelant le `TableAdapterManager.UpdateAll()` méthode), la `TableAdapterManager` tente de mettre à jour les données pour chaque table dans une transaction unique. Si une partie de la mise à jour pour n’importe quelle table échoue, la transaction entière est annulée. Dans la plupart des cas, la restauration retourne votre application à son état d’origine.

Toutefois, vous pouvez parfois restaurer le jeu de données à partir de la copie de sauvegarde. Un exemple de ceci peut se produire lorsque vous utilisez des valeurs incrémentées automatiquement. Par exemple, si un enregistrement opération n’aboutit pas, valeurs incrémentées automatiquement ne sont pas réinitialisées dans le jeu de données, et le jeu de données continue à créer des valeurs à incrémentation automatique. Cela laisse un écart de numérotation qui ne peut pas être acceptable dans votre application. Dans les situations où il s’agit d’un problème, le `TableAdapterManager` fournit un `BackupDataSetBeforeUpdate` propriété qui remplace le jeu de données existant par une copie de sauvegarde si la transaction échoue.

> [!NOTE]
> La copie de sauvegarde est uniquement en mémoire lors de la `TableAdapterManager.UpdateAll` méthode est en cours d’exécution. Il n’est donc aucun accès par programmation à ce jeu de données de sauvegarde, car il remplace le jeu de données d’origine ou est hors de portée dès que le `TableAdapterManager.UpdateAll` méthode termine en cours d’exécution.

## <a name="modify-the-generated-save-code-to-perform-the-hierarchical-update"></a>Modifier le texte généré le code pour effectuer la mise à jour hiérarchique d’enregistrement

Enregistrez les modifications des tables de données associées du dataset dans la base de données en appelant la méthode `TableAdapterManager.UpdateAll` et en passant le nom du dataset contenant les tables associées. Par exemple, exécutez la méthode `TableAdapterManager.UpdateAll(NorthwindDataset)` pour envoyer les mises à jour de toutes les tables de NorthwindDataset à la base de données principale.

Une fois que vous avez déposé des éléments provenant de la fenêtre **Sources de données**, du code est ajouté automatiquement à l’événement `Form_Load` pour remplir chaque table (les méthodes `TableAdapter.Fill`). Du code est également ajouté à l’événement Click du bouton **Enregistrer** du <xref:System.Windows.Forms.BindingNavigator> pour enregistrer les données du dataset dans la base de données (la méthode `TableAdapterManager.UpdateAll`).

Le code d'enregistrement généré contient également une ligne de code qui appelle la méthode `CustomersBindingSource.EndEdit`. Plus spécifiquement, il appelle le <xref:System.Windows.Forms.BindingSource.EndEdit%2A> méthode du premier <xref:System.Windows.Forms.BindingSource>qui est ajouté au formulaire. En d’autres termes, ce code est généré uniquement pour la première table qui est déplacée de la **des Sources de données** fenêtre vers le formulaire. L’appel de <xref:System.Windows.Forms.BindingSource.EndEdit%2A> valide toutes les modifications en cours de tous les contrôles liés aux données modifiés. Par conséquent, si un contrôle lié aux données a encore le focus et que vous cliquez sur le bouton **Enregistrer**, toutes les modifications en attente dans ce contrôle sont validées avant l’enregistrement réel (la méthode `TableAdapterManager.UpdateAll`).

> [!NOTE]
> Le **Concepteur de Dataset** ajoute uniquement les `BindingSource.EndEdit` code pour la première table qui est déplacée vers le formulaire. Par conséquent, vous devez ajouter une ligne de code pour appeler la méthode `BindingSource.EndEdit` pour chaque table associée dans le formulaire. Dans cette procédure pas à pas, cela signifie que vous devez ajouter un appel à la méthode `OrdersBindingSource.EndEdit`.

### <a name="to-update-the-code-to-commit-changes-to-the-related-tables-before-saving"></a>Pour mettre à jour le code afin de valider les modifications des tables associées avant l’enregistrement

1.  Double-cliquez sur le bouton **Enregistrer** du <xref:System.Windows.Forms.BindingNavigator> pour ouvrir **Form1** dans l’éditeur de code.

2.  Ajoutez une ligne de code pour appeler la méthode `OrdersBindingSource.EndEdit` après la ligne appelant la méthode `CustomersBindingSource.EndEdit`. Le code de l’événement Click du bouton **Enregistrer** doit ressembler à ce qui suit :

     [!code-vb[VSProDataOrcasHierarchicalUpdate#1](../data-tools/codesnippet/VisualBasic/hierarchical-update_1.vb)]
     [!code-csharp[VSProDataOrcasHierarchicalUpdate#1](../data-tools/codesnippet/CSharp/hierarchical-update_1.cs)]

Outre la validation des modifications d’une table enfant associée avant l’enregistrement des données dans une base de données, vous devez aussi peut-être valider les enregistrements parents récemment créés avant d’ajouter de nouveaux enregistrement enfants à un dataset. En d’autres termes, vous devrez peut-être ajouter le nouvel enregistrement parent (`Customer`) au jeu de données avant de contraintes de clé étrangère activer de nouveaux enregistrements enfants (`Orders`) à ajouter au jeu de données. Pour ce faire, vous pouvez utiliser l'événement `BindingSource.AddingNew` enfant.

> [!NOTE]
> Si vous devez valider les nouveaux enregistrements parents varie selon le type de contrôle qui est utilisé pour lier à votre source de données. Dans cette procédure pas à pas, vous utilisez des contrôles individuels à lier à la table parente. Cela nécessite du code supplémentaire pour valider le nouvel enregistrement parent. Si les enregistrements parents ont été affichés à la place dans un contrôle de liaison complexe tel que le <xref:System.Windows.Forms.DataGridView>ce supplémentaires <xref:System.Windows.Forms.BindingSource.EndEdit%2A> appeler pour l’enregistrement parent ne serait pas nécessaire. En effet, la fonctionnalité sous-jacente de liaison aux données du contrôle gère la validation des nouveaux enregistrements.

### <a name="to-add-code-to-commit-parent-records-in-the-dataset-before-adding-new-child-records"></a>Pour ajouter du code afin de valider les enregistrements parents dans le dataset avant d'ajouter de nouveaux enregistrements enfants

1.  Créez un gestionnaire d'événements pour l'événement `OrdersBindingSource.AddingNew`.

    -   Ouvrez **Form1** en mode conception, sélectionnez **OrdersBindingSource** dans la barre des composants, sélectionnez **événements** dans le **propriétés** fenêtre, et puis double-cliquez sur le **AddingNew** événement.

2.  Ajouter une ligne de code au gestionnaire d’événements qui appelle la `CustomersBindingSource.EndEdit` (méthode). Le code du gestionnaire d'événements `OrdersBindingSource_AddingNew` doit ressembler à ce qui suit :

     [!code-vb[VSProDataOrcasHierarchicalUpdate#2](../data-tools/codesnippet/VisualBasic/hierarchical-update_2.vb)]
     [!code-csharp[VSProDataOrcasHierarchicalUpdate#2](../data-tools/codesnippet/CSharp/hierarchical-update_2.cs)]

## <a name="tableadaptermanager-reference"></a>Référence de TableAdapterManager

Par défaut, un `TableAdapterManager` classe est générée lorsque vous créez un dataset qui contient les tables associées. Pour éviter que la classe en cours de génération, modifiez la valeur de la `Hierarchical Update` propriété du jeu de données sur false. Lorsque vous faites glisser une table qui possède une relation sur l’aire de conception d’un Windows Form ou d’une page WPF, Visual Studio déclare une variable membre de la classe. Si vous n’utilisez la liaison de données, vous devez manuellement déclarer la variable.

Le `TableAdapterManager` classe n’est pas dans le cadre de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Par conséquent, vous ne pouvez pas chercher dans la documentation. Il est créé au moment du design dans le cadre du processus de création de jeu de données.

Les éléments suivants sont les méthodes fréquemment utilisées et les propriétés de la `TableAdapterManager` classe :

|Membre|Description|
|------------|-----------------|
|Méthode `UpdateAll`|Enregistre toutes les données de toutes les tables de données.|
|Propriété`BackUpDataSetBeforeUpdate` |Détermine s’il faut créer une copie de sauvegarde du jeu de données avant d’exécuter le `TableAdapterManager.UpdateAll` (méthode). Valeur booléenne.|
|*tableName* `TableAdapter` propriété|Représente un `TableAdapter`. Le texte généré `TableAdapterManager` contient une propriété pour chaque `TableAdapter` qu’il gère. Par exemple, un jeu de données avec une table Customers et Orders est généré avec un `TableAdapterManager` contenant `CustomersTableAdapter` et `OrdersTableAdapter` propriétés.|
|Propriété`UpdateOrder` |Contrôler l’ordre de l’individuel insert, update et les commandes delete. Définissez ce paramètre à une des valeurs dans le `TableAdapterManager.UpdateOrderOption` énumération.<br /><br /> Par défaut, le `UpdateOrder` a la valeur **InsertUpdateDelete**. Cela signifie que les insertions, puis met à jour et supprime ensuite sont effectuées pour toutes les tables dans le jeu de données.|

## <a name="see-also"></a>Voir aussi

- [Enregistrer les données dans la base de données](../data-tools/save-data-back-to-the-database.md)
