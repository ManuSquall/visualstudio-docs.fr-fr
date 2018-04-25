---
title: Enregistrer des données dans la base de données
ms.date: 11/04/2016
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 4116a06ff57ae6793c7f80abea2464767b33c3bf
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="save-data-back-to-the-database"></a>Enregistrer des données dans la base de données
Le dataset est une copie en mémoire des données. Si vous modifiez ces données, il est recommandé d’enregistrer ces modifications dans la base de données. Vous faire de trois manières :

-   En appelant une des méthodes de mise à jour d’un TableAdapter

-   En appelant une des méthodes DBDirect du TableAdapter

-   En appelant la méthode UpdateAll TableAdapterManager qui Visual Studio génère automatiquement lorsque le jeu de données contient des tables qui sont associées à d’autres tables dans le jeu de données

Lorsque vous données liez des tables de jeu de données aux contrôles sur une page Windows Form ou XAML, l’architecture de liaison de données effectue tout le travail pour vous.

Si vous êtes familiarisé avec les TableAdapters, vous pouvez accéder directement à une des rubriques suivantes :

|Rubrique|Description|
|-----------|-----------------|
|[Guide pratique pour insérer de nouveaux enregistrements dans une base de données](../data-tools/insert-new-records-into-a-database.md)|Comment effectuer des mises à jour et l’insère à l’aide d’objets TableAdapters ou une commande|
|[Guide pratique pour mettre à jour les données à l’aide d’un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)|Comment effectuer des mises à jour avec des TableAdapters|
|[Mise à jour hiérarchique](../data-tools/hierarchical-update.md)|Comment effectuer des mises à jour à partir d’un jeu de données de deux ou plusieurs tables connexes|
|[Gérer une exception d’accès concurrentiel](../data-tools/handle-a-concurrency-exception.md)|La gestion des exceptions lorsque deux utilisateurs tentent de modifier les mêmes données dans une base de données en même temps|
|[Comment : enregistrer des données à l’aide d’une transaction](../data-tools/save-data-by-using-a-transaction.md)|Comment enregistrer les données dans une transaction à l’aide de l’espace de noms System.Transactions et un objet de TransactionScope|
|[Procédure pas à pas : enregistrer des données dans une transaction](../data-tools/save-data-in-a-transaction.md)|Procédure pas à pas qui crée une application Windows Forms pour illustrer l’enregistrement de données à une base de données à l’intérieur d’une transaction|
|[Enregistrer des données dans une base de données (plusieurs tables)](../data-tools/save-data-to-a-database-multiple-tables.md)|Comment modifier les enregistrements et enregistrer les modifications dans plusieurs tables à la base de données|
|[Guide pratique pour enregistrer les données d’un objet dans une base de données](../data-tools/save-data-from-an-object-to-a-database.md)|Comment transmettre des données à partir d’un objet qui n’est pas dans un jeu de données à une base de données à l’aide d’une méthode DbDirect du TableAdapter|
|[Enregistrer des données avec les méthodes DBDirect du TableAdapter](../data-tools/save-data-with-the-tableadapter-dbdirect-methods.md)|Comment utiliser le TableAdapter à envoyer des requêtes SQL directement à la base de données|
|[Enregistrer un dataset au format XML](../data-tools/save-a-dataset-as-xml.md)|Comment enregistrer un jeu de données à un document XML|

## <a name="two-stage-updates"></a>Mises à jour des deux étapes
 Mise à jour d’une source de données est un processus en deux étapes. La première étape consiste à mettre à jour le jeu de données avec nouveaux enregistrements, enregistrements modifiés ou enregistrements supprimés. Si votre application envoie jamais ces modifications à la source de données, puis vous avez terminé la mise à jour.

 Si vous envoyez les modifications apportées à la base de données, une deuxième étape est requise. Si vous n’utilisez pas de contrôles liés aux données, vous devez appeler manuellement la méthode de mise à jour de la même TableAdapter (ou adaptateur de données) que vous avez utilisé pour remplir le dataset. Toutefois, vous pouvez également utiliser différents adaptateurs, par exemple, pour déplacer des données à partir d’une source de données à un autre ou pour mettre à jour de plusieurs sources de données. Si vous n’utilisez pas de liaison de données et enregistrez les modifications pour les tables associées, vous devez manuellement instancier une variable de la classe TableAdapterManager généré automatiquement, puis appeler sa méthode UdpateAll.

 ![Mises à jour du jeu de données Visual Basic](../data-tools/media/vbdatasetupdates.gif "vbDatasetUpdates") deux étapes mettre à jour les processus et le rôle de DataRowVersion dans une mise à jour réussie

 Un dataset contient des collections de tables qui contiennent des collections de lignes. Si vous envisagez de mettre à jour une source de données sous-jacente ultérieurement, vous devez utiliser les méthodes de la propriété DataTable.DataRowCollection lors de l’ajout ou la suppression de lignes. Ces méthodes effectuent le suivi des modifications de mise à jour de la source de données que nécessaire. Si vous appelez la collection RemoveAt sur la propriété de lignes, la suppression ne sont pas être communiquée en retour à la base de données.

## <a name="merge-datasets"></a>Fusionner les jeux de données
 Vous pouvez mettre à jour le contenu d’un dataset en *la fusion* avec un autre dataset. Cela implique la copie le contenu d’un *source* dataset dans le jeu de données appelant (appelé le *cible* jeu de données). Lorsque vous fusionnez des jeux de données, les nouveaux enregistrements dans le jeu de données source sont ajoutées au jeu de données cible. En outre, des colonnes supplémentaires dans le jeu de données source sont ajoutées au jeu de données cible. La fusion de jeux de données est utile lorsque vous disposez d’un jeu de données local et que vous obtenez un second jeu de données à partir d’une autre application. Il est également utile lorsque vous obtenez un second jeu de données à partir d’un composant comme un service web XML, ou lorsque vous avez besoin intégrer des données provenant de plusieurs datasets.

 Lors de la fusion de jeux de données, vous pouvez passer un argument booléen (`preserveChanges`) qui indique le <xref:System.Data.DataSet.Merge%2A> méthode s’il faut conserver les modifications existantes dans le jeu de données cible. Étant donné que les jeux de données conserver plusieurs versions d’enregistrements, il est important de garder à l’esprit que plusieurs versions des enregistrements sont en cours de fusion. Le tableau suivant montre comment un enregistrement dans les deux jeux de données est fusionné :

|DataRowVersion|Groupe de données cible|Jeu de données source|
|--------------------|--------------------|--------------------|
|D'origine|James Wilson|James C. Wilson|
|Actuel|Jim Wilson|James C. Wilson|

 Appel de la <xref:System.Data.DataSet.Merge%2A> méthode sur le tableau précédent avec `preserveChanges=false targetDataset.Merge(sourceDataset)` donne le résultat suivant :

|DataRowVersion|Groupe de données cible|Jeu de données source|
|--------------------|--------------------|--------------------|
|D'origine|James C. Wilson|James C. Wilson|
|Actuel|James C. Wilson|James C. Wilson|

 Appel de la <xref:System.Data.DataSet.Merge%2A> méthode avec `preserveChanges = true targetDataset.Merge(sourceDataset, true)` donne le résultat suivant :

|DataRowVersion|Groupe de données cible|Jeu de données source|
|--------------------|--------------------|--------------------|
|D'origine|James C. Wilson|James C. Wilson|
|Actuel|Jim Wilson|James C. Wilson|

> [!CAUTION]
>  Dans le `preserveChanges = true` scénario, si le <xref:System.Data.DataSet.RejectChanges%2A> méthode est appelée sur un enregistrement dans le jeu de données cible, puis il revient aux données d’origine à partir de la *source* jeu de données. Cela signifie que si vous essayez de mettre à jour de la source de données d’origine avec le jeu de données cible, il ne peut pas être en mesure de trouver la ligne d’origine pour mettre à jour. Vous pouvez empêcher une violation d’accès concurrentiel en remplissant un autre jeu de données avec les enregistrements mis à jour à partir de la source de données, puis exécutez une fusion pour empêcher une violation d’accès concurrentiel. (Une violation d’accès concurrentiel se produit lorsqu’un autre utilisateur modifie un enregistrement dans la source de données une fois que le dataset est rempli.)

## <a name="update-constraints"></a>Contraintes de mise à jour
 Pour apporter des modifications à une ligne de données existante, ajouter ou mettre à jour des données dans les colonnes individuelles. Si le jeu de données contient des contraintes (telles que les clés étrangères ou des contraintes non nullable), il est possible que l’enregistrement peut être temporairement dans un état d’erreur que vous mettez à jour. Autrement dit, il peut être dans un état d’erreur après avoir terminé la mise à jour d’une colonne, mais avant de passer à la suivante.

 Pour empêcher les violations de contrainte prématurées, vous pouvez interrompre temporairement les contraintes de mise à jour. Cela a deux objectifs :

-   Il empêche une erreur ne soit levée lorsque vous avez terminé la mise à jour d’une colonne, mais n’ont pas commencé la mise à jour d’un autre.

-   Il empêche la mise à jour de certaine événements ne soient pas déclenchés (les événements sont souvent utilisés pour la validation).

> [!NOTE]
>  Dans les Windows Forms, l’architecture de liaison de données qui est intégrée à la grille de données interrompt la contrainte de vérification jusqu'à ce que le focus se déplace hors d’une ligne, il est inutile d’appeler explicitement la <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A>, ou <xref:System.Data.DataRow.CancelEdit%2A> méthodes.

 Les contraintes sont automatiquement désactivées lorsque la <xref:System.Data.DataSet.Merge%2A> méthode est appelée sur un jeu de données. Lorsque la fusion est terminée, s’il existe des contraintes de dataset qui ne peut pas être activé, un <xref:System.Data.ConstraintException> est levée. Dans ce cas, le <xref:System.Data.DataSet.EnforceConstraints%2A> est définie sur `false,` et toutes les violations de contrainte doivent être résolues avant de réinitialiser le <xref:System.Data.DataSet.EnforceConstraints%2A> propriété `true`.

 Après avoir effectué une mise à jour, vous pouvez réactiver la vérification des contraintes, ce qui active de nouveau les événements de mise à jour et les déclenche également.

 Pour plus d’informations sur la suspension d’événements, consultez [désactiver les contraintes pendant le remplissage d’un dataset](../data-tools/turn-off-constraints-while-filling-a-dataset.md).

## <a name="dataset-update-errors"></a>Erreurs de mise à jour de jeu de données
 Lorsque vous mettez à jour un enregistrement dans un jeu de données, il existe un risque d’une erreur. Par exemple, vous pouvez par inadvertance écrire des données d’un type incorrect à une colonne, ou les données qui sont trop longues ou qui a un autre problème d’intégrité. Ou vous pouvez avoir des contrôles de validation de spécifiques à l’application qui peuvent déclencher des erreurs personnalisées lors de n’importe quelle étape d’un événement de mise à jour. Pour plus d’informations, consultez [valider des données dans les jeux de données](../data-tools/validate-data-in-datasets.md).

## <a name="maintaining-information-about-changes"></a>Gérer les informations sur les modifications
 Pour plus d’informations sur les modifications dans un jeu de données sont conservées de deux manières : le fait de marquer les lignes qui indiquent qu’ils ont été modifiés (<xref:System.Data.DataRow.RowState%2A>) et en conservant plusieurs copies d’un enregistrement (<xref:System.Data.DataRowVersion>). À l’aide de ces informations, le processus peuvent déterminer ce qui a changé dans le jeu de données et peuvent envoyer des mises à jour appropriées à la source de données.

### <a name="rowstate-property"></a>Propriété RowState
 Le <xref:System.Data.DataRow.RowState%2A> propriété d’un <xref:System.Data.DataRow> objet est une valeur qui fournit des informations sur l’état d’une ligne particulière de données.

 Le tableau suivant détaille les valeurs possibles de la <xref:System.Data.DataRowState> énumération :

|Valeur DataRowState|Description|
|------------------------|-----------------|
|<xref:System.Data.DataRowState.Added>|La ligne a été ajoutée comme un élément à un <xref:System.Data.DataRowCollection>. (Une ligne dans cet état n’a pas une version d’origine correspondante puisqu’elle n’existait pas lors de la dernière <xref:System.Data.DataRow.AcceptChanges%2A> méthode a été appelée).|
|<xref:System.Data.DataRowState.Deleted>|La ligne a été supprimée à l’aide de la <xref:System.Data.DataRow.Delete%2A> d’un <xref:System.Data.DataRow> objet.|
|<xref:System.Data.DataRowState.Detached>|La ligne a été créée, mais elle ne fait pas partie de n’importe quel <xref:System.Data.DataRowCollection>. A <xref:System.Data.DataRow> objet est dans cet état immédiatement après sa création, avant qu’il a été ajouté à une collection et une fois qu’il a été supprimé d’une collection.|
|<xref:System.Data.DataRowState.Modified>|Une valeur de colonne dans la ligne a changé d’une certaine façon.|
|<xref:System.Data.DataRowState.Unchanged>|La ligne n’a pas changé depuis <xref:System.Data.DataRow.AcceptChanges%2A> dernier appel.|

### <a name="datarowversion-enumeration"></a>DataRowVersion (énumération)
Jeux de données conserver plusieurs versions d’enregistrements. Le <xref:System.Data.DataRowVersion> champs peuvent être utilisés lors de la récupération de la valeur trouvée dans un <xref:System.Data.DataRow> à l’aide de la <xref:System.Data.DataRow.Item%2A> propriété ou le <xref:System.Data.DataRow.GetChildRows%2A> méthode de la <xref:System.Data.DataRow> objet.

Le tableau suivant détaille les valeurs possibles de la <xref:System.Data.DataRowVersion> énumération :

|Valeur DataRowVersion|Description|
|--------------------------|-----------------|
|<xref:System.Data.DataRowVersion.Current>|La version actuelle d’un enregistrement contient toutes les modifications qui ont été effectuées sur l’enregistrement depuis la dernière <xref:System.Data.DataRow.AcceptChanges%2A> a été appelée. Si la ligne a été supprimée, il n’existe aucune version actuelle.|
|<xref:System.Data.DataRowVersion.Default>|La valeur par défaut d’un enregistrement, tel que défini par la source de schéma ou les données du jeu de données.|
|<xref:System.Data.DataRowVersion.Original>|La version d’origine d’un enregistrement est une copie de l’enregistrement comme c’était que les dernier enregistrement des modifications ont été validées dans le jeu de données. En pratique, il s’agit généralement la version d’un enregistrement en lecture à partir d’une source de données.|
|<xref:System.Data.DataRowVersion.Proposed>|La version proposée d’un enregistrement qui est disponible temporairement au cours d’une mise à jour, autrement dit, entre le moment où vous avez appelé la <xref:System.Data.DataRow.BeginEdit%2A> (méthode) et le <xref:System.Data.DataRow.EndEdit%2A> (méthode). Vous en général accéder à la version proposée d’un enregistrement dans un gestionnaire pour un événement tel que <xref:System.Data.DataTable.RowChanging>. Appel de la <xref:System.Data.DataRow.CancelEdit%2A> méthode annule les modifications et supprime la version proposée de la ligne de données.|

 Les versions d’origine et actuelle sont utiles lorsque les informations de mise à jour sont transmises à une source de données. En général, lorsqu’une mise à jour est envoyée à la source de données, les nouvelles informations de la base de données sont la version actuelle d’un enregistrement. Pour plus d’informations à partir de la version d’origine sont utilisés pour rechercher l’enregistrement à mettre à jour.

 Par exemple, dans le cas où la clé primaire d’un enregistrement est modifiée, vous devez permet de rechercher l’enregistrement approprié dans la source de données pour mettre à jour les modifications. Si aucune version d’origine n’existe, l’enregistrement serait très probablement être ajouté à la source de données résultant dans un enregistrement supplémentaire inutile, mais dans un enregistrement est incorrect ou obsolète. Les deux versions sont également utilisées dans le contrôle d’accès concurrentiel. Vous pouvez comparer la version d’origine par rapport à un enregistrement dans la source de données pour déterminer si l’enregistrement a changé depuis son chargement dans le jeu de données.

 La version proposée est utile lorsque vous avez besoin effectuer la validation avant d’apporter réellement des modifications au jeu de données.

 Même si les enregistrements ont été modifiés, il ne sont pas toujours des versions d’origine ou en cours de cette ligne. Lorsque vous insérez une nouvelle ligne dans la table, il n’existe aucune version d’origine, seule une version en cours. De même, si vous supprimez une ligne en appelant la table `Delete` (méthode), il existe une version d’origine, mais aucune version actuelle.

 Vous pouvez tester pour voir s’il existe une version spécifique d’un enregistrement en interrogeant une ligne de données <xref:System.Data.DataRow.HasVersion%2A> (méthode). Vous pouvez accéder à des versions d’un enregistrement en passant une <xref:System.Data.DataRowVersion> valeur d’énumération comme un argument facultatif lorsque vous demandez la valeur d’une colonne.

## <a name="getting-changed-records"></a>Mise en route des enregistrements modifiés
 Il est courant ne pas de mettre à jour tous les enregistrements dans un jeu de données. Par exemple, un utilisateur peut utiliser avec un Windows Form <xref:System.Windows.Forms.DataGridView> contrôle qui affiche le nombre d’enregistrements. Toutefois, l’utilisateur peut mettre à jour que quelques enregistrements, supprimez l’un et insérer un nouveau. Les tables de données et des jeux de données fournissent une méthode (`GetChanges`) pour retourner uniquement les lignes qui ont été modifiés.

 Vous pouvez créer des sous-ensembles d’enregistrements modifiés à l’aide de la `GetChanges` de la table de données (méthode) (<xref:System.Data.DataTable.GetChanges%2A>) ou du jeu de données (<xref:System.Data.DataSet.GetChanges%2A>) lui-même. Si vous appelez la méthode pour la table de données, il retourne une copie de la table contenant uniquement les enregistrements modifiés. De même, si vous appelez la méthode sur le jeu de données, vous obtenez un nouveau dataset avec uniquement les enregistrements modifiés.

 `GetChanges` Retourne tous les enregistrements modifiés par lui-même. En revanche, en la passant souhaité <xref:System.Data.DataRowState> en tant que paramètre à la `GetChanges` (méthode), vous pouvez spécifier le sous-ensemble d’enregistrements modifiés souhaité : nouvellement ajouté des enregistrements, enregistrements marqués pour suppression, les enregistrements détachés et enregistrements modifiés.

 Obtention d’un sous-ensemble des enregistrements modifiés est utile lorsque vous souhaitez envoyer des enregistrements à un autre composant pour traitement. Au lieu d’envoyer l’ensemble du dataset, vous pouvez réduire la charge de la communication avec l’autre composant en récupérant uniquement les enregistrements dont il a besoin.

## <a name="committing-changes-in-the-dataset"></a>Validation des modifications dans le jeu de données
 Lorsque des modifications sont apportées dans le dataset, le <xref:System.Data.DataRow.RowState%2A> propriété des lignes modifiées est définie. Les versions d’origine et actuelle des enregistrements sont établies, gérées et mises à disposition par le <xref:System.Data.DataRowView.RowVersion%2A> propriété. Les métadonnées sont stockées dans les propriétés de ces lignes modifiées sont nécessaires pour envoyer les mises à jour appropriées à la source de données.

 Si les modifications reflètent l’état actuel de la source de données, vous n’avez plus besoin de conserver ces informations. Il existe deux fois lorsque le jeu de données et sa source sont synchronisés :

-   Immédiatement après le chargement des informations dans le jeu de données, telles que lorsque vous lisez des données à partir de la source.

-   Après l’envoi des modifications à partir du dataset à la source de données (mais pas avant, car vous perdez les informations de modification qui sont nécessaire pour envoyer les modifications à la base de données).

Vous pouvez valider les modifications en attente pour le jeu de données en appelant le <xref:System.Data.DataSet.AcceptChanges%2A> (méthode). En règle générale, <xref:System.Data.DataSet.AcceptChanges%2A> est appelée aux heures suivantes :

-   Après avoir chargé le jeu de données. Si vous chargez un jeu de données en appelant d’un TableAdapter `Fill` méthode, puis l’adaptateur valide automatiquement les modifications pour vous. Toutefois, si vous chargez un jeu de données en y fusionnant un autre jeu de données, vous devez valider les modifications manuellement.

    > [!NOTE]
    >  Vous pouvez empêcher l’adaptateur de valider automatiquement les modifications lorsque vous appelez le `Fill` méthode en définissant le `AcceptChangesDuringFill` propriété de l’adaptateur à `false`. Si elle est définie sur `false`, puis le <xref:System.Data.DataRow.RowState%2A> de chaque ligne est insérée lors du remplissage est définie sur <xref:System.Data.DataRowState.Added>.

-   Une fois que vous envoyez des modifications du jeu de données à un autre processus, comme un service Web XML.

    > [!CAUTION]
    >  Validation de la modification de cette manière efface toutes les informations de modification. Ne pas valider les modifications tant qu’après avoir terminent effectue des opérations qui nécessitent votre application de savoir quelles modifications ont été apportées dans le jeu de données.

Cette méthode effectue les opérations suivantes :

-   Écrit le <xref:System.Data.DataRowVersion.Current> version d’un enregistrement dans son <xref:System.Data.DataRowVersion.Original> version et remplace la version d’origine.

-   Supprime toutes les lignes où la <xref:System.Data.DataRow.RowState%2A> est définie sur <xref:System.Data.DataRowState.Deleted>.

-   Définit le <xref:System.Data.DataRow.RowState%2A> propriété d’un enregistrement à <xref:System.Data.DataRowState.Unchanged>.

Le <xref:System.Data.DataSet.AcceptChanges%2A> méthode est disponible à trois niveaux. Vous pouvez l’appeler sur un <xref:System.Data.DataRow> objet à des validations change pour simplement cette ligne. Vous pouvez également l’appeler sur un <xref:System.Data.DataTable> objet à valider toutes les lignes dans une table. Enfin, vous pouvez l’appeler sur le <xref:System.Data.DataSet> objet à valider toutes les modifications en attente dans tous les enregistrements de toutes les tables du dataset.

Le tableau suivant décrit les modifications qui sont validées en fonction de ce que la méthode est appelée sur l’objet.

|Méthode|Résultat|
|------------|------------|
|<xref:System.Data.DataRow.AcceptChanges%2A?displayProperty=fullName>|Les modifications sont validées uniquement sur la ligne spécifique.|
|<xref:System.Data.DataTable.AcceptChanges%2A?displayProperty=fullName>|Les modifications sont validées dans toutes les lignes de la table.|
|<xref:System.Data.DataSet.AcceptChanges%2A?displayProperty=fullName>|Les modifications sont validées dans toutes les lignes de toutes les tables du dataset.|

> [!NOTE]
>  Si vous chargez un jeu de données en appelant d’un TableAdapter `Fill` (méthode), il est inutile d’accepter explicitement les modifications. Par défaut, le `Fill` les appels de méthode le `AcceptChanges` méthode une fois celle-ci terminée le remplissage de la table de données.

 Une méthode associée, <xref:System.Data.DataSet.RejectChanges%2A>, annule les modifications en copiant le <xref:System.Data.DataRowVersion.Original> version dans le <xref:System.Data.DataRowVersion.Current> version d’enregistrements. Il définit également la <xref:System.Data.DataRow.RowState%2A> de chaque enregistrement à <xref:System.Data.DataRowState.Unchanged>.

## <a name="data-validation"></a>Validation des données
 Afin de vérifier que les données dans votre application respecte les exigences des processus, il est passé à, vous devez souvent ajouter la validation. Cela peut impliquer la vérification que l’entrée d’utilisateur dans un formulaire est correcte, validation des données qui sont envoyées à votre application par une autre application, ou même vérification que les informations qui sont calculées dans votre composant se trouve dans des limites de votre source de données et les exigences de l’application.

 Vous pouvez valider les données de plusieurs manières :

-   Dans la couche métier, en ajoutant du code à votre application pour valider les données. Le jeu de données est un emplacement pour ce faire. Le jeu de données fournit des avantages de la validation de serveur principal, comme la possibilité de valider les modifications qu’une modifiant des valeurs de colonne et de ligne. Pour plus d’informations, consultez [valider des données dans les jeux de données](../data-tools/validate-data-in-datasets.md).

-   Dans la couche de présentation, en ajoutant la validation aux formulaires. Pour plus d’informations, consultez [Validation d’entrée d’utilisateur dans les Windows Forms](/dotnet/framework/winforms/user-input-validation-in-windows-forms).

-   Dans les données back-end, par envoi de données à la source de données, par exemple, la base de données et en l’autorisant à accepter ou refuser les données. Si vous travaillez avec une base de données qui a des fonctionnalités évoluées de validation des données et en fournissant des informations d’erreur, cela peut être une approche pratique, car vous pouvez valider les données, quel que soit la provenance. Toutefois, cette approche ne peut pas prendre en compte les exigences de validation spécifique à l’application. En outre, la source de données valider des données peut entraîner de nombreux allers-retours vers la source de données, en fonction de la façon dont votre application facilite la résolution des erreurs de validation déclenchées par le serveur principal.

    > [!IMPORTANT]
    >  Lors de l’utilisation des commandes de données avec un <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> propriété a la valeur <xref:System.Data.CommandType.Text>, soigneusement vérifier les informations qui sont envoyées à partir d’un client avant de le transmettre à votre base de données. Les utilisateurs malveillants peuvent tenter d’envoyer (injecter) des instructions SQL modifiées ou supplémentaires dans le but d’obtenir un accès non autorisé ou d’endommager la base de données. Avant de transférer une entrée utilisateur vers une base de données, vérifiez toujours que les informations sont valides. Il est recommandé de toujours utiliser des requêtes paramétrées ou des procédures stockées lorsque cela est possible.

## <a name="transmitting-updates-to-the-data-source"></a>Transmettre les mises à jour à la source de données
Une fois que les modifications ont été apportées dans un jeu de données, vous pouvez transmettre les modifications apportées à une source de données. En règle générale, cela en appelant le `Update` méthode d’un TableAdapter (ou adaptateur de données). La méthode parcourt chaque enregistrement dans une table de données détermine quel type de mise à jour est nécessaire (update, insert ou delete), le cas échéant, puis exécute la commande appropriée.

 En guise d’illustration de la façon dont les mises à jour sont effectuées, supposons que votre application utilise un jeu de données qui contient une table de données unique. L’application extrait deux lignes de la base de données. Après la récupération, la table de données en mémoire ressemble à ceci :

```
(RowState)     CustomerID   Name             Status
(Unchanged)    c200         Robert Lyon      Good
(Unchanged)    c400         Nancy Buchanan    Pending
```

 Votre application change le statut de Nancy Buchanan « Préféré ». Suite à cette modification, la valeur de la <xref:System.Data.DataRow.RowState%2A> propriété pour cette ligne passe de <xref:System.Data.DataRowState.Unchanged> à <xref:System.Data.DataRowState.Modified>. La valeur de la <xref:System.Data.DataRow.RowState%2A> propriété pour la première ligne reste <xref:System.Data.DataRowState.Unchanged>. La table de données ressemble maintenant à ceci :

```
(RowState)     CustomerID   Name             Status
(Unchanged)    c200         Robert Lyon      Good
(Modified)     c400         Nancy Buchanan    Preferred
```

 Votre application maintenant appelle la `Update` méthode pour transmettre le jeu de données à la base de données. La méthode inspecte chaque ligne à son tour. Pour la première ligne, la méthode ne transmet aucun instruction SQL à la base de données, car cette ligne n’a pas changé depuis qu’elle a été extraite à l’origine à partir de la base de données.

 Pour la deuxième ligne, la `Update` méthode automatiquement appelle la commande de données correct et la transmet à la base de données. La syntaxe spécifique de l’instruction SQL varie selon le dialecte SQL pris en charge par le magasin de données sous-jacent. Mais les caractéristiques suivantes de l’instruction SQL transmise sont dignes d’intérêt :

-   L’instruction SQL transmise est une instruction de mise à jour. L’adaptateur sache qu’il peut pour utiliser une instruction UPDATE, car la valeur de la <xref:System.Data.DataRow.RowState%2A> propriété est <xref:System.Data.DataRowState.Modified>.

-   L’instruction SQL transmise comprend une clause WHERE indiquant que la cible de l’instruction UPDATE est la ligne où `CustomerID = 'c400'`. Cette partie de l’instruction SELECT distingue la ligne cible des autres, car le `CustomerID` est la clé primaire de la table cible. Les informations de la clause WHERE est dérivée de la version d’origine de l’enregistrement (`DataRowVersion.Original`), au cas où les valeurs qui sont requises pour identifier la ligne ont été modifiés.

-   L’instruction SQL transmise comprend la clause SET pour définir les nouvelles valeurs des colonnes modifiées.

    > [!NOTE]
    > Si le TableAdapter `UpdateCommand` propriété a été définie pour le nom d’une procédure stockée, l’adaptateur ne construit pas une instruction SQL. Au lieu de cela, il appelle la procédure stockée avec les paramètres passés dans appropriés.

## <a name="passing-parameters"></a>Passage de paramètres
 Vous utilisez généralement des paramètres pour passer les valeurs pour les enregistrements qui vont être mis à jour dans la base de données.  Lorsque du TableAdapter `Update` méthode exécute une instruction UPDATE, elle doit remplir les valeurs de paramètre. Ces valeurs sont obtenues à partir de la `Parameters` collection pour la commande de données appropriée, dans ce cas, le `UpdateCommand` objet dans le TableAdapter.

 Si vous avez utilisé les outils Visual Studio pour générer un adaptateur de données, le `UpdateCommand` objet contient une collection de paramètres correspondant à chaque espace réservé de paramètre dans l’instruction.

 Le <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A?displayProperty=fullName> la propriété de chaque paramètre pointe vers une colonne dans la table de données. Par exemple, le `SourceColumn` propriété pour le `au_id` et `Original_au_id` paramètres est définie sur la colonne dans la table de données contenant l’id d’auteur. Lorsque l’adaptateur `Update` exécution de la méthode, il lit l’auteur de colonne d’id de l’enregistrement est mis à jour et remplit les valeurs dans l’instruction.

 Dans une instruction UPDATE, vous devez spécifier les nouvelles valeurs (celles qui sont écrits dans l’enregistrement) ainsi que les anciennes valeurs (de sorte que l’enregistrement peut se trouver dans la base de données). Il existe deux paramètres pour chaque valeur : un pour la clause SET et un autre pour la clause WHERE. Les deux paramètres lisent les données à partir de l’enregistrement est mis à jour, mais ils obtiennent des versions différentes de la valeur de colonne en fonction du paramètre <xref:System.Data.SqlClient.SqlParameter.SourceVersion> propriété. Le paramètre de la clause SET obtient la version actuelle, et le paramètre de la clause WHERE obtient la version d’origine.

> [!NOTE]
> Vous pouvez également définir des valeurs le `Parameters` collection vous-même dans le code que vous effectuez en général dans un gestionnaire d’événements pour l’adaptateur de données <xref:System.Data.DataTable.RowChanging> événement.

## <a name="see-also"></a>Voir aussi

- [Outils de dataset dans Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Créer et configurer des TableAdapters](create-and-configure-tableadapters.md)
- [Guide pratique pour mettre à jour les données à l’aide d’un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)
- [Lier des contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Validation des données](validate-data-in-datasets.md)
- [Enregistrer des données](../data-tools/saving-data.md)