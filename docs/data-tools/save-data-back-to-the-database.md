---
title: Enregistrer les données dans la base de données
description: Utilisez les outils de DataSet pour réenregistrer les données dans la base de données. Le jeu de données est une copie en mémoire des données qui doit être enregistrée dans la base de données si elle est modifiée.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- datasets [Visual Basic], validating data
- data validation, datasets
- data [Visual Studio], saving
- row version
- updating datasets, constraints
- datasets [Visual Basic], about datasets
- datasets [Visual Basic], merging
- updates, constraints in datasets
- saving data, about saving data
- datasets [Visual Basic], constraints
- TableAdapters
ms.assetid: afe6cb8a-dc6a-428b-b07b-903ac02c890b
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 77f6a837fcc88c7154978e8031b17febaa0fcd39
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436053"
---
# <a name="save-data-back-to-the-database"></a>Enregistrer les données dans la base de données

Le jeu de données est une copie en mémoire des données. Si vous modifiez ces données, il est conseillé d’enregistrer ces modifications dans la base de données. Pour ce faire, vous disposez de trois méthodes :

- En appelant l’une des `Update` méthodes d’un TableAdapter

- En appelant l’une des `DBDirect` méthodes du TableAdapter

- En appelant la `UpdateAll` méthode sur le TableAdapterManager que Visual Studio génère pour vous lorsque le DataSet contient des tables qui sont liées à d’autres tables dans le DataSet

Lorsque vous liez des données à des tables de DataSet à des contrôles sur un Windows Form ou une page XAML, l’architecture de liaison de données effectue tout le travail pour vous.

Si vous êtes familiarisé avec les TableAdapters, vous pouvez accéder directement à l’une des rubriques suivantes :

|Rubrique|Description|
|-----------|-----------------|
|[Insérer de nouveaux enregistrements dans une base de données](../data-tools/insert-new-records-into-a-database.md)|Comment effectuer des mises à jour et des insertions à l’aide de TableAdapters ou d’objets de commande|
|[Mettre à jour les données à l’aide d’un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)|Comment effectuer des mises à jour avec des TableAdapters|
|[Mise à jour hiérarchique](../data-tools/hierarchical-update.md)|Comment effectuer des mises à jour à partir d’un jeu de données avec au moins deux tables associées|
|[Gérer une exception d’accès concurrentiel](../data-tools/handle-a-concurrency-exception.md)|Comment gérer les exceptions quand deux utilisateurs essaient de modifier les mêmes données dans une base de données en même temps|
|[Comment : enregistrer des données à l’aide d’une transaction](../data-tools/save-data-by-using-a-transaction.md)|Comment enregistrer des données dans une transaction à l’aide du système. Espace de noms transactions et objet TransactionScope|
|[Enregistrer des données dans une transaction](../data-tools/save-data-in-a-transaction.md)|Procédure pas à pas qui crée une application Windows Forms pour illustrer l’enregistrement de données dans une base de données à l’intérieur d’une transaction|
|[Enregistrer des données dans une base de données (plusieurs tables)](../data-tools/save-data-to-a-database-multiple-tables.md)|Comment modifier des enregistrements et enregistrer les modifications apportées à plusieurs tables dans la base de données|
|[Enregistrer les données d’un objet dans une base de données](../data-tools/save-data-from-an-object-to-a-database.md)|Comment passer des données d’un objet qui n’est pas dans un DataSet à une base de données à l’aide d’une méthode DbDirect du TableAdapter|
|[Enregistrer des données avec les méthodes DBDirect du TableAdapter](../data-tools/save-data-with-the-tableadapter-dbdirect-methods.md)|Comment utiliser le TableAdapter pour envoyer des requêtes SQL directement à la base de données|
|[Enregistrer un dataset au format XML](../data-tools/save-a-dataset-as-xml.md)|Comment enregistrer un DataSet dans un document XML|

## <a name="two-stage-updates"></a>Mises à jour en deux étapes

La mise à jour d’une source de données est un processus en deux étapes. La première étape consiste à mettre à jour le jeu de données avec les nouveaux enregistrements, les enregistrements modifiés ou les enregistrements supprimés. Si votre application n’envoie jamais ces modifications à la source de données, vous avez terminé la mise à jour.

Si vous renvoyez les modifications à la base de données, une deuxième étape est requise. Si vous n’utilisez pas de contrôles liés aux données, vous devez appeler manuellement la `Update` méthode du même TableAdapter (ou de l’adaptateur de données) que vous avez utilisé pour remplir le DataSet. Toutefois, vous pouvez également utiliser des adaptateurs différents, par exemple, pour déplacer des données d’une source de données vers une autre ou pour mettre à jour plusieurs sources de données. Si vous n’utilisez pas la liaison de données et que vous enregistrez les modifications pour les tables associées, vous devez instancier manuellement une variable de la classe générée automatiquement `TableAdapterManager` , puis appeler sa `UpdateAll` méthode.

![Diagramme conceptuel des mises à jour de DataSet](../data-tools/media/vbdatasetupdates.gif)

Un DataSet contient des collections de tables, qui contiennent des collections de lignes. Si vous envisagez de mettre à jour une source de données sous-jacente ultérieurement, vous devez utiliser les méthodes sur la `DataTable.DataRowCollection` propriété lors de l’ajout ou de la suppression de lignes. Ces méthodes effectuent le suivi des modifications nécessaire à la mise à jour de la source de données. Si vous appelez la `RemoveAt` collection sur la propriété Rows, la suppression n’est pas renvoyée à la base de données.

## <a name="merge-datasets"></a>Fusionner des datasets

Vous pouvez mettre à jour le contenu d’un DataSet en le *fusionnant* avec un autre jeu de données. Cela implique de copier le contenu d’un jeu de données *source* dans le DataSet appelant (appelé DataSet *cible* ). Lorsque vous fusionnez des jeux de données, les nouveaux enregistrements du jeu de données source sont ajoutés au jeu de données cible. En outre, les colonnes supplémentaires du jeu de données source sont ajoutées au jeu de données cible. La fusion de datasets est utile lorsque vous disposez d’un jeu de données local et que vous recevez un deuxième jeu de données à partir d’une autre application. Elle est également utile lorsque vous recevez un deuxième jeu de données à partir d’un composant, tel qu’un service Web XML, ou lorsque vous avez besoin d’intégrer des données provenant de plusieurs datasets.

Lors de la fusion de datasets, vous pouvez passer un argument booléen ( `preserveChanges` ) qui indique <xref:System.Data.DataSet.Merge%2A> à la méthode s’il faut conserver les modifications existantes dans le DataSet cible. Étant donné que les jeux de données conservent plusieurs versions d’enregistrements, il est important de garder à l’esprit que plusieurs versions des enregistrements sont fusionnées. Le tableau suivant montre comment fusionner un enregistrement dans deux datasets :

|DataRowVersion|Jeu de données cible|Jeu de données source|
| - | - | - |
|Original|James Wilson|James C. Wilson|
|Actuel|Jim Wilson|James C. Wilson|

L’appel de la <xref:System.Data.DataSet.Merge%2A> méthode sur le tableau précédent avec `preserveChanges=false targetDataset.Merge(sourceDataset)` génère les données suivantes :

|DataRowVersion|Jeu de données cible|Jeu de données source|
| - | - | - |
|Original|James C. Wilson|James C. Wilson|
|Actuel|James C. Wilson|James C. Wilson|

L’appel de la <xref:System.Data.DataSet.Merge%2A> méthode avec `preserveChanges = true targetDataset.Merge(sourceDataset, true)` génère les données suivantes :

|DataRowVersion|Jeu de données cible|Jeu de données source|
| - | - | - |
|Original|James C. Wilson|James C. Wilson|
|Actuel|Jim Wilson|James C. Wilson|

> [!CAUTION]
> Dans le `preserveChanges = true` scénario, si la <xref:System.Data.DataSet.RejectChanges%2A> méthode est appelée sur un enregistrement dans le DataSet cible, elle revient aux données d’origine à partir du jeu de données *source* . Cela signifie que si vous essayez de mettre à jour la source de données d’origine avec le DataSet cible, il est possible qu’elle ne puisse pas trouver la ligne d’origine à mettre à jour. Vous pouvez empêcher une violation de l’accès concurrentiel en remplissant un autre DataSet avec les enregistrements mis à jour de la source de données, puis en effectuant une fusion pour empêcher une violation de l’accès concurrentiel. (Une violation d’accès concurrentiel se produit lorsqu’un autre utilisateur modifie un enregistrement dans la source de données après avoir rempli le jeu de données.)

## <a name="update-constraints"></a>Mettre à jour des contraintes

Pour apporter des modifications à une ligne de données existante, ajoutez ou mettez à jour des données dans les colonnes individuelles. Si le DataSet contient des contraintes (telles que des clés étrangères ou des contraintes non Nullable), il est possible que l’enregistrement soit temporairement dans un état d’erreur lors de sa mise à jour. Autrement dit, il peut être dans un état d’erreur une fois que vous avez terminé la mise à jour d’une colonne, mais avant d’accéder à la suivante.

Pour éviter les violations de contrainte prématurées, vous pouvez suspendre temporairement les contraintes de mise à jour. Cela a deux objectifs :

- Elle empêche la levée d’une erreur une fois que vous avez terminé la mise à jour d’une colonne, mais que vous n’avez pas commencé à la mettre à jour.

- Il empêche l’déclenchement de certains événements de mise à jour (événements souvent utilisés pour la validation).

> [!NOTE]
> Dans Windows Forms, l’architecture de liaison de données intégrée au DataGrid interrompt la vérification des contraintes jusqu’à ce que le focus se déplace hors d’une ligne et que vous n’ayez pas à appeler explicitement les <xref:System.Data.DataRow.BeginEdit%2A> <xref:System.Data.DataRow.EndEdit%2A> méthodes, ou <xref:System.Data.DataRow.CancelEdit%2A> .

Les contraintes sont automatiquement désactivées lorsque la <xref:System.Data.DataSet.Merge%2A> méthode est appelée sur un DataSet. Une fois la fusion terminée, si des contraintes sur le DataSet ne peuvent pas être activées, une <xref:System.Data.ConstraintException> est levée. Dans ce cas, la <xref:System.Data.DataSet.EnforceConstraints%2A> propriété a la valeur `false,` et toutes les violations de contrainte doivent être résolues avant de réaffecter la valeur <xref:System.Data.DataSet.EnforceConstraints%2A> à la propriété `true` .

Une fois que vous avez terminé une mise à jour, vous pouvez réactiver la vérification des contraintes, ce qui réactive également les événements de mise à jour et les déclenche.

Pour plus d’informations sur la suspension des événements, consultez [Désactiver les contraintes lors du remplissage d’un jeu de données](../data-tools/turn-off-constraints-while-filling-a-dataset.md).

## <a name="dataset-update-errors"></a>Erreurs de mise à jour du jeu de données

Lorsque vous mettez à jour un enregistrement dans un jeu de données, il existe un risque d’erreur. Par exemple, vous pouvez écrire par inadvertance des données d’un type incorrect dans une colonne, ou des données trop longues, ou des données qui présentent un autre problème d’intégrité. Ou bien, vous pouvez avoir des contrôles de validation spécifiques à l’application qui peuvent déclencher des erreurs personnalisées lors de n’importe quelle étape d’un événement de mise à jour. Pour plus d’informations, consultez [valider des données dans des datasets](../data-tools/validate-data-in-datasets.md).

## <a name="maintain-information-about-changes"></a>Conserver des informations sur les modifications

Les informations sur les modifications apportées à un jeu de données sont conservées de deux façons : en marquant les lignes qui indiquent qu’elles ont changé ( <xref:System.Data.DataRow.RowState%2A> ) et en conservant plusieurs copies d’un enregistrement ( <xref:System.Data.DataRowVersion> ). Grâce à ces informations, les processus peuvent déterminer ce qui a changé dans le jeu de données et peuvent envoyer des mises à jour appropriées à la source de données.

### <a name="rowstate-property"></a>Propriété RowState

La <xref:System.Data.DataRow.RowState%2A> propriété d’un <xref:System.Data.DataRow> objet est une valeur qui fournit des informations sur l’état d’une ligne de données particulière.

Le tableau suivant détaille les valeurs possibles de l' <xref:System.Data.DataRowState> énumération :

|Valeur DataRowState|Description|
| - |-----------------|
|<xref:System.Data.DataRowState.Added>|La ligne a été ajoutée en tant qu’élément à un <xref:System.Data.DataRowCollection> . (Une ligne dans cet État n’a pas de version d’origine correspondante, car elle n’existait pas lorsque la dernière <xref:System.Data.DataRow.AcceptChanges%2A> méthode a été appelée).|
|<xref:System.Data.DataRowState.Deleted>|La ligne a été supprimée à l’aide du <xref:System.Data.DataRow.Delete%2A> d’un <xref:System.Data.DataRow> objet.|
|<xref:System.Data.DataRowState.Detached>|La ligne a été créée, mais n'appartient à aucun <xref:System.Data.DataRowCollection>. Un <xref:System.Data.DataRow> objet est dans cet État immédiatement après qu’il a été créé, avant d’avoir été ajouté à une collection et qu’il a été supprimé d’une collection.|
|<xref:System.Data.DataRowState.Modified>|Une valeur de colonne dans la ligne a été modifiée d’une certaine façon.|
|<xref:System.Data.DataRowState.Unchanged>|La ligne n'a pas été modifiée depuis le dernier appel à <xref:System.Data.DataRow.AcceptChanges%2A>.|

### <a name="datarowversion-enumeration"></a>DataRowVersion (énumération)

Les jeux de données conservent plusieurs versions d’enregistrements. Les <xref:System.Data.DataRowVersion> champs sont utilisés lors de la récupération de la valeur trouvée dans un <xref:System.Data.DataRow> à l’aide de la <xref:System.Data.DataRow.Item%2A> propriété ou <xref:System.Data.DataRow.GetChildRows%2A> de la méthode de l' <xref:System.Data.DataRow> objet.

Le tableau suivant détaille les valeurs possibles de l' <xref:System.Data.DataRowVersion> énumération :

|Valeur DataRowVersion|Description|
| - |-----------------|
|<xref:System.Data.DataRowVersion.Current>|La version actuelle d’un enregistrement contient toutes les modifications qui ont été effectuées sur l’enregistrement depuis l’appel de la dernière fois <xref:System.Data.DataRow.AcceptChanges%2A> . Si la ligne a été supprimée, il n’y a pas de version actuelle.|
|<xref:System.Data.DataRowVersion.Default>|Valeur par défaut d’un enregistrement, telle que définie par le schéma ou la source de données du DataSet.|
|<xref:System.Data.DataRowVersion.Original>|La version d’origine d’un enregistrement est une copie de l’enregistrement telle qu’elle était lors de la dernière validation des modifications dans le jeu de données. En pratique, il s’agit généralement de la version d’un enregistrement lu à partir d’une source de données.|
|<xref:System.Data.DataRowVersion.Proposed>|Version proposée d’un enregistrement qui est disponible temporairement pendant que vous êtes au milieu d’une mise à jour, c’est-à-dire entre l’heure à laquelle vous avez appelé la <xref:System.Data.DataRow.BeginEdit%2A> méthode et la <xref:System.Data.DataRow.EndEdit%2A> méthode. En général, vous accédez à la version proposée d’un enregistrement dans un gestionnaire pour un événement tel que <xref:System.Data.DataTable.RowChanging> . L’appel <xref:System.Data.DataRow.CancelEdit%2A> de la méthode inverse les modifications et supprime la version proposée de la ligne de données.|

Les versions d’origine et actuelle sont utiles lorsque les informations de mise à jour sont transmises à une source de données. En général, lorsqu’une mise à jour est envoyée à la source de données, les nouvelles informations de la base de données se trouvent dans la version actuelle d’un enregistrement. Les informations de la version d’origine sont utilisées pour localiser l’enregistrement à mettre à jour.

Par exemple, dans le cas où la clé primaire d’un enregistrement est modifiée, vous devez disposer d’un moyen de localiser l’enregistrement approprié dans la source de données afin de mettre à jour les modifications. Si aucune version d’origine n’existait, l’enregistrement sera probablement ajouté à la source de données, ce qui entraînerait non seulement un enregistrement supplémentaire indésirable, mais dans un enregistrement inexact et obsolète. Les deux versions sont également utilisées dans le contrôle d’accès concurrentiel. Vous pouvez comparer la version d’origine à un enregistrement de la source de données pour déterminer si l’enregistrement a changé depuis qu’il a été chargé dans le jeu de données.

La version proposée est utile lorsque vous devez effectuer la validation avant de valider les modifications apportées au jeu de données.

Même si les enregistrements ont changé, il n’y a pas toujours d’original ou de versions actuelles de cette ligne. Lorsque vous insérez une nouvelle ligne dans la table, il n’y a pas de version d’origine, uniquement une version actuelle. De même, si vous supprimez une ligne en appelant la méthode de la table `Delete` , il existe une version d’origine, mais pas de version actuelle.

Vous pouvez tester pour déterminer s’il existe une version spécifique d’un enregistrement en interrogeant la méthode d’une ligne de données <xref:System.Data.DataRow.HasVersion%2A> . Vous pouvez accéder à l’une ou l’autre des versions d’un enregistrement en passant une <xref:System.Data.DataRowVersion> valeur d’énumération en tant qu’argument facultatif quand vous demandez la valeur d’une colonne.

## <a name="get-changed-records"></a>Récupérer les enregistrements modifiés

Il est courant de ne pas mettre à jour chaque enregistrement dans un jeu de données. Par exemple, un utilisateur peut travailler avec un contrôle de Windows Forms <xref:System.Windows.Forms.DataGridView> qui affiche de nombreux enregistrements. Toutefois, l’utilisateur ne peut mettre à jour que quelques enregistrements, en supprimer un et en insérer un nouveau. Les datasets et les tables de données fournissent une méthode ( `GetChanges` ) pour retourner uniquement les lignes qui ont été modifiées.

Vous pouvez créer des sous-ensembles d’enregistrements modifiés à l’aide `GetChanges` de la méthode de la table de données ( <xref:System.Data.DataTable.GetChanges%2A> ) ou du jeu de données ( <xref:System.Data.DataSet.GetChanges%2A> ) lui-même. Si vous appelez la méthode pour la table de données, elle retourne une copie de la table avec uniquement les enregistrements modifiés. De même, si vous appelez la méthode sur le DataSet, vous recevez un nouveau jeu de données avec uniquement les enregistrements modifiés.

`GetChanges` retourne tous les enregistrements modifiés. En revanche, en passant le souhaité <xref:System.Data.DataRowState> en tant que paramètre à la `GetChanges` méthode, vous pouvez spécifier le sous-ensemble d’enregistrements modifiés que vous souhaitez : enregistrements récemment ajoutés, enregistrements marqués pour suppression, enregistrements détachés ou enregistrements modifiés.

L’obtention d’un sous-ensemble d’enregistrements modifiés est utile lorsque vous souhaitez envoyer des enregistrements à un autre composant en vue de leur traitement. Au lieu d’envoyer l’ensemble du jeu de données, vous pouvez réduire la surcharge liée à la communication avec l’autre composant en obtenant uniquement les enregistrements dont le composant a besoin.

## <a name="commit-changes-in-the-dataset"></a>Valider les modifications dans le jeu de données

À mesure que des modifications sont apportées dans le jeu de données, la <xref:System.Data.DataRow.RowState%2A> propriété des lignes modifiées est définie. Les versions d’origine et actuelle des enregistrements sont établies, gérées et mises à votre disposition par la <xref:System.Data.DataRowView.RowVersion%2A> propriété. Les métadonnées stockées dans les propriétés de ces lignes modifiées sont nécessaires pour envoyer les mises à jour appropriées à la source de données.

Si les modifications reflètent l’état actuel de la source de données, vous n’avez plus besoin de conserver ces informations. En règle générale, il existe deux fois lorsque le DataSet et sa source sont synchronisés :

- Immédiatement après avoir chargé les informations dans le jeu de données, par exemple lorsque vous lisez des données à partir de la source.

- Après l’envoi des modifications du DataSet à la source de données (mais pas avant, car vous perdrez les informations de modification requises pour envoyer des modifications à la base de données).

Vous pouvez valider les modifications en attente du DataSet en appelant la <xref:System.Data.DataSet.AcceptChanges%2A> méthode. En général, <xref:System.Data.DataSet.AcceptChanges%2A> est appelé aux moments suivants :

- Après avoir chargé le jeu de données. Si vous chargez un DataSet en appelant la méthode d’un TableAdapter `Fill` , l’adaptateur valide automatiquement les modifications pour vous. Toutefois, si vous chargez un DataSet en fusionnant un autre jeu de données dans celui-ci, vous devez valider les modifications manuellement.

    > [!NOTE]
    > Vous pouvez empêcher l’adaptateur de valider automatiquement les modifications lorsque vous appelez la `Fill` méthode en affectant `AcceptChangesDuringFill` à la propriété de l’adaptateur la valeur `false` . Si la valeur est `false` , la <xref:System.Data.DataRow.RowState%2A> valeur de chaque ligne insérée pendant le remplissage est définie sur <xref:System.Data.DataRowState.Added> .

- Après avoir envoyé des modifications de jeu de données à un autre processus, tel qu’un service Web XML.

    > [!CAUTION]
    > La validation de la modification de cette façon efface toutes les informations de modification. Ne validez pas les modifications tant que vous n’avez pas terminé l’exécution des opérations qui requièrent que votre application sache quelles modifications ont été apportées au jeu de données.

Cette méthode effectue les opérations suivantes :

- Écrit la version <xref:System.Data.DataRowVersion.Current> d’un enregistrement dans sa <xref:System.Data.DataRowVersion.Original> version et remplace la version d’origine.

- Supprime toutes les lignes où la <xref:System.Data.DataRow.RowState%2A> propriété a la valeur <xref:System.Data.DataRowState.Deleted> .

- Affecte la valeur <xref:System.Data.DataRow.RowState%2A> à la propriété d’un enregistrement <xref:System.Data.DataRowState.Unchanged> .

La <xref:System.Data.DataSet.AcceptChanges%2A> méthode est disponible à trois niveaux. Vous pouvez l’appeler sur un <xref:System.Data.DataRow> objet pour valider les modifications uniquement pour cette ligne. Vous pouvez également l’appeler sur un <xref:System.Data.DataTable> objet pour valider toutes les lignes d’une table. Enfin, vous pouvez l’appeler sur l' <xref:System.Data.DataSet> objet pour valider toutes les modifications en attente dans tous les enregistrements de toutes les tables du DataSet.

Le tableau suivant décrit les modifications qui sont validées en fonction de l’objet sur lequel la méthode est appelée :

|Méthode|Résultats|
|------------|------------|
|<xref:System.Data.DataRow.AcceptChanges%2A?displayProperty=fullName>|Les modifications sont validées uniquement sur la ligne spécifique.|
|<xref:System.Data.DataTable.AcceptChanges%2A?displayProperty=fullName>|Les modifications sont validées sur toutes les lignes de la table spécifique.|
|<xref:System.Data.DataSet.AcceptChanges%2A?displayProperty=fullName>|Les modifications sont validées sur toutes les lignes de toutes les tables du DataSet.|

> [!NOTE]
> Si vous chargez un DataSet en appelant la méthode d’un TableAdapter `Fill` , vous n’êtes pas obligé d’accepter explicitement les modifications. Par défaut, la `Fill` méthode appelle la `AcceptChanges` méthode une fois que le remplissage de la table de données est terminé.

Une méthode associée, <xref:System.Data.DataSet.RejectChanges%2A> , annule l’effet des modifications en recopiant la <xref:System.Data.DataRowVersion.Original> version dans la <xref:System.Data.DataRowVersion.Current> version des enregistrements. Elle rétablit également le <xref:System.Data.DataRow.RowState%2A> de chaque enregistrement <xref:System.Data.DataRowState.Unchanged> .

## <a name="data-validation"></a>Validation des données

Pour vérifier que les données de votre application remplissent les conditions des processus qu’elle reçoit, vous devez souvent ajouter la validation. Cela peut impliquer de vérifier que l’entrée d’un utilisateur dans un formulaire est correcte, de valider les données envoyées à votre application par une autre application, ou même de vérifier que les informations calculées au sein de votre composant se trouvent dans les contraintes de la source de données et des exigences de votre application.

Vous pouvez valider les données de plusieurs façons :

- Dans la couche métier, ajoutez du code à votre application pour valider les données. Le jeu de données est un emplacement où vous pouvez effectuer cette opération. Le jeu de données présente certains des avantages de la validation du serveur principal, par exemple la possibilité de valider des modifications au fur et à mesure que les valeurs des colonnes et des lignes changent. Pour plus d’informations, consultez [valider des données dans des datasets](../data-tools/validate-data-in-datasets.md).

- Dans la couche de présentation, en ajoutant la validation aux formulaires. Pour plus d’informations, consultez [validation des entrées d’utilisateur dans Windows Forms](/dotnet/framework/winforms/user-input-validation-in-windows-forms).

- Dans le back end de données, en envoyant des données à la source de données (par exemple, la base de données) et en l’autorisant à accepter ou à refuser les données. Si vous travaillez avec une base de données qui dispose de fonctionnalités sophistiquées pour valider les données et fournir des informations sur les erreurs, il peut s’agir d’une approche pratique, car vous pouvez valider les données quel que soit leur origine. Toutefois, cette approche peut ne pas répondre aux exigences de validation spécifiques à l’application. En outre, la validation des données par la source de données peut entraîner de nombreux allers-retours vers la source de données, en fonction de la manière dont votre application facilite la résolution des erreurs de validation déclenchées par le back end.

   > [!IMPORTANT]
   > Lorsque vous utilisez des commandes de données avec une <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> propriété définie sur <xref:System.Data.CommandType.Text> , vérifiez attentivement les informations envoyées à partir d’un client avant de les transmettre à votre base de données. Des utilisateurs malveillants peuvent tenter d’envoyer (injecter) des instructions SQL modifiées ou supplémentaires afin d’accéder à la base de données ou de l’endommager. Avant de transférer une entrée d’utilisateur à une base de données, vérifiez toujours que les informations sont valides. Il est recommandé de toujours utiliser des requêtes paramétrables ou des procédures stockées dans la mesure du possible.

## <a name="transmit-updates-to-the-data-source"></a>Transmettre des mises à jour à la source de données

Une fois les modifications apportées à un jeu de données, vous pouvez transmettre les modifications à une source de données. Le plus souvent, vous le faites en appelant la `Update` méthode d’un TableAdapter (ou d’un adaptateur de données). La méthode parcourt chaque enregistrement d’une table de données, détermine le type de mise à jour requis (mise à jour, insertion ou suppression), le cas échéant, puis exécute la commande appropriée.

Pour illustrer la façon dont les mises à jour sont effectuées, supposez que votre application utilise un jeu de données qui contient une table de données unique. L’application extrait deux lignes de la base de données. Après la récupération, la table de données en mémoire se présente comme suit :

```sql
(RowState)     CustomerID   Name             Status
(Unchanged)    c200         Robert Lyon      Good
(Unchanged)    c400         Nancy Buchanan    Pending
```

Votre application modifie l’état de Nancy Buchanan en « préféré ». Suite à cette modification, la valeur de la <xref:System.Data.DataRow.RowState%2A> propriété pour cette ligne passe de <xref:System.Data.DataRowState.Unchanged> à <xref:System.Data.DataRowState.Modified> . La valeur de la <xref:System.Data.DataRow.RowState%2A> propriété de la première ligne est conservée <xref:System.Data.DataRowState.Unchanged> . La table de données se présente désormais comme suit :

```sql
(RowState)     CustomerID   Name             Status
(Unchanged)    c200         Robert Lyon      Good
(Modified)     c400         Nancy Buchanan    Preferred
```

Votre application appelle désormais la `Update` méthode pour transmettre le DataSet à la base de données. La méthode inspecte chaque ligne à son tour. Pour la première ligne, la méthode ne transmet aucune instruction SQL à la base de données, car cette ligne n’a pas été modifiée depuis qu’elle a été extraite à l’origine de la base de données.

Toutefois, pour la deuxième ligne, la `Update` méthode appelle automatiquement la commande de données correcte et la transmet à la base de données. La syntaxe spécifique de l’instruction SQL dépend du dialecte SQL pris en charge par le magasin de données sous-jacent. Toutefois, les caractéristiques générales suivantes de l’instruction SQL transmise sont intéressantes :

- L’instruction SQL transmise est une instruction UPDATE. L’adaptateur sait qu’il doit utiliser une instruction UPDATE, car la valeur de la <xref:System.Data.DataRow.RowState%2A> propriété est <xref:System.Data.DataRowState.Modified> .

- L’instruction SQL transmise comprend une clause WHERE indiquant que la cible de l’instruction UPDATE correspond à la ligne où `CustomerID = 'c400'` . Cette partie de l’instruction SELECT distingue la ligne cible des autres, car `CustomerID` est la clé primaire de la table cible. Les informations de la clause WHERE sont dérivées de la version d’origine de l’enregistrement ( `DataRowVersion.Original` ), au cas où les valeurs requises pour identifier la ligne ont changé.

- L’instruction SQL transmise comprend la clause SET, afin de définir les nouvelles valeurs des colonnes modifiées.

   > [!NOTE]
   > Si la propriété du TableAdapter `UpdateCommand` a été définie sur le nom d’une procédure stockée, l’adaptateur ne construit pas d’instruction SQL. Au lieu de cela, il appelle la procédure stockée avec les paramètres appropriés passés.

## <a name="pass-parameters"></a>Transmettre des paramètres

En général, vous utilisez des paramètres pour transmettre les valeurs des enregistrements qui vont être mis à jour dans la base de données. Quand la méthode du TableAdapter `Update` exécute une instruction Update, elle doit remplir les valeurs des paramètres. Elle obtient ces valeurs à partir de la `Parameters` collection pour la commande de données appropriée, dans ce cas, l' `UpdateCommand` objet dans le TableAdapter.

Si vous avez utilisé les outils Visual Studio pour générer un adaptateur de données, l' `UpdateCommand` objet contient une collection de paramètres qui correspondent à chaque espace réservé de paramètre dans l’instruction.

La <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A?displayProperty=fullName> propriété de chaque paramètre pointe vers une colonne de la table de données. Par exemple, la `SourceColumn` propriété des `au_id` paramètres et `Original_au_id` est définie sur la colonne de la table de données qui contient l’ID de l’auteur. Lorsque la méthode de l’adaptateur `Update` s’exécute, elle lit la colonne ID de l’auteur à partir de l’enregistrement en cours de mise à jour et remplit les valeurs dans l’instruction.

Dans une instruction UPDATE, vous devez spécifier les nouvelles valeurs (celles qui seront écrites dans l’enregistrement), ainsi que les anciennes valeurs (afin que l’enregistrement puisse se trouver dans la base de données). Par conséquent, il existe deux paramètres pour chaque valeur : un pour la clause SET et un autre pour la clause WHERE. Les deux paramètres lisent les données de l’enregistrement en cours de mise à jour, mais ils obtiennent différentes versions de la valeur de colonne en fonction de la propriété du paramètre <xref:System.Data.SqlClient.SqlParameter.SourceVersion> . Le paramètre de la clause SET obtient la version actuelle et le paramètre de la clause WHERE obtient la version d’origine.

> [!NOTE]
> Vous pouvez également définir vous-même les valeurs de la `Parameters` collection dans le code, ce qui est généralement le cas dans un gestionnaire d’événements pour l’événement de l’adaptateur de données <xref:System.Data.DataTable.RowChanging> .

## <a name="see-also"></a>Voir aussi

- [Outils de dataset dans Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Créer et configurer des TableAdapters](create-and-configure-tableadapters.md)
- [Mettre à jour les données à l’aide d’un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)
- [Lier des contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Valider des données](validate-data-in-datasets.md)
- [Guide pratique pour ajouter, modifier et supprimer des entités (services de données WCF)](/dotnet/framework/data/wcf/how-to-add-modify-and-delete-entities-wcf-data-services)
