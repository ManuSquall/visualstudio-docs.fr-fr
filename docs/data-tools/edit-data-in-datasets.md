---
title: Modifier des données dans des datasets
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- datasets [Visual Basic], editing data
- data [Visual Studio], editing in datasets
ms.assetid: 50d5c580-fbf7-408f-be70-e63ac4f4d0eb
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 08cf47310c9743d1071dd46a30e5c04372ca5cb6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54996725"
---
# <a name="edit-data-in-datasets"></a>Modifier des données dans des datasets
Pour modifier les données dans les tables de données de la même manière que vous modifiez les données dans une table dans une base de données. Le processus peut inclure insertion, la mise à jour et suppression d’enregistrements dans la table. Dans un formulaire lié aux données, vous pouvez spécifier quels champs sont modifiables par l’utilisateur. Dans ce cas, l’infrastructure de liaison de données gère tout le suivi des modifications afin que les modifications puissent être envoyées à la base de données plus tard. Si vous apportez des modifications par programme aux données, et que vous avez l’intention de renvoyer ces modifications à la base de données, vous devez utiliser les objets et les méthodes qui effectuent le suivi des modifications pour vous.

Outre la modification des données réelles, vous pouvez également interroger un <xref:System.Data.DataTable> pour retourner les lignes de données spécifiques. Par exemple, vous est possible d’interroger pour des lignes individuelles, des versions spécifiques de lignes (d’origine et proposés), les lignes qui ont été modifiés ou les lignes qui contiennent des erreurs.

## <a name="to-edit-rows-in-a-dataset"></a>Pour modifier les lignes dans un jeu de données
Pour modifier une ligne existante dans un <xref:System.Data.DataTable>, vous devez localiser la <xref:System.Data.DataRow> vous souhaitez modifier, puis assigner les valeurs mises à jour pour les colonnes de votre choix.

Si vous ne connaissez pas l’index de la ligne que vous souhaitez modifier, utilisez le `FindBy` méthode de recherche par la clé primaire :

[!code-csharp[VbRaddataEditing#3](../data-tools/codesnippet/CSharp/edit-data-in-datasets_1.cs)]
[!code-vb[VbRaddataEditing#3](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_1.vb)]

Si vous connaissez l’index de ligne, vous pouvez accéder à et modifie les lignes comme suit :

[!code-csharp[VbRaddataEditing#5](../data-tools/codesnippet/CSharp/edit-data-in-datasets_2.cs)]
[!code-vb[VbRaddataEditing#5](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_2.vb)]

## <a name="to-insert-new-rows-into-a-dataset"></a>Pour insérer de nouvelles lignes dans un jeu de données
Les applications qui utilisent des contrôles liés aux données généralement ajoutent de nouveaux enregistrements via le **Ajouter nouveau** bouton sur un [contrôle BindingNavigator](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms).

Pour ajouter manuellement des enregistrements à un jeu de données, créez une nouvelle ligne de données en appelant la méthode sur la table de données. Ensuite, ajoutez la ligne à la <xref:System.Data.DataRow> collection (<xref:System.Data.DataTable.Rows%2A>) de la <xref:System.Data.DataTable>:

[!code-csharp[VbRaddataEditing#1](../data-tools/codesnippet/CSharp/edit-data-in-datasets_3.cs)]
[!code-vb[VbRaddataEditing#1](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_3.vb)]

Pour conserver les informations que le jeu de données a besoin envoyer des mises à jour à la source de données, utilisez la <xref:System.Data.DataRow.Delete%2A> méthode pour supprimer des lignes dans une table de données. Par exemple, si votre application utilise un TableAdapter (ou <xref:System.Data.Common.DataAdapter>), le TableAdapter `Update` méthode supprime des lignes dans la base de données qui ont un <xref:System.Data.DataRow.RowState%2A> de <xref:System.Data.DataRowState.Deleted>.

Si votre application n’a pas besoin envoyer des mises à jour à la source de données, il est possible de supprimer des enregistrements en accédant directement à la collection de lignes de données (<xref:System.Data.DataRowCollection.Remove%2A>).

#### <a name="to-delete-records-from-a-data-table"></a>Pour supprimer des enregistrements à partir d’une table de données

-   Appelez le <xref:System.Data.DataRow.Delete%2A> méthode d’un <xref:System.Data.DataRow>.

     Cette méthode ne supprime pas physiquement l’enregistrement. Au lieu de cela, il les marque pour suppression.

    > [!NOTE]
    >  Si vous obtenez la propriété count d’un <xref:System.Data.DataRowCollection>, le résultat inclut les enregistrements qui ont été marqués pour suppression. Pour obtenir un décompte précis d’enregistrements qui ne sont pas marqués pour suppression, vous pouvez parcourir la collection et rechercher la <xref:System.Data.DataRow.RowState%2A> propriété de chaque enregistrement. (Les enregistrements marqués pour suppression ont un <xref:System.Data.DataRow.RowState%2A> de <xref:System.Data.DataRowState.Deleted>.) Vous pouvez également créer une vue de données d’un dataset filtres basés sur l’état de la ligne et obtenir la propriété count à partir de là.

L’exemple suivant montre comment appeler le <xref:System.Data.DataRow.Delete%2A> méthode pour marquer la première ligne dans le `Customers` comme étant supprimé de la table :

[!code-csharp[VbRaddataEditing#8](../data-tools/codesnippet/CSharp/edit-data-in-datasets_4.cs)]
[!code-vb[VbRaddataEditing#8](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_4.vb)]

## <a name="determine-if-there-are-changed-rows"></a>Déterminer s’il existe des lignes modifiées
Lorsque des modifications sont apportées aux enregistrements dans un jeu de données, les informations relatives à ces modifications sont stockées jusqu'à ce que vous les validiez. Vous validez les modifications lorsque vous appelez le `AcceptChanges` (méthode) d’une table de données ou le jeu de données, ou lorsque vous appelez le `Update` méthode d’un adaptateur de données ou du TableAdapter.

Modifications sont suivies de deux façons dans chaque ligne de données :

-   Chaque ligne de données contient des informations relatives à son <xref:System.Data.DataRow.RowState%2A> (par exemple, <xref:System.Data.DataRowState.Added>, <xref:System.Data.DataRowState.Modified>, <xref:System.Data.DataRowState.Deleted>, ou <xref:System.Data.DataRowState.Unchanged>).

-   Chaque ligne de données modifiée contient plusieurs versions de cette ligne (<xref:System.Data.DataRowVersion>), la version d’origine (avant modification) et la version actuelle (après les modifications). Pendant la période quand une modification est en attente (le temps lorsque vous pouvez répondre à la <xref:System.Data.DataTable.RowChanging> événement), une troisième version — la version proposée — est également disponible.

Le <xref:System.Data.DataSet.HasChanges%2A> retourne de la méthode d’un dataset `true` si les modifications ont été apportées dans le jeu de données. Après avoir déterminé qu’il existe des lignes modifiées, vous pouvez appeler la `GetChanges` méthode d’un <xref:System.Data.DataSet> ou <xref:System.Data.DataTable> pour retourner un jeu de lignes modifiées.

#### <a name="to-determine-if-changes-have-been-made-to-any-rows"></a>Pour déterminer si des modifications ont été apportées aux lignes

-   Appelez le <xref:System.Data.DataSet.HasChanges%2A> méthode d’un dataset pour vérifier les lignes modifiées.

L’exemple suivant montre comment vérifier la valeur de retour à partir de la <xref:System.Data.DataSet.HasChanges%2A> méthode pour détecter s’il existe des lignes modifiées dans un dataset nommé `NorthwindDataset1`:

[!code-csharp[VbRaddataEditing#12](../data-tools/codesnippet/CSharp/edit-data-in-datasets_5.cs)]
[!code-vb[VbRaddataEditing#12](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_5.vb)]

## <a name="determine-the-type-of-changes"></a>Déterminer le type de modifications
Vous pouvez également vérifier pour voir quel type de modifications ont été apportées dans un jeu de données en transmettant une valeur à partir de la <xref:System.Data.DataRowState> énumération à la <xref:System.Data.DataSet.HasChanges%2A> (méthode).

#### <a name="to-determine-what-type-of-changes-have-been-made-to-a-row"></a>Pour déterminer le type de modifications ont été apportées à une ligne

-   Passer un <xref:System.Data.DataRowState> valeur pour le <xref:System.Data.DataSet.HasChanges%2A> (méthode).

L’exemple suivant montre comment vérifier un dataset nommé `NorthwindDataset1` pour déterminer si toutes les nouvelles lignes ont été ajoutés à celui-ci :

[!code-csharp[VbRaddataEditing#13](../data-tools/codesnippet/CSharp/edit-data-in-datasets_6.cs)]
[!code-vb[VbRaddataEditing#13](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_6.vb)]

## <a name="to-locate-rows-that-have-errors"></a>Pour rechercher des lignes qui contiennent des erreurs
Lorsque vous travaillez avec des colonnes et des lignes de données, vous pouvez rencontrer des erreurs. Vous pouvez vérifier le `HasErrors` propriété afin de déterminer si des erreurs existent dans un <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, ou <xref:System.Data.DataRow>.

1.  Vérifier le `HasErrors` propriété pour voir s’il existe des erreurs dans le jeu de données.

2.  Si le `HasErrors` propriété est `true`, effectuer une itération dans les collections de tables, puis le via les lignes, pour rechercher la ligne avec l’erreur.

[!code-csharp[VbRaddataEditing#23](../data-tools/codesnippet/CSharp/edit-data-in-datasets_7.cs)]
[!code-vb[VbRaddataEditing#23](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_7.vb)]

## <a name="see-also"></a>Voir aussi

- [Outils de dataset dans Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)