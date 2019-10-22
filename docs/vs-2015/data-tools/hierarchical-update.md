---
title: Mise à jour hiérarchique | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
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
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 99e19bce34c2bc8578a062c87aaef10302589075
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670023"
---
# <a name="hierarchical-update"></a>Mise à jour hiérarchique
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La mise à jour hiérarchique * fait référence au processus d’enregistrement des données mises à jour (d’un DataSet avec au moins deux tables associées) dans une base de données tout en conservant les règles d’intégrité référentielle. L' *intégrité référentielle* fait référence aux règles de cohérence fournies par les contraintes d’une base de données qui contrôlent le comportement de l’insertion, de la mise à jour et de la suppression des enregistrements associés. Par exemple, il s’agit de l’intégrité référentielle qui impose la création d’un enregistrement de client avant d’autoriser la création de commandes pour ce client.  Pour plus d’informations sur les relations dans les jeux de données, consultez [relations dans les jeux de données](../data-tools/relationships-in-datasets.md) .

 La fonctionnalité de mise à jour hiérarchique utilise une `TableAdapterManager` pour gérer les `TableAdapter`s dans un DataSet typé. Le composant `TableAdapterManager` est une classe générée par le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. il ne fait donc pas partie de la [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Quand vous faites glisser une table de la fenêtre sources de données vers une page Windows Form ou WPF, Visual Studio ajoute une variable de type TableAdapterManager au formulaire ou à la page, et vous la voyez dans le concepteur de la barre d’état des composants. Pour plus d’informations sur la classe `TableAdapterManager`, consultez la section Référence TableAdapterManager de la [vue d’ensemble de TableAdapterManager](https://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650).

 Par défaut, un DataSet traite les tables associées comme des « relations uniquement », ce qui signifie qu’il n’applique pas de contraintes de clé étrangère. Vous pouvez modifier ce paramètre au moment du design à l’aide de l’Concepteur de DataSet. Sélectionnez la ligne de relation entre deux tables pour afficher la boîte de dialogue **relation** . Les modifications apportées ici déterminent la façon dont le TableAdapterManager se comporte lorsqu’il envoie à la base de données les modifications apportées aux tables connexes.

## <a name="enablehierarchical-update-in-a-dataset"></a>Mise à jour Enablehierarchical dans un jeu de données
 Par défaut, la mise à jour hiérarchique est activée pour tous les nouveaux jeux de données qui sont ajoutés ou créés dans un projet. Activez ou désactivez la mise à jour hiérarchique en affectant à la propriété **mise à jour hiérarchique** d’un DataSet typé dans le concepteur de DataSet la **valeur true** ou **false**:

 ![Paramètre de mise à jour hiérarchique](../data-tools/media/hierarchical-update-setting.png "Paramètre de mise à jour hiérarchique")

## <a name="create-a-new-relation-between-tables"></a>Créer une relation entre des tables
 Pour créer une relation entre deux tables, dans la Concepteur de DataSet, sélectionnez la barre de titre de chaque table, puis cliquez avec le bouton droit et sélectionnez**Ajouter une relation**.

 ![Menu mise à jour hiérarchique-ajouter une relation](../data-tools/media/hierarchical-update-add-relation-menu.png "Menu mise à jour hiérarchique-ajouter une relation")

## <a name="understand-foreign-key-constraints-cascading-updates-and-deletes"></a>Comprendre les contraintes de clé étrangère, les mises à jour en cascade et les suppressions
 Il est important de comprendre comment les contraintes de clé étrangère et le comportement en cascade dans la base de données sont créés dans le code du DataSet généré.

 Par défaut, les tables de données d’un DataSet sont générées avec des relations (<xref:System.Data.DataRelation>) qui correspondent aux relations dans la base de données. Toutefois, la relation dans le DataSet n’est pas générée en tant que contrainte de clé étrangère. La <xref:System.Data.DataRelation> est configurée en tant que **relation uniquement** sans <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> ou <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> en vigueur.

 Par défaut, les mises à jour en cascade et les suppressions en cascade sont désactivées, même si la relation de base de données est définie avec des mises à jour en cascade et/ou si les suppressions en cascade sont activées. Par exemple, la création d’un nouveau client et d’une nouvelle commande, puis la tentative d’enregistrement des données peuvent entraîner un conflit avec les contraintes de clé étrangère définies dans la base de données. Pour plus d’informations, consultez [Comment : configurer des contraintes de clé étrangère dans un DataSet](https://msdn.microsoft.com/library/3954c388-e209-4a67-a34e-5ca106282f8e).

## <a name="set-the-order-to-perform-updates"></a>Définir l’ordre d’exécution des mises à jour
 La définition de l’ordre d’exécution des mises à jour définit l’ordre des insertions individuelles, des mises à jour et des suppressions nécessaires à l’enregistrement de toutes les données modifiées dans toutes les tables d’un jeu de données. Lorsque la mise à jour hiérarchique est activée, les insertions sont effectuées en premier, puis mises à jour, puis supprimées. L' `TableAdapterManager` fournit une propriété `UpdateOrder` qui peut être définie pour effectuer d’abord des mises à jour, puis des insertions, puis des suppressions.

> [!NOTE]
> Il est important de comprendre que l’ordre de mise à jour est compris. Autrement dit, lorsque des mises à jour sont effectuées, les insertions, puis les suppressions sont effectuées pour toutes les tables du DataSet.

 Pour définir la propriété `UpdateOrder`, après avoir fait glisser des éléments depuis la [fenêtre sources de données](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) vers un formulaire, sélectionnez l' `TableAdapterManager` dans la barre d’état des composants, puis définissez la propriété `UpdateOrder` dans la fenêtre **Propriétés** . Pour plus d’informations, consultez [procédure : définition de l’ordre lors de l’exécution d’une mise à jour hiérarchique](https://msdn.microsoft.com/library/a0734935-78dd-4c0b-80d7-5e7925789c83).

## <a name="create-a-backup-copy-of-a-dataset-before-performing-a-hierarchical-update"></a>Créer une copie de sauvegarde d’un jeu de données avant d’effectuer une mise à jour hiérarchique
 Lorsque vous enregistrez des données (en appelant la méthode `TableAdapterManager.UpdateAll()`), le `TableAdapterManager` tente de mettre à jour les données de chaque table dans une transaction unique. Si une partie de la mise à jour d’une table échoue, toute la transaction est restaurée. Dans la plupart des cas, la restauration rétablit l’état d’origine de votre application.

 Toutefois, il peut arriver que vous souhaitiez restaurer le jeu de données à partir de la copie de sauvegarde. Cela peut se produire par exemple lorsque vous utilisez des valeurs d’incrémentation automatique. Par exemple, si une opération d’enregistrement échoue, les valeurs d’incrémentation automatique ne sont pas réinitialisées dans le jeu de données et le jeu de données continue à créer des valeurs à incrémentation automatique. Cela laisse un écart de numérotation qui peut ne pas être acceptable dans votre application. Dans les situations où il s’agit d’un problème, le `TableAdapterManager` fournit une propriété `BackupDataSetBeforeUpdate` qui remplace le DataSet existant par une copie de sauvegarde en cas d’échec de la transaction.

> [!NOTE]
> La copie de sauvegarde est uniquement en mémoire pendant l’exécution de la méthode `TableAdapterManager.UpdateAll`. Par conséquent, il n’existe aucun accès par programme à ce jeu de données de sauvegarde, car il remplace le jeu de données d’origine ou est hors de portée dès que l’exécution de la méthode `TableAdapterManager.UpdateAll` se termine.

## <a name="modify-the-generated-save-code-to-perform-the-hierarchical-update"></a>Modifier le code d’enregistrement généré pour effectuer la mise à jour hiérarchique
 Enregistrez les modifications des tables de données associées du dataset dans la base de données en appelant la méthode `TableAdapterManager.UpdateAll` et en passant le nom du dataset contenant les tables associées. Par exemple, exécutez la méthode `TableAdapterManager.UpdateAll(NorthwindDataset)` pour envoyer les mises à jour de toutes les tables de NorthwindDataset à la base de données principale.

 Une fois que vous avez déposé des éléments provenant de la fenêtre **Sources de données**, du code est ajouté automatiquement à l’événement `Form_Load` pour remplir chaque table (les méthodes `TableAdapter.Fill`). Du code est également ajouté à l’événement Click du bouton **Enregistrer** du <xref:System.Windows.Forms.BindingNavigator> pour enregistrer les données du dataset dans la base de données (la méthode `TableAdapterManager.UpdateAll`).

 Le code d'enregistrement généré contient également une ligne de code qui appelle la méthode `CustomersBindingSource.EndEdit`. Plus spécifiquement, il appelle la méthode <xref:System.Windows.Forms.BindingSource.EndEdit%2A> du premier <xref:System.Windows.Forms.BindingSource>that ajouté au formulaire. En d’autres termes, ce code est généré uniquement pour la première table déplacée de la fenêtre **sources de données** vers le formulaire. L'appel de <xref:System.Windows.Forms.BindingSource.EndEdit%2A> valide toutes les modifications en cours de tous les contrôles liés aux données modifiés. Par conséquent, si un contrôle lié aux données a encore le focus et que vous cliquez sur le bouton **Enregistrer**, toutes les modifications en attente dans ce contrôle sont validées avant l’enregistrement réel (la méthode `TableAdapterManager.UpdateAll`).

> [!NOTE]
> Le Concepteur de DataSet ajoute uniquement le code `BindingSource.EndEdit` pour la première table qui est déplacée dans le formulaire. Par conséquent, vous devez ajouter une ligne de code pour appeler la méthode `BindingSource.EndEdit` pour chaque table associée dans le formulaire. Dans cette procédure pas à pas, cela signifie que vous devez ajouter un appel à la méthode `OrdersBindingSource.EndEdit`.

#### <a name="to-update-the-code-to-commit-changes-to-the-related-tables-before-saving"></a>Pour mettre à jour le code afin de valider les modifications des tables associées avant l'enregistrement

1. Double-cliquez sur le bouton **Enregistrer** du <xref:System.Windows.Forms.BindingNavigator> pour ouvrir **Form1** dans l’éditeur de code.

2. Ajoutez une ligne de code pour appeler la méthode `OrdersBindingSource.EndEdit` après la ligne appelant la méthode `CustomersBindingSource.EndEdit`. Le code de l’événement Click du bouton **Enregistrer** doit ressembler à ce qui suit :

    [!code-csharp[VSProDataOrcasHierarchicalUpdate#1](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasHierarchicalUpdate/CS/Form1.cs#1)]
    [!code-vb[VSProDataOrcasHierarchicalUpdate#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasHierarchicalUpdate/VB/Form1.vb#1)]

   Outre la validation des modifications d'une table enfant associée avant l'enregistrement des données dans une base de données, vous devez aussi peut-être valider les enregistrements parents récemment créés avant d'ajouter de nouveaux enregistrement enfants à un dataset. En d'autres termes, vous devez peut-être ajouter le nouvel enregistrement parent (Customer) au dataset avant que les contraintes de clé étrangère ne permettent d'ajouter de nouveaux enregistrements enfants (Orders) au dataset. Pour ce faire, vous pouvez utiliser l'événement `BindingSource.AddingNew` enfant.

> [!NOTE]
> La validation de nouveaux enregistrements parents dépend du type de contrôle utilisé pour la liaison à votre source de données. Dans cette procédure pas à pas, vous utilisez des contrôles individuels pour effectuer une liaison à la table parente. Cela nécessite que le code supplémentaire valide le nouvel enregistrement parent. Si les enregistrements parents étaient affichés à la place dans un contrôle de liaison complexe comme le <xref:System.Windows.Forms.DataGridView>, cet appel de <xref:System.Windows.Forms.BindingSource.EndEdit%2A> supplémentaire pour l’enregistrement parent n’est pas nécessaire. En effet, la fonctionnalité sous-jacente de liaison aux données du contrôle gère la validation des nouveaux enregistrements.

#### <a name="to-add-code-to-commit-parent-records-in-the-dataset-before-adding-new-child-records"></a>Pour ajouter du code afin de valider les enregistrements parents dans le dataset avant d’ajouter de nouveaux enregistrements enfants

1. Créez un gestionnaire d'événements pour l'événement `OrdersBindingSource.AddingNew`.

    - Ouvrez **Form1** en mode conception, sélectionnez **OrdersBindingSource** dans la barre d’état des composants, sélectionnez **événements** dans la fenêtre **Propriétés** , puis double-cliquez sur l’événement **AddingNew** .

2. Ajoutez une ligne de code au gestionnaire d’événements qui appelle la méthode `CustomersBindingSource.EndEdit`. Le code du gestionnaire d'événements `OrdersBindingSource_AddingNew` doit ressembler à ce qui suit :

     [!code-csharp[VSProDataOrcasHierarchicalUpdate#2](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasHierarchicalUpdate/CS/Form1.cs#2)]
     [!code-vb[VSProDataOrcasHierarchicalUpdate#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasHierarchicalUpdate/VB/Form1.vb#2)]

## <a name="tableadaptermanager-reference"></a>Référence TableAdapterManager
 Par défaut, une classe `TableAdapterManager` est générée lorsque vous créez un DataSet qui contient des tables associées. Pour empêcher la génération de la classe, remplacez la valeur de la propriété `Hierarchical Update` du jeu de données par false. Quand vous faites glisser une table qui a une relation sur l’aire de conception d’un Windows Form ou d’une page WPF, Visual Studio déclare une variable membre de la classe. Si vous n’utilisez pas DataBinding, vous devez déclarer la variable manuellement.

 La classe `TableAdapterManager` ne fait pas partie du [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Par conséquent, vous ne pouvez pas le Rechercher dans la documentation. Il est créé au moment du design dans le cadre du processus de création du jeu de données.

 Voici les méthodes et les propriétés fréquemment utilisées de la classe `TableAdapterManager` :

|Membre|Description|
|------------|-----------------|
|Méthode `UpdateAll`|Enregistre toutes les données de toutes les tables de données.|
|Propriété`BackUpDataSetBeforeUpdate`|Détermine si une copie de sauvegarde du DataSet doit être créée avant l’exécution de la méthode `TableAdapterManager.UpdateAll`. Expression.|
|propriété `TableAdapter` *TableName*|Représente un `TableAdapter`. Le `TableAdapterManager` généré contient une propriété pour chaque `TableAdapter` qu’il gère. Par exemple, un jeu de données avec une table Customers et Orders est généré avec un `TableAdapterManager` qui contient des propriétés `CustomersTableAdapter` et `OrdersTableAdapter`.|
|Propriété`UpdateOrder`|Contrôle l’ordre des commandes INSERT, Update et DELETE individuelles. Définissez cette valeur sur l’une des valeurs de l’énumération `TableAdapterManager.UpdateOrderOption`.<br /><br /> Par défaut, le `UpdateOrder` est défini sur **InsertUpdateDelete**. Cela signifie que les insertions, les mises à jour, puis les suppressions sont effectuées pour toutes les tables du DataSet. Pour plus d’informations, consultez [procédure : définition de l’ordre lors de l’exécution d’une mise à jour hiérarchique](https://msdn.microsoft.com/library/a0734935-78dd-4c0b-80d7-5e7925789c83).|

## <a name="see-also"></a>Voir aussi
 [Enregistrer les données dans la base de données](../data-tools/save-data-back-to-the-database.md)
