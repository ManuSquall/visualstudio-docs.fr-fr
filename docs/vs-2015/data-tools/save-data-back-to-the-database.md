---
title: Enregistrer les données dans la base de données | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
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
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: baddf87e24efc48ea597e44c52abcee5e5bdcfad
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49829638"
---
# <a name="save-data-back-to-the-database"></a>Enregistrer les données dans la base de données
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Le jeu de données est une copie en mémoire des données. Si vous modifiez ces données, il est conseillé d’enregistrer ces modifications dans la base de données. Pour cela de trois manières :  
  
- En appelant une de le `Update` méthodes d’un TableAdapter  
  
- En appelant une des méthodes DBDirect du TableAdapter  
  
- En appelant la méthode UpdateAll sur le `TableAdapterManager` généré par Visual Studio pour vous lorsque le jeu de données contient des tables qui sont liées à d’autres tables dans le jeu de données  
  
  Lors de la lier des données des tables de jeu de données aux contrôles sur une page Windows Form ou XAML, l’architecture de liaison de données fait tout le travail pour vous.  
  
  Si vous êtes familiarisé avec les TableAdapters, vous pouvez passer directement à une des rubriques suivantes :  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Guide pratique pour insérer de nouveaux enregistrements dans une base de données](../data-tools/insert-new-records-into-a-database.md)|Comment effectuer des mises à jour et insertions à l’aide des objets de commande ou des TableAdapters|  
|[Guide pratique pour mettre à jour les données à l’aide d’un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)|Comment effectuer des mises à jour avec les TableAdapters|  
|[Mise à jour hiérarchique](../data-tools/hierarchical-update.md)|Comment effectuer des mises à jour à partir d’un jeu de données avec deux ou plusieurs tables connexes|  
|[Gérer une exception d’accès concurrentiel](../data-tools/handle-a-concurrency-exception.md)|Comment gérer des exceptions lorsque deux utilisateurs tentent de modifier les mêmes données dans une base de données en même temps|  
|[Enregistrer des données à l’aide d’une transaction](../data-tools/save-data-by-using-a-transaction.md)|Comment enregistrer des données dans une transaction à l’aide de l’espace de noms System.Transactions et de l’objet TransactionScope|  
|[Enregistrer des données dans une transaction](../data-tools/save-data-in-a-transaction.md)|Comment enregistrer des données dans une transaction à l’aide de l’espace de noms System.Transactions|  
|[Enregistrer des données dans une base de données (plusieurs tables)](../data-tools/save-data-to-a-database-multiple-tables.md)|Comment modifier les enregistrements et enregistrer les modifications dans plusieurs tables dans la base de données|  
|[Guide pratique pour enregistrer les données d’un objet dans une base de données](../data-tools/save-data-from-an-object-to-a-database.md)|Comment passer des données à partir d’un objet qui n’est pas dans un jeu de données à une base de données à l’aide d’une méthode DbDirect du TableAdapter|  
|[Enregistrer des données avec les méthodes DBDirect du TableAdapter](../data-tools/save-data-with-the-tableadapter-dbdirect-methods.md)|Comment utiliser le TableAdapter pour envoyer des requêtes SQL directement à la base de données|  
|[Enregistrer un dataset au format XML](../data-tools/save-a-dataset-as-xml.md)|Comment enregistrer un jeu de données dans un document XML|  
  
## <a name="two-stage-updates"></a>Mises à jour de deux étapes  
 La mise à jour une source de données est un processus en deux étapes. La première étape consiste à mettre à jour le jeu de données avec les nouveaux enregistrements, enregistrements modifiés ou enregistrements supprimés. Si votre application envoie jamais ces modifications à la source de données, puis vous avez terminé la mise à jour.  
  
 Si vous envoyez les modifications apportées à la base de données, puis une deuxième étape est requise. Si vous n’utilisez pas des contrôles liés aux données, vous devez appeler manuellement la méthode de mise à jour de la même TableAdapter (ou adaptateur de données) que vous avez utilisé pour remplir le jeu de données. Toutefois, vous pouvez également utiliser différents adaptateurs, par exemple, pour déplacer des données à partir d’une source de données vers un autre ou pour mettre à jour de plusieurs sources de données. Si vous n’utilisez pas la liaison de données et enregistrez les modifications pour les tables associées, vous devez instancier manuellement une variable de la classe TableAdapterManager généré automatiquement, puis appelez sa méthode UdpateAll.  
  
 ![Mises à jour du jeu de données de Visual Basic](../data-tools/media/vbdatasetupdates.gif "vbDatasetUpdates")  
Processus de mise à jour des deux étapes et le rôle de DataRowVersion dans une mise à jour réussie  
  
 Un jeu de données contient des collections de tables qui contiennent une collection de lignes. Si vous envisagez de mettre à jour une source de données sous-jacente ultérieurement, vous devez utiliser les méthodes sur la propriété DataTable.DataRowCollection lors de l’ajout ou la suppression de lignes. Ces méthodes effectuent le suivi des modifications qui sont nécessaire pour la mise à jour de la source de données. Si vous appelez la collection RemoveAt sur la propriété de lignes, la suppression ne sont pas communiquée à la base de données.  
  
## <a name="merge-datasets"></a>Fusionner les jeux de données  
 Vous pouvez mettre à jour le contenu d’un jeu de données par *fusion* avec un autre jeu de données. Cela implique la copie le contenu d’un *source* jeu de données dans le jeu de données appelant (appelé le *cible* jeu de données). Lorsque vous fusionnez des jeux de données, les nouveaux enregistrements dans le jeu de données source sont ajoutées au jeu de données cible. En outre, les colonnes supplémentaires dans le jeu de données source sont ajoutées au jeu de données cible. Fusion de jeux de données est utile lorsque vous avez un jeu de données local et vous obtenez un deuxième jeu de données à partir d’une autre application. Il est également utile lorsque vous recevez un deuxième jeu de données à partir d’un composant tel qu’un service web XML, ou lorsque vous avez besoin intégrer des données à partir de plusieurs jeux de données.  
  
 Lors de la fusion des jeux de données, vous pouvez passer un argument booléen (`preserveChanges`) qui indique le <xref:System.Data.DataSet.Merge%2A> méthode s’il faut conserver les modifications existantes dans le jeu de données cible. Étant donné que les jeux de données conserver plusieurs versions d’enregistrements, il est important de garder à l’esprit que plusieurs versions des enregistrements sont en cours de fusion. Le tableau suivant montre comment un enregistrement dans les deux jeux de données est fusionné :  
  
|DataRowVersion|Dataset cible|Jeu de données source|  
|--------------------|--------------------|--------------------|  
|D'origine|James Wilson|James C. Wilson|  
|Actuel|Jim Wilson|James C. Wilson|  
  
 Appel de la <xref:System.Data.DataSet.Merge%2A> méthode sur le tableau précédent avec `preserveChanges=false targetDataset.Merge(sourceDataset)` donne le résultat suivant :  
  
|DataRowVersion|Dataset cible|Jeu de données source|  
|--------------------|--------------------|--------------------|  
|D'origine|James C. Wilson|James C. Wilson|  
|Actuel|James C. Wilson|James C. Wilson|  
  
 Appel de la <xref:System.Data.DataSet.Merge%2A> méthode avec `preserveChanges = true targetDataset.Merge(sourceDataset, true)` donne le résultat suivant :  
  
|DataRowVersion|Dataset cible|Jeu de données source|  
|--------------------|--------------------|--------------------|  
|D'origine|James C. Wilson|James C. Wilson|  
|Actuel|Jim Wilson|James C. Wilson|  
  
> [!CAUTION]
>  Dans le `preserveChanges = true` scénario, si le <xref:System.Data.DataSet.RejectChanges%2A> méthode est appelée sur un enregistrement dans le jeu de données cible, puis il revient aux données d’origine à partir de la *source* jeu de données. Cela signifie que si vous essayez de mettre à jour de la source de données d’origine avec le jeu de données cible, il ne peut pas être en mesure de trouver la ligne d’origine pour mettre à jour. Vous pouvez empêcher une violation d’accès concurrentiel en remplissant un autre jeu de données avec les enregistrements mis à jour à partir de la source de données, puis exécutez une fusion pour éviter une violation d’accès concurrentiel. (Une violation d’accès concurrentiel se produit lorsqu’un autre utilisateur modifie un enregistrement dans la source de données une fois que le jeu de données a été renseigné.)  
  
## <a name="update-constraints"></a>Contraintes de mise à jour  
 Pour apporter des modifications à une ligne de données existante, ajouter ou mettre à jour des données dans les colonnes individuelles. Si le jeu de données contient des contraintes (telles que les clés étrangères ou des contraintes non nullable), il est possible que l’enregistrement soit temporairement dans un état d’erreur quand vous mettez à jour. Autrement dit, il peut être dans un état d’erreur après avoir terminé la mise à jour d’une colonne, mais avant de passer à la suivante.  
  
 Pour empêcher les violations de contrainte prématurées, vous pouvez interrompre temporairement les contraintes de mise à jour. Cela a deux objectifs :  
  
- Il empêche une erreur ne soit levée une fois que vous avez terminé la mise à jour une colonne mais que vous n’avez pas commencé la mise à jour à un autre.  
  
- Il empêche la mise à jour de certains événements ne soient pas déclenchés (les événements sont souvent utilisés pour la validation).  
  
  Après avoir effectué une mise à jour, vous pouvez réactiver la vérification des contraintes, ce qui active les événements de mise à jour de nouveau et déclenche également les.  
  
> [!NOTE]
>  Dans Windows Forms, l’architecture de liaison de données qui est intégrée à la grille de données interrompt la contrainte de vérification jusqu'à ce que le focus se déplace en dehors d’une ligne, et il est inutile d’appeler explicitement la <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A>, ou <xref:System.Data.DataRow.CancelEdit%2A> méthodes.  
  
 Les contraintes sont automatiquement désactivées lorsque le <xref:System.Data.DataSet.Merge%2A> méthode est appelée sur un jeu de données. Lorsque la fusion est terminée, s’il existe des contraintes sur le jeu de données qui ne peut pas être activée, un <xref:System.Data.ConstraintException> est levée. Dans ce cas, le <xref:System.Data.DataSet.EnforceConstraints%2A> propriété est définie sur `false,` et toutes les violations de contrainte doivent être résolues avant de réinitialiser le <xref:System.Data.DataSet.EnforceConstraints%2A> propriété `true`.  
  
 Après avoir effectué une mise à jour, vous pouvez réactiver la vérification des contraintes, ce qui active les événements de mise à jour de nouveau et déclenche également les.  
  
 Pour plus d’informations sur la suspension d’événements, consultez [désactiver les contraintes pendant le remplissage d’un jeu de données](../data-tools/turn-off-constraints-while-filling-a-dataset.md).  
  
## <a name="dataset-update-errors"></a>Erreurs de mise à jour de jeu de données  
 Lorsque vous mettez à jour un enregistrement dans un jeu de données, il est possible d’une erreur. Par exemple, vous pouvez par inadvertance écrire des données d’un type incorrect à une colonne, ou les données qui sont trop longues ou qui a un autre problème d’intégrité. Ou vous pouvez avoir des contrôles de validation de spécifique à l’application qui peuvent déclencher des erreurs personnalisées lors de n’importe quelle étape d’un événement de mise à jour. Pour plus d’informations, consultez [valider des données dans les jeux de données](../data-tools/validate-data-in-datasets.md).  
  
## <a name="maintaining-information-about-changes"></a>Gérer les informations sur les modifications  
 Informations sur les modifications dans un jeu de données sont gérées de deux manières : en marquant les lignes qui indiquent qu’ils ont été modifiés (<xref:System.Data.DataRow.RowState%2A>) et en conservant plusieurs copies d’un enregistrement (<xref:System.Data.DataRowVersion>). À l’aide de ces informations, le processus peuvent déterminer ce qui a changé dans le jeu de données et peuvent envoyer des mises à jour appropriées à la source de données.  
  
### <a name="rowstate-property"></a>Propriété RowState  
 Le <xref:System.Data.DataRow.RowState%2A> propriété d’un <xref:System.Data.DataRow> objet est une valeur qui fournit des informations sur l’état d’une ligne particulière de données.  
  
 Le tableau suivant détaille les valeurs possibles de la <xref:System.Data.DataRowState> énumération :  
  
|Valeur DataRowState|Description|  
|------------------------|-----------------|  
|<xref:System.Data.DataRowState>|La ligne a été ajoutée en tant qu’élément à un <xref:System.Data.DataRowCollection>. (Une ligne dans cet état n’a pas une version d’origine correspondante dans la mesure où il n’existait pas lors de la dernière <xref:System.Data.DataRow.AcceptChanges%2A> méthode a été appelée).|  
|<xref:System.Data.DataRowState>|La ligne a été supprimée à l’aide de la <xref:System.Data.DataRow.Delete%2A> d’un <xref:System.Data.DataRow> objet.|  
|<xref:System.Data.DataRowState>|La ligne a été créée mais ne fait pas partie de n’importe quel <xref:System.Data.DataRowCollection>. Un <xref:System.Data.DataRow> objet est dans cet état immédiatement après sa création, avant qu’il a été ajouté à une collection et après avoir été supprimée à partir d’une collection.|  
|<xref:System.Data.DataRowState>|Une valeur de colonne dans la ligne a changé d’une certaine façon.|  
|<xref:System.Data.DataRowState>|La ligne n’a pas changé depuis <xref:System.Data.DataRow.AcceptChanges%2A> dernier appel.|  
  
### <a name="datarowversion-enumeration"></a>DataRowVersion (énumération)  
 Jeux de données conserver plusieurs versions d’enregistrements. Le <xref:System.Data.DataRowVersion> énumération d’un <xref:System.Data.DataRow> objet est une valeur qui peut être utilisée pour retourner une version spécifique d’un <xref:System.Data.DataRow> objet.  
  
 Le tableau suivant détaille les valeurs possibles de la <xref:System.Data.DataRowVersion> énumération :  
  
|Valeur DataRowVersion|Description|  
|--------------------------|-----------------|  
|<xref:System.Data.DataRowVersion>|La version actuelle d’un enregistrement contient toutes les modifications qui ont été effectuées sur l’enregistrement depuis la dernière fois <xref:System.Data.DataRow.AcceptChanges%2A> a été appelée. Si la ligne a été supprimée, il n’existe aucune version actuelle.|  
|<xref:System.Data.DataRowVersion>|La valeur par défaut d’un enregistrement, tel que défini par la source de schéma ou les données du jeu de données.|  
|<xref:System.Data.DataRowVersion>|La version d’origine d’un enregistrement est une copie de l’enregistrement comme c’était que les dernier enregistrement des modifications ont été validées dans le jeu de données. Dans la pratique, il s’agit généralement la version d’un enregistrement en lecture à partir d’une source de données.|  
|<xref:System.Data.DataRowVersion>|La version proposée d’un enregistrement qui est disponible temporairement pendant que vous êtes au milieu d’une mise à jour, autrement dit, entre le moment où vous avez appelé la <xref:System.Data.DataRow.BeginEdit%2A> (méthode) et le <xref:System.Data.DataRow.EndEdit%2A> (méthode). Vous en général accéder à la version proposée d’un enregistrement dans un gestionnaire pour un événement tel que <xref:System.Data.DataTable.RowChanging>. Appel de la <xref:System.Data.DataRow.CancelEdit%2A> méthode annule les modifications et supprime la version proposée de la ligne de données.|  
  
 Les versions d’origine et actuelles sont utiles lorsque les informations de mise à jour sont transmises à une source de données. En règle générale, lorsqu’une mise à jour est envoyé à la source de données, les nouvelles informations de la base de données sont dans la version actuelle d’un enregistrement. Informations à partir de la version d’origine sont utilisées pour rechercher l’enregistrement à mettre à jour.  
  
 Par exemple, dans un cas où la clé primaire d’un enregistrement est modifiée, vous avez besoin d’un moyen de localiser l’enregistrement correct dans la source de données pour mettre à jour les modifications. Si aucune version d’origine n’existe, l’enregistrement serait probablement être ajouté à la source de données, ce qui entraîne non seulement dans un enregistrement supplémentaire inutile, mais dans un seul enregistrement est inexact et obsolètes. Les deux versions sont également utilisées dans le contrôle d’accès concurrentiel. Vous pouvez comparer la version d’origine par rapport à un enregistrement dans la source de données pour déterminer si l’enregistrement a changé depuis son chargement dans le jeu de données.  
  
 La version proposée est utile lorsque vous avez besoin effectuer la validation avant validation réellement des modifications au jeu de données.  
  
 Même si les enregistrements ont été modifiés, il n'existe pas toujours des versions d’origine ou en cours de cette ligne. Lorsque vous insérez une nouvelle ligne dans la table, il n’existe aucune version d’origine, seule une version actuelle. De même, si vous supprimez une ligne en appelant de la table `Delete` (méthode), il existe une version d’origine, mais aucune version actuelle.  
  
 Vous pouvez tester pour voir si une version spécifique d’un enregistrement existe en interrogeant une ligne de données <xref:System.Data.DataRow.HasVersion%2A> (méthode). Vous pouvez accéder à des versions d’un enregistrement en passant un <xref:System.Data.DataRowVersion> valeur d’énumération comme un argument facultatif lorsque vous demandez la valeur d’une colonne.  
  
## <a name="getting-changed-records"></a>Obtention des enregistrements modifiés  
 Il est une pratique courante ne pas mettre à jour chaque enregistrement dans un jeu de données. Par exemple, un utilisateur peut utiliser un formulaire Windows <xref:System.Windows.Forms.DataGridView> contrôle qui affiche le nombre d’enregistrements. Toutefois, l’utilisateur peut mettre à jour uniquement quelques enregistrements, supprimez l’une et insérer un nouveau. Jeux de données et tables de données fournissent une méthode (`GetChanges`) pour retourner uniquement les lignes qui ont été modifiées.  
  
 Vous pouvez créer des sous-ensembles d’enregistrements modifiés à l’aide de la `GetChanges` de la table de données (méthode) (<xref:System.Data.DataTable.GetChanges%2A>) ou du jeu de données (<xref:System.Data.DataSet.GetChanges%2A>) lui-même. Si vous appelez la méthode pour la table de données, il retourne une copie de la table contenant uniquement les enregistrements modifiés. De même, si vous appelez la méthode sur le jeu de données, vous obtenez un nouveau dataset avec uniquement les enregistrements modifiés.  
  
 `GetChanges` par elle-même retourne tous les enregistrements modifiés. En revanche, en passant le texte souhaité <xref:System.Data.DataRowState> en tant que paramètre à la `GetChanges` (méthode), vous pouvez spécifier le sous-ensemble d’enregistrements modifiés souhaité : nouvellement ajouté détaché d’enregistrements, enregistrements marqués pour suppression, enregistrements ou des enregistrements modifiés.  
  
 Obtention d’un sous-ensemble des enregistrements modifiés est utile lorsque vous souhaitez envoyer des enregistrements à un autre composant pour traitement. Au lieu d’envoyer l’ensemble du dataset, vous pouvez réduire la surcharge de la communication avec l’autre composant en récupérant uniquement les enregistrements dont le composant a besoin. Pour plus d’informations, consultez [Comment : récupérer des lignes modifiées](http://msdn.microsoft.com/library/6ff0cbd0-5253-48e7-888a-144d56c2e0a9).  
  
## <a name="committing-changes-in-the-dataset"></a>Validation des modifications dans le jeu de données  
 Lorsque des modifications sont apportées dans le jeu de données, le <xref:System.Data.DataRow.RowState%2A> propriété des lignes modifiées est définie. Les versions d’origine et actuelles des enregistrements sont établies, conservées et mises à votre disposition par le <xref:System.Data.DataRowView.RowVersion%2A> propriété. Les métadonnées sont stockées dans les propriétés de ces lignes modifiées ne sont nécessaire pour envoyer les mises à jour correctes à la source de données.  
  
 Si les modifications reflètent l’état actuel de la source de données, vous n’avez plus besoin de conserver ces informations. En règle générale, voici les deux heures lorsque le jeu de données et sa source sont synchronisés :  
  
- Immédiatement après le chargement des informations dans le jeu de données, telles que lorsque vous lisez des données à partir de la source.  
  
- Après l’envoi des modifications du jeu de données à la source de données (mais pas avant, car vous perdrez les informations de modification qui sont nécessaire pour envoyer les modifications à la base de données).  
  
  Vous pouvez valider les modifications en attente pour le jeu de données en appelant le <xref:System.Data.DataSet.AcceptChanges%2A> (méthode). En règle générale, <xref:System.Data.DataSet.AcceptChanges%2A> est appelée pendant les heures suivantes dans votre application.  
  
- Après avoir chargé le jeu de données. Si vous chargez un jeu de données en appelant d’un TableAdapter `Fill` (méthode), puis l’adaptateur valide automatiquement les modifications pour vous. Toutefois, si vous chargez un jeu de données en y fusionnant un autre jeu de données, vous devez valider les modifications manuellement.  
  
  > [!NOTE]
  >  Vous pouvez empêcher l’adaptateur de validation des modifications automatiquement lorsque vous appelez le `Fill` méthode en définissant le `AcceptChangesDuringFill` propriété de l’adaptateur à `false`. Si elle est définie sur `false`, puis le <xref:System.Data.DataRow.RowState%2A> de chaque ligne est insérée lors du remplissage est définie sur <xref:System.Data.DataRowState>.  
  
- Une fois que vous envoyez les modifications de jeu de données à un autre processus, comme un service Web XML.  
  
  > [!CAUTION]
  >  Validation de la modification de cette façon efface toutes les informations modifiées. Ne pas valider les modifications jusqu'à ce qu’après avoir terminent des opérations nécessitant de votre application pour savoir quelles modifications ont été apportées dans le jeu de données.  
  
  Cette méthode effectue les opérations suivantes :  
  
- Écrit le <xref:System.Data.DataRowVersion> version d’un enregistrement dans son <xref:System.Data.DataRowVersion> version et remplace la version d’origine.  
  
- Supprime toute ligne où le <xref:System.Data.DataRow.RowState%2A> propriété est définie sur <xref:System.Data.DataRowState>.  
  
- Définit le <xref:System.Data.DataRow.RowState%2A> propriété d’un enregistrement à <xref:System.Data.DataRowState>.  
  
  Le <xref:System.Data.DataSet.AcceptChanges%2A> méthode est disponible à trois niveaux. Vous pouvez l’appeler sur un <xref:System.Data.DataRow> objet aux validations est modifié pour simplement cette ligne. Vous pouvez également l’appeler sur un <xref:System.Data.DataTable> objet à valider toutes les lignes dans une table. Enfin, vous pouvez l’appeler sur le <xref:System.Data.DataSet> objet à valider toutes les modifications en attente dans tous les enregistrements de toutes les tables du jeu de données.  
  
  Le tableau suivant décrit les modifications sont validées selon ce que la méthode est appelée sur l’objet.  
  
|Méthode|Résultat|  
|------------|------------|  
|<xref:System.Data.DataRow.AcceptChanges%2A?displayProperty=fullName>|Les modifications sont validées uniquement sur la ligne spécifique.|  
|<xref:System.Data.DataTable.AcceptChanges%2A?displayProperty=fullName>|Les modifications sont validées sur toutes les lignes dans la table spécifique.|  
|<xref:System.Data.DataSet.AcceptChanges%2A?displayProperty=fullName>|Les modifications sont validées sur toutes les lignes de toutes les tables du jeu de données.|  
  
> [!NOTE]
>  Si vous chargez un jeu de données en appelant d’un TableAdapter `Fill` (méthode), vous ne devez accepter explicitement les modifications. Par défaut, le `Fill` les appels de méthode le `AcceptChanges` méthode après son remplissage de la table de données.  
  
 Une méthode associée, `RejectChanges`, annule les modifications en copiant le <xref:System.Data.DataRowVersion> version dans le <xref:System.Data.DataRowVersion> version d’enregistrements. Il définit également la <xref:System.Data.DataRow.RowState%2A> de chaque enregistrement à <xref:System.Data.DataRowState>.  
  
## <a name="data-validation"></a>Validation des données  
 Afin de vérifier que les données dans votre application répond aux exigences des processus qui elle est passée à, vous devez souvent ajouter la validation. Cela peut impliquer la vérification que l’entrée d’utilisateur dans un formulaire est correcte, validation des données qui sont envoyées à votre application par une autre application, ou même vérifier que les informations qui sont calculées au sein de votre composant se trouve dans les contraintes de votre source de données et les exigences de l’application.  
  
 Vous pouvez valider les données de plusieurs manières :  
  
- Dans la couche métier, en ajoutant du code à votre application pour valider les données. Le jeu de données est un seul endroit, vous pouvez le faire. Le jeu de données fournit quelques-uns des avantages de la validation de serveur principal, telles que la capacité à valider les modifications que la modifiant des valeurs de colonne et de ligne. Pour plus d’informations, consultez [valider des données dans les jeux de données](../data-tools/validate-data-in-datasets.md).  
  
- Dans la couche de présentation, en ajoutant la validation aux formulaires. Pour plus d’informations, consultez [Validation des entrées utilisateur dans les Windows Forms](http://msdn.microsoft.com/library/4ec07681-1dee-4bf9-be5e-718f635a33a1).  
  
- Dans les données back-end, en envoyant des données à la source de données, par exemple, la base de données et en l’autorisant à accepter ou refuser les données. Si vous travaillez avec une base de données qui a des fonctionnalités évoluées de validation des données et fournir des informations d’erreur, cela peut être une approche pratique, car vous pouvez valider les données, quel que soit l’emplacement d’origine. Toutefois, cette approche ne peut pas satisfaire les exigences de la validation spécifique à l’application. En outre, la source de données valider des données peut entraîner de nombreux allers-retours vers la source de données, en fonction de la façon dont votre application facilite la résolution des erreurs de validation déclenchés par le serveur principal.  
  
  > [!IMPORTANT]
  >  Lorsque vous utilisez les commandes de données avec un <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> propriété a la valeur <xref:System.Data.CommandType>, soigneusement vérifier les informations qui sont envoyées à partir d’un client avant de le transmettre à votre base de données. Les utilisateurs malveillants peuvent tenter d’envoyer (injecter) des instructions SQL modifiées ou supplémentaires dans le but d’obtenir un accès non autorisé ou d’endommager la base de données. Avant de transférer l’entrée utilisateur et une base de données, vérifiez toujours que les informations sont valides. Il est recommandé de toujours utiliser des requêtes paramétrables ou les procédures stockées lorsque cela est possible. Pour plus d’informations, consultez [Vue d’ensemble des attaques de script](http://msdn.microsoft.com/library/772c7312-211a-4eb3-8d6e-eec0aa1dcc07).  
  
  Une fois que les modifications ont été apportées dans un jeu de données, vous pouvez transmettre les modifications apportées à une source de données. En règle générale, ce faire, appelez le `Update` méthode d’un TableAdapter (ou adaptateur de données). La méthode parcourt chaque enregistrement dans une table de données détermine quel type de mise à jour est nécessaire (update, insert ou delete), le cas échéant, puis exécute la commande appropriée.  
  
## <a name="transmitting-updates-to-the-data-source"></a>Transmission des mises à jour à la source de données  
 En guise d’illustration de la façon dont les mises à jour sont effectuées, supposons que votre application utilise un jeu de données qui contient une table de données unique. L’application extrait les deux lignes de la base de données. Après la récupération, la table de données en mémoire ressemble à ceci :  
  
```  
(RowState)     CustomerID   Name             Status  
(Unchanged)    c200         Robert Lyon      Good  
(Unchanged)    c400         Nancy Buchanan    Pending  
```  
  
 Votre application change le statut de Nancy Buchanan « Favoris ». Suite à cette modification, la valeur de la <xref:System.Data.DataRow.RowState%2A> propriété pour cette ligne passe de <xref:System.Data.DataRowState> à <xref:System.Data.DataRowState>. La valeur de la <xref:System.Data.DataRow.RowState%2A> propriété pour la première ligne reste <xref:System.Data.DataRowState>. La table de données ressemble maintenant à ceci :  
  
```  
(RowState)     CustomerID   Name             Status  
(Unchanged)    c200         Robert Lyon      Good  
(Modified)     c400         Nancy Buchanan    Preferred  
```  
  
 Votre application maintenant appelle le `Update` méthode pour transmettre le jeu de données à la base de données. La méthode inspecte chaque ligne à son tour. Pour la première ligne, la méthode ne transmet aucun instruction SQL à la base de données, car cette ligne n’a pas changé dans la mesure où il a été récupérée à l’origine à partir de la base de données.  
  
 Pour la deuxième ligne, la `Update` méthode appelle la commande de données correcte et transmet à la base de données automatiquement. La syntaxe de l’instruction SQL spécifique varie selon le dialecte SQL qui est pris en charge par le magasin de données sous-jacent. Mais les caractéristiques suivantes de l’instruction SQL transmise sont dignes d’intérêt :  
  
-   L’instruction SQL transmise est une instruction de mise à jour. L’adaptateur sait qu’il doit pour utiliser une instruction UPDATE, car la valeur de la <xref:System.Data.DataRow.RowState%2A> propriété est <xref:System.Data.DataRowState>.  
  
-   L’instruction SQL transmise comprend une clause WHERE indiquant que la cible de l’instruction UPDATE est la ligne où `CustomerID = 'c400'`. Cette partie de l’instruction SELECT distingue la ligne cible des autres, car le `CustomerID` est la clé primaire de la table cible. Les informations de la clause WHERE est dérivée de la version d’origine de l’enregistrement (`DataRowVersion.Original`), au cas où les valeurs qui sont nécessaires pour identifier la ligne ont été modifiés.  
  
-   L’instruction SQL transmise inclut la clause SET pour définir les nouvelles valeurs des colonnes modifiées.  
  
    > [!NOTE]
    >  Si le TableAdapter `UpdateCommand` propriété a été définie sur le nom d’une procédure stockée, l’adaptateur ne construit pas une instruction SQL. Au lieu de cela, elle appelle la procédure stockée avec les paramètres passés dans appropriés.  
  
## <a name="passing-parameters"></a>Passage de paramètres  
 Vous utilisez généralement des paramètres pour passer les valeurs pour les enregistrements qui vont être mis à jour dans la base de données.  Lorsque le TableAdapter `Update` méthode exécute une instruction de mise à jour, il doit remplir les valeurs de paramètre. Ces valeurs sont obtenues à partir de la `Parameters` collection pour la commande de données approprié, dans ce cas, le `UpdateCommand` objet dans le TableAdapter.  
  
 Si vous avez utilisé les outils Visual Studio pour générer un adaptateur de données, le `UpdateCommand` objet constituée une collection de paramètres correspondant à chaque espace réservé de paramètre dans l’instruction.  
  
 Le <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A?displayProperty=fullName> propriété de chaque paramètre pointe vers une colonne dans la table de données. Par exemple, le `SourceColumn` propriété pour le `au_id` et `Original_au_id` paramètres est définie sur la colonne dans la table de données contenant l’id de l’auteur. Lorsque l’adaptateur `Update` exécutions de méthode, il lit l’auteur de colonne d’id de l’enregistrement est mis à jour et remplit les valeurs dans l’instruction.  
  
 Dans une instruction de mise à jour, vous devez spécifier les nouvelles valeurs (celles qui sont écrits dans l’enregistrement), ainsi que les anciennes valeurs (de sorte que l’enregistrement peut se trouver dans la base de données). Il existe donc deux paramètres pour chaque valeur : un pour la clause SET et un autre pour la clause WHERE. Les deux paramètres lisent les données à partir de l’enregistrement est mis à jour, mais ils obtiennent des versions différentes de la valeur de colonne en fonction du paramètre [propriété SqlParameter.SourceVersion](https://msdn.microsoft.com/library/system.data.sqlclient.sqlparameter.sourceversion.aspx). Le paramètre pour la clause SET obtient la version actuelle, et le paramètre pour la clause WHERE obtient la version d’origine.  
  
> [!NOTE]
>  Vous pouvez également définir des valeurs le `Parameters` collection vous-même dans le code que vous le feriez en général dans un gestionnaire d’événements pour l’adaptateur de données <xref:System.Data.DataTable.RowChanging> événement.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de TableAdapter](../data-tools/tableadapter-overview.md)   
 [Mettre à jour des données à l’aide d’un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)   
 [Vue d’ensemble des Applications de données dans Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Connexion aux données dans Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Préparation de votre Application à recevoir des données](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Récupération de données dans votre Application](../data-tools/fetching-data-into-your-application.md)   
 [Lier des contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modification des données dans votre Application](../data-tools/editing-data-in-your-application.md)   
 [Validation des données](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Enregistrer des données](../data-tools/saving-data.md)

