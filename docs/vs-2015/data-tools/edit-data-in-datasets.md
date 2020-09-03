---
title: Modifier des données dans des jeux de données | Microsoft Docs
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
- datasets [Visual Basic], editing data
- data [Visual Studio], editing in datasets
ms.assetid: 50d5c580-fbf7-408f-be70-e63ac4f4d0eb
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 699ee9b6e7a68c6a79f7f7dac526127206e8aa42
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672403"
---
# <a name="edit-data-in-datasets"></a>Modifier des données dans des datasets
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez modifier des données dans des tables de données de la même façon que vous modifiez les données d’une table dans une base de données. Le processus peut inclure l’insertion, la mise à jour et la suppression d’enregistrements dans la table. Dans un formulaire lié aux données, vous pouvez spécifier les champs modifiables par l’utilisateur. Dans ce cas, l’infrastructure de liaison de données gère l’ensemble du suivi des modifications afin que les modifications puissent être renvoyées ultérieurement à la base de données. Si vous apportez par programmation des modifications aux données et que vous envisagez de les envoyer à la base de données, vous devez utiliser les objets et méthodes qui effectuent le suivi des modifications pour vous.

 En plus de modifier les données réelles, vous pouvez également interroger un <xref:System.Data.DataTable> pour retourner des lignes de données spécifiques. Par exemple, vous pouvez interroger des lignes individuelles, des versions spécifiques de lignes (originales et proposées), des lignes qui ont été modifiées ou des lignes qui contiennent des erreurs.

## <a name="to-edit-rows-in-a-dataset"></a>Pour modifier des lignes dans un DataSet
 Pour modifier une ligne existante dans un <xref:System.Data.DataTable> , vous devez rechercher le <xref:System.Data.DataRow> que vous souhaitez modifier, puis affecter les valeurs mises à jour aux colonnes souhaitées.

 Si vous ne connaissez pas l’index de la ligne que vous souhaitez modifier, utilisez la `FindBy` méthode pour effectuer une recherche à l’aide de la clé primaire :

 [!code-csharp[VbRaddataEditing#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#3)]
 [!code-vb[VbRaddataEditing#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#3)]

 Si vous connaissez l’index de ligne, vous pouvez accéder aux lignes et les modifier comme suit :

 [!code-csharp[VbRaddataEditing#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#5)]
 [!code-vb[VbRaddataEditing#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#5)]

## <a name="to-insert-new-rows-into-a-dataset"></a>Pour insérer de nouvelles lignes dans un jeu de données
 Les applications qui utilisent des contrôles liés aux données ajoutent généralement de nouveaux enregistrements par le biais du bouton **Ajouter un nouveau** sur un [contrôle BindingNavigator](https://msdn.microsoft.com/library/18c1e2a5-9834-40d3-9b2e-2b545e4e769e).

 Pour ajouter manuellement de nouveaux enregistrements à un DataSet, créez une nouvelle ligne de données en appelant la méthode sur le DataTable. Ajoutez ensuite la ligne à la <xref:System.Data.DataRow> collection ( <xref:System.Data.DataTable.Rows%2A> ) du <xref:System.Data.DataTable> :

 [!code-csharp[VbRaddataEditing#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#1)]
 [!code-vb[VbRaddataEditing#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#1)]

 Afin de conserver les informations dont le DataSet a besoin pour envoyer des mises à jour à la source de données, utilisez la <xref:System.Data.DataRow.Delete%2A> méthode pour supprimer des lignes dans une table de données. Par exemple, si votre application utilise un TableAdapter (ou <xref:System.Data.Common.DataAdapter> ), la méthode du TableAdapter `Update` supprime les lignes de la base de données qui ont un <xref:System.Data.DataRow.RowState%2A> de <xref:System.Data.DataRowState> .

 Si votre application n’a pas besoin d’envoyer des mises à jour à une source de données, il est possible de supprimer des enregistrements en accédant directement à la collection de lignes de données ( <xref:System.Data.DataRowCollection.Remove%2A> ).

#### <a name="to-delete-records-from-a-data-table"></a>Pour supprimer des enregistrements d’une table de données

- Appelez la <xref:System.Data.DataRow.Delete%2A> méthode d’un <xref:System.Data.DataRow> .

     Cette méthode ne supprime pas physiquement l’enregistrement. Au lieu de cela, il marque l’enregistrement pour suppression.

    > [!NOTE]
    > Si vous obtenez la propriété Count d’un <xref:System.Data.DataRowCollection> , le nombre résultant comprend les enregistrements qui ont été marqués pour suppression. Pour obtenir un nombre précis d’enregistrements qui ne sont pas marqués pour suppression, vous pouvez parcourir la collection en examinant la <xref:System.Data.DataRow.RowState%2A> propriété de chaque enregistrement. (Les enregistrements marqués pour suppression ont un <xref:System.Data.DataRow.RowState%2A> de <xref:System.Data.DataRowState> .) Vous pouvez également créer une vue de données d’un DataSet qui filtre en fonction de l’état de la ligne et obtenir la propriété Count à partir de là.

     L’exemple suivant montre comment appeler la <xref:System.Data.DataRow.Delete%2A> méthode pour marquer la première ligne de la `Customers` table comme supprimée :

     [!code-csharp[VbRaddataEditing#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#8)]
     [!code-vb[VbRaddataEditing#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#8)]

## <a name="determine-if-there-are-changed-rows"></a>Déterminer si des lignes ont été modifiées
 Lorsque des modifications sont apportées aux enregistrements d’un jeu de données, les informations relatives à ces modifications sont stockées jusqu’à ce que vous les validiez. Vous validez les modifications lorsque vous appelez la `AcceptChanges` méthode d’un DataSet ou d’une table de données, ou lorsque vous appelez la `Update` méthode d’un TableAdapter ou d’un adaptateur de données.

 Les modifications sont suivies de deux façons dans chaque ligne de données :

- Chaque ligne de données contient des informations relatives à celle-ci <xref:System.Data.DataRow.RowState%2A> (par exemple,,, <xref:System.Data.DataRowState> <xref:System.Data.DataRowState> <xref:System.Data.DataRowState> ou <xref:System.Data.DataRowState> ).

- Chaque ligne de données modifiée contient plusieurs versions de cette ligne ( <xref:System.Data.DataRowVersion> ), la version d’origine (avant les modifications) et la version actuelle (après modification). Pendant la période pendant laquelle une modification est en attente (l’heure à laquelle vous pouvez répondre à l' <xref:System.Data.DataTable.RowChanging> événement), une troisième version (la version proposée) est également disponible.

  La <xref:System.Data.DataSet.HasChanges%2A> méthode d’un DataSet retourne `true` si des modifications ont été apportées au jeu de données. Après avoir déterminé que des lignes modifiées existent, vous pouvez appeler la `GetChanges` méthode d’un <xref:System.Data.DataSet> ou <xref:System.Data.DataTable> pour retourner un ensemble de lignes modifiées. Pour plus d’informations, consultez [Comment : récupérer des lignes modifiées](https://msdn.microsoft.com/library/6ff0cbd0-5253-48e7-888a-144d56c2e0a9).

#### <a name="to-determine-if-changes-have-been-made-to-any-rows"></a>Pour déterminer si des modifications ont été apportées à des lignes

- Appelez la <xref:System.Data.DataSet.HasChanges%2A> méthode d’un jeu de données pour rechercher les lignes modifiées.

     L’exemple suivant montre comment vérifier la valeur de retour de la <xref:System.Data.DataSet.HasChanges%2A> méthode pour déterminer s’il existe des lignes modifiées dans un dataset nommé `NorthwindDataset1` :

     [!code-csharp[VbRaddataEditing#12](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#12)]
     [!code-vb[VbRaddataEditing#12](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#12)]

## <a name="determine-the-type-of-changes"></a>Déterminer le type de modifications
 Vous pouvez également vérifier le type de modifications apportées à un DataSet en passant une valeur de l' <xref:System.Data.DataRowState> énumération à la <xref:System.Data.DataSet.HasChanges%2A> méthode.

#### <a name="to-determine-what-type-of-changes-have-been-made-to-a-row"></a>Pour déterminer le type de modifications apportées à une ligne

- Transmettez une <xref:System.Data.DataRowState> valeur à la <xref:System.Data.DataSet.HasChanges%2A> méthode.

     L’exemple suivant montre comment vérifier un dataset nommé `NorthwindDataset1` pour déterminer si de nouvelles lignes y ont été ajoutées :

     [!code-csharp[VbRaddataEditing#13](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#13)]
     [!code-vb[VbRaddataEditing#13](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#13)]

## <a name="to-locate-rows-that-have-errors"></a>Pour rechercher les lignes qui contiennent des erreurs
 Lorsque vous utilisez des colonnes et des lignes de données individuelles, vous pouvez rencontrer des erreurs. Vous pouvez vérifier la `HasErrors` propriété pour déterminer si des erreurs existent dans un <xref:System.Data.DataSet> , <xref:System.Data.DataTable> ou <xref:System.Data.DataRow> .

1. Vérifiez la `HasErrors` propriété pour voir s’il existe des erreurs dans le jeu de données.

2. Si la `HasErrors` propriété a la valeur `true` , effectuez une itération dans les collections de tables, puis sur les lignes, pour rechercher la ligne contenant l’erreur.

     [!code-csharp[VbRaddataEditing#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#23)]
     [!code-vb[VbRaddataEditing#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#23)]
