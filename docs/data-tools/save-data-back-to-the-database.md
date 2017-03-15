---
title: "Enregistrement de donn&#233;es dans des groupes de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "données (Visual Studio), enregistrer"
  - "validation des données, groupes de données"
  - "groupes de données (Visual Basic), à propos des groupes de données"
  - "groupes de données (Visual Basic), contraintes"
  - "groupes de données (Visual Basic), fusionner"
  - "groupes de données (Visual Basic), valider des données"
  - "version des lignes"
  - "enregistrer les données, à propos de l'enregistrement de données"
  - "TableAdapters"
  - "mises à jour, contraintes dans des groupes de données"
  - "mise à jour de groupes de données, contraintes"
ms.assetid: afe6cb8a-dc6a-428b-b07b-903ac02c890b
caps.latest.revision: 27
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Enregistrement de donn&#233;es dans des groupes de donn&#233;es
L'enregistrement des données correspond au processus consistant à rendre persistantes les données modifiées d'une application dans le magasin de données d'origine, en général une base de données relationnelle telle que SQL Server.  
  
 Un groupe de données est en fait un cache \(une copie en mémoire\) de données. L'écriture d'informations dans la source de données d'origine est donc un processus distinct de celui de la modification des données dans le groupe de données.  Vous pouvez renvoyer les données mises à jour dans les groupes de données à la base de données en appelant la méthode `Update` d'un TableAdapter ou en appelant l'une des méthodes DBDirect du TableAdapter.  
  
 Pour plus d'informations sur la manière de renvoyer à la base de données les modifications apportées à un groupe de données, consultez [Comment : mettre à jour les données à l'aide d'un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md) et [Comment : enregistrer les modifications apportées à un groupe de données dans une base de données](../Topic/How%20to:%20Save%20Dataset%20Changes%20to%20a%20Database.md).  
  
 Visual Studio fournit un composant `TableAdapterManager` qui aide à effectuer des enregistrements de données dans les tables connexes.  Ce composant vérifie que les enregistrements sont effectués dans l'ordre approprié en fonction des contraintes de clé étrangère définies dans la base de données.  Pour plus d'informations, consultez [Vue d'ensemble de la mise à jour hiérarchique](../Topic/Hierarchical%20Update%20Overview.md).  
  
 Pour plus d'informations sur la modification de données dans le groupe de données, consultez [Modification des données dans votre application](../data-tools/editing-data-in-your-application.md).  
  
## Mises à jour en deux étapes  
 La procédure de mise à jour d'une source de données au moyen d'un groupe de données comprend deux étapes.  La première étape consiste à mettre à jour le groupe de données avec les nouvelles informations : nouveaux enregistrements, enregistrements modifiés ou enregistrements supprimés.  Si votre application n'est liée qu'au groupe de données — par exemple, après avoir mis à jour le groupe de données, vous l'envoyez à une autre application qui y effectuera des traitements supplémentaires — votre mise à jour est terminée.  
  
> [!NOTE]
>  Dans les Windows Forms, l'architecture de liaison de données se charge d'envoyer les modifications des contrôles liés aux données au groupe de données, en vous dispensant de mettre à jour explicitement le groupe de données à l'aide de votre propre code.  Pour plus d'informations, consultez [Liaison de données Windows Forms](../Topic/Windows%20Forms%20Data%20Binding.md).  
  
 Si vous mettez à jour une source de données \(telle qu'une base de données\), la seconde étape consiste à envoyer les modifications du groupe de données à la source de données d'origine.  C'est\-à\-dire que le processus de mise à jour du groupe de données n'écrit pas les modifications dans une source de données sous\-jacente ; il vous faut donc explicitement réaliser cette seconde étape.  En général, pour réaliser cette opération, vous devez appeler la méthode Update du TableAdapter \(ou de l'adaptateur de données\) que vous avez utilisé pour remplir le groupe de données. Vous pouvez néanmoins utiliser des adaptateurs différents, notamment pour déplacer des données d'une source dans une autre ou pour mettre à jour plusieurs sources.  
  
 ![Mises à jour des groupes de données Visual Basic](../data-tools/media/vbdatasetupdates.gif "vbDatasetUpdates")  
Processus de mise à jour en deux étapes et rôle de DataRowVersion dans une mise à jour réussie  
  
 Structurellement, un groupe de données propose les données sous forme d'un ensemble de collections.  Les groupes de données contiennent des collections de tables.  Les tables contiennent des collections de lignes.  Les tables sont exposées sous la forme d'une collection de l'objet <xref:System.Data.DataSet> et les enregistrements sont disponibles dans la collection <xref:System.Data.DataTable.Rows%2A> des objets <xref:System.Data.DataTable>.  Vous pouvez apporter des modifications aux données d'un groupe de données en manipulant ces collections à l'aide de méthodes de base de collection. Cependant, si vous souhaitez mettre à jour une source de données sous\-jacente, vous devez utiliser les méthodes spécialement conçues pour la modification des groupes de données.  
  
 Par exemple, pour supprimer un enregistrement d'une table de données, vous pouvez appeler la [méthode RemoveAt](https://msdn.microsoft.com/en-us/library/system.data.datarowcollection.removeat.aspx) de la collection <xref:System.Data.DataTable.Rows%2A> de la table. L'enregistrement sera alors supprimé physiquement du groupe de données.  Si vous n'utilisez le groupe de données que comme magasin structuré de données et que vous ne souhaitez pas transmettre les informations de modification vers d'autres applications, cette façon de manipuler les collections représente un moyen acceptable de mettre à jour un groupe de données.  
  
 Néanmoins, si vous avez l'intention d'envoyer les modifications vers une source de données ou une autre application, vous devez conserver les informations de modification \(telles que les métadonnées\) relatives à chaque mise à jour.  Lorsque vous enverrez les modifications à la source de données ou à l'application, le processus disposera alors des informations nécessaires pour rechercher et mettre à jour les enregistrements appropriés.  Par exemple, si vous supprimez un enregistrement dans le groupe de données, les informations relatives à l'enregistrement supprimé doivent être conservées dans le groupe de données,  de sorte que lors de l'appel à `DeleteCommand` du TableAdapter, il existe une quantité suffisante d'informations d'historique pour rechercher l'enregistrement d'origine dans la source de données et afin de le supprimer.  Pour plus d'informations, consultez « Conservation des informations relatives aux modifications » ci\-après.  
  
## Fusion de groupes de données  
 Vous pouvez mettre à jour le contenu d'un groupe de données en *fusionnant* \(c'est\-à\-dire en copiant le contenu d'un groupe de données, appelé groupe de données *source*, dans le groupe de données appelant, appelé groupe de données *cible*\).  Lorsque vous fusionnez des groupes de données, les nouveaux enregistrements du groupe de données source sont ajoutés au groupe de données cible.  De plus, les colonnes supplémentaires du groupe de données source sont ajoutées au groupe de données cible.  La fusion de groupes de données est particulièrement utile lorsque, alors que vous disposez déjà d'un groupe de données local, vous obtenez un second groupe de données à partir d'une autre application ou d'un composant tel qu'un service Web XML,  ou lorsque vous avez simplement besoin d'intégrer des données de plusieurs groupes de données.  
  
 Lorsque vous fusionnez des groupes de données, vous pouvez également transmettre un argument Boolean facultatif \(`preserveChanges`\) qui indique à la méthode <xref:System.Data.DataSet.Merge%2A> si elle doit conserver les modifications existantes du groupe de données cible.  Les groupes de données conservant plusieurs versions des enregistrements, toutes ces versions seront donc fusionnées.  Le tableau suivant représente un enregistrement de deux groupes de données qui vont être fusionnés :  
  
|DataRowVersion|Groupe de données cible|Groupe de données source|  
|--------------------|-----------------------------|------------------------------|  
|D'origine|James Wilson|James C.  Wilson|  
|Actuelle|Jim Wilson|James C.  Wilson|  
  
 L'appel à la méthode <xref:System.Data.DataSet.Merge%2A> dans le tableau ci\-dessus à l'aide de `preserveChanges=false targetDataset.Merge(sourceDataset)` donne le résultat suivant :  
  
|DataRowVersion|Groupe de données cible|Groupe de données source|  
|--------------------|-----------------------------|------------------------------|  
|D'origine|James C.  Wilson|James C.  Wilson|  
|Actuelle|James C.  Wilson|James C.  Wilson|  
  
 L'appel de la méthode <xref:System.Data.DataSet.Merge%2A> avec `preserveChanges = true targetDataset.Merge(sourceDataset, true)` donne le résultat suivant :  
  
|DataRowVersion|Groupe de données cible|Groupe de données source|  
|--------------------|-----------------------------|------------------------------|  
|D'origine|James C.  Wilson|James C.  Wilson|  
|Actuelle|Jim Wilson|James C.  Wilson|  
  
> [!CAUTION]
>  Dans le scénario `preserveChanges = true`, si la méthode <xref:System.Data.DataSet.RejectChanges%2A> est appelée sur un enregistrement dans le groupe de données cible, ce sont les données d'origine du groupe de données *source* qui s'affichent.  Cela signifie que si vous essayez de mettre à jour la source des données d'origine avec le groupe de données cible, il se peut qu'il ne soit pas en mesure de rechercher la ligne d'origine à mettre à jour.  Toutefois, vous pouvez empêcher toute violation d'accès concurrentiel en remplissant un autre groupe de données avec les enregistrements mis à jour provenant de la source de données et en exécutant ensuite une fusion. \(Une violation d'accès concurrentiel se produit lorsqu'un autre utilisateur modifie un enregistrement dans la source de données après le remplissage du groupe de données.\)  
  
## Contraintes de mise à jour  
 Pour effectuer des modifications dans une ligne de données existante, vous devez ajouter ou mettre à jour des données dans les colonnes individuelles.  Si le groupe de données contient des contraintes \(telles que des contraintes de clé étrangère ou des contraintes autorisant les valeurs Null\), lors de la mise à jour d'un enregistrement, entre la mise à jour d'une colonne et le passage à la suivante, il se peut que l'enregistrement soit temporairement en état d'erreur.  
  
 Pour éviter des violations de contrainte prématurées, vous pouvez interrompre temporairement les contraintes de mise à jour.  Ceci permet :  
  
-   d'empêcher la génération d'une erreur entre deux mises à jour de colonnes ;  
  
-   d'interrompre le déclenchement de certains événements de mise à jour \(les événements fréquemment utilisés pour la validation\).  
  
 Après avoir effectué une mise à jour, vous pouvez réactiver la vérification des contraintes, ce qui réactive et déclenche également les événements de mise à jour.  
  
> [!NOTE]
>  Dans les Windows Forms, l'architecture de liaison de données intégrée à la grille de données interrompt la vérification des contraintes jusqu'à ce que le focus quitte une ligne. Vous n'avez pas à appeler explicitement la méthode <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A> ou <xref:System.Data.DataRow.CancelEdit%2A>.  
  
 Les contraintes sont automatiquement désactivées lorsque la méthode <xref:System.Data.DataSet.Merge%2A> est appelée sur un groupe de données.  Après la fusion, la présence, dans le groupe de données, de contraintes qui ne peuvent pas être activées entraîne la levée d'une <xref:System.Data.ConstraintException>.  Dans ce cas, la propriété <xref:System.Data.DataSet.EnforceConstraints%2A> a la valeur `false` et toutes les violations de contrainte doivent être résolues avant de réinitialiser la valeur de la propriété <xref:System.Data.DataSet.EnforceConstraints%2A> sur `true`.  
  
 Après avoir effectué une mise à jour, vous pouvez réactiver la vérification des contraintes, ce qui réactive et déclenche également les événements de mise à jour.  
  
 Pour plus d'informations sur la suspension d'événements, consultez [Comment : désactiver les contraintes pendant le remplissage d'un groupe de données](../data-tools/turn-off-constraints-while-filling-a-dataset.md).  
  
## Erreurs de mise à jour de groupes de données  
 Lorsque vous mettez à jour un enregistrement dans un groupe de données, il peut se produire une erreur.  Vous pouvez, par exemple, écrire par inadvertance dans une colonne des données d'un type incorrect, trop longues ou présentant d'autres problèmes d'intégrité.  En outre, des contrôles de validation propre aux applications peuvent déclencher des erreurs personnalisées à tout moment pendant un événement de mise à jour.  Pour plus d'informations, consultez [Validation de données dans des groupes de données](../data-tools/validate-data-in-datasets.md).  
  
## Conservation des informations relatives aux modifications  
 Les informations sur les modifications apportées à un groupe de données sont gérées de deux façons : en attribuant à la ligne un indicateur signalant si elle a été modifiée \(<xref:System.Data.DataRow.RowState%2A>\) et en conservant plusieurs copies d'un même enregistrement \(<xref:System.Data.DataRowVersion>\).  Grâce à ces informations, les processus peuvent déterminer quelles modifications ont été apportées au groupe de données et envoyer les mises à jour appropriées à la source de données.  
  
### RowState, propriété  
 La propriété <xref:System.Data.DataRow.RowState%2A> d'un objet <xref:System.Data.DataRow> est une valeur fournissant des informations sur l'état d'une ligne de données particulière.  
  
 Le tableau suivant détaille les valeurs possibles de l'énumération <xref:System.Data.DataRowState> :  
  
|Valeur DataRowState|Description|  
|-------------------------|-----------------|  
|<xref:System.Data.DataRowState>|La ligne a été ajoutée à un <xref:System.Data.DataRowCollection> en tant qu'élément \(une ligne dans cet état ne possède pas de version d'origine correspondante puisqu'elle n'existait pas au moment du dernier appel à la méthode <xref:System.Data.DataRow.AcceptChanges%2A>\).|  
|<xref:System.Data.DataRowState>|La ligne a été supprimée à l'aide du <xref:System.Data.DataRow.Delete%2A> d'un objet <xref:System.Data.DataRow>.|  
|<xref:System.Data.DataRowState>|La ligne a été créée, mais n'appartient à aucun <xref:System.Data.DataRowCollection>.  Un objet <xref:System.Data.DataRow> est dans cet état immédiatement après sa création et avant d'avoir été ajouté à une collection ou s'il a été supprimé d'une collection.|  
|<xref:System.Data.DataRowState>|Une valeur de colonne de la ligne a été modifiée.|  
|<xref:System.Data.DataRowState>|La ligne n'a pas été modifiée depuis le dernier appel à <xref:System.Data.DataRow.AcceptChanges%2A>.|  
  
### DataRowVersion, énumération  
 Les groupes de données conservent plusieurs versions d'un même enregistrement.  L'énumération <xref:System.Data.DataRowVersion> d'un objet <xref:System.Data.DataRow> est une valeur pouvant être utilisée pour retourner une version particulière d'un objet <xref:System.Data.DataRow>.  
  
 Le tableau suivant détaille les valeurs possibles de l'énumération <xref:System.Data.DataRowVersion> :  
  
|Valeur DataRowVersion|Description|  
|---------------------------|-----------------|  
|<xref:System.Data.DataRowVersion>|La version en cours d'un enregistrement contient toutes les modifications apportées à un enregistrement depuis le dernier appel à la méthode <xref:System.Data.DataRow.AcceptChanges%2A>.  Si la ligne a été supprimée, il n'existe pas de version en cours.|  
|<xref:System.Data.DataRowVersion>|La valeur par défaut d'un enregistrement, telle que définie par le schéma de groupe de données ou la source de données.|  
|<xref:System.Data.DataRowVersion>|La version d'origine d'un enregistrement est une copie de l'enregistrement tel qu'il était la dernière fois que des modifications ont été apportées au groupe de données.  Il s'agit généralement de la version d'un enregistrement lu à partir d'une source de données.|  
|<xref:System.Data.DataRowVersion>|La version proposée d'un enregistrement temporairement disponible, au cours d'une mise à jour, c'est\-à\-dire entre l'appel à la méthode <xref:System.Data.DataRow.BeginEdit%2A> et l'appel à la méthode <xref:System.Data.DataRow.EndEdit%2A>.  Généralement, vous pouvez accéder à la version proposée d'un enregistrement dans un gestionnaire pour un événement tel que <xref:System.Data.DataTable.RowChanging>.  L'appel à la méthode <xref:System.Data.DataRow.CancelEdit%2A> annule les modifications et supprime la version proposée de la ligne de données.|  
  
 Les versions d'origine et actuelles sont utiles lorsque les informations de mise à jour sont transmises à une source de données.  Généralement, lors de l'envoi d'une mise à jour à la source de données, les nouvelles informations de la base de données se trouvent dans la version actuelle d'un enregistrement  et les informations de la version d'origine sont utilisées pour rechercher l'enregistrement à mettre à jour.  Par exemple, en cas de modification de la clé primaire d'un enregistrement, vous devrez rechercher l'enregistrement approprié dans la source de données de façon à mettre à jour les modifications.  S'il n'existait pas de version d'origine, l'enregistrement serait probablement ajouté à la source de données, entraînant ainsi la présence d'un enregistrement supplémentaire inutile qui sera, en outre, inexact ou obsolète.  Les deux versions sont également utilisées dans le contrôle d'accès concurrentiel ; vous pouvez comparer la version d'origine à un enregistrement de la source de données afin de déterminer si l'enregistrement a été modifié depuis son chargement dans le groupe de données.  
  
 Vous pouvez utiliser la version proposée lorsque vous devez effectuer une validation avant d'apporter réellement des modifications au groupe de données.  
  
 Même si des enregistrements ont été modifiés, il n'existe pas toujours de version d'origine ou de version actuelle de la ligne concernée.  Lorsque vous insérez une nouvelle ligne dans la table, il n'existe qu'une version actuelle de la ligne, pas de version d'origine.  De même, si vous supprimez une ligne en appelant la méthode `Delete` de la table, il existe une version d'origine, mais pas de version actuelle.  
  
 Vous pouvez effectuer un test pour voir s'il existe une version spécifique d'un enregistrement en interrogeant la méthode <xref:System.Data.DataRow.HasVersion%2A> d'une ligne de données.  Vous pouvez accéder à l'une ou l'autre des versions d'un enregistrement en passant une valeur d'énumération <xref:System.Data.DataRowVersion> en tant qu'argument facultatif lorsque vous demandez la valeur d'une colonne.  
  
## Obtention d'enregistrements modifiés  
 Il est courant de ne pas mettre à jour tous les enregistrements d'un groupe de données.  Par exemple, un utilisateur peut utiliser un contrôle <xref:System.Windows.Forms.DataGridView> Windows Forms affichant plusieurs enregistrements.  Néanmoins, il peut ne mettre à jour que quelques enregistrements, en supprimer un et en insérer un nouveau.  Les groupes de données et les tables de données proposent une méthode \(`GetChanges`\) permettant de ne retourner que les lignes modifiées.  
  
 Vous pouvez créer des sous\-ensembles d'enregistrements modifiés en utilisant la méthode `GetChanges` de la table de données \(<xref:System.Data.DataTable.GetChanges%2A>\) ou du groupe de données \(<xref:System.Data.DataSet.GetChanges%2A>\) lui\-même.  Lorsque vous appelez la méthode pour la table de données, elle retourne une copie de la table avec les enregistrements modifiés uniquement.  De la même façon, si vous appelez la méthode sur le groupe de données, vous obtenez un nouveau groupe de données comportant uniquement les enregistrements modifiés.  `GetChanges` par elle\-même retourne tous les enregistrements modifiés.  alors que si vous passez le <xref:System.Data.DataRowState> approprié en tant que paramètre à la méthode `GetChanges`, vous pouvez spécifier le sous\-ensemble d'enregistrements modifiés souhaité : enregistrements qui viennent d'être ajoutés, enregistrements marqués pour suppression, enregistrements détachés et enregistrements modifiés.  
  
 L'obtention d'un sous\-ensemble d'enregistrements modifiés est particulièrement utile lorsque vous souhaitez envoyer des enregistrements à un autre composant à des fins de traitement.  Plutôt que d'envoyer le groupe de données complet, vous pouvez réduire la charge liée à la communication avec l'autre composant en n'obtenant que les enregistrements dont il a besoin.  Pour plus d'informations, consultez [Comment : récupérer des lignes modifiées](../Topic/How%20to:%20Retrieve%20Changed%20Rows.md).  
  
## Validation des modifications dans le groupe de données  
 Lorsque des modifications sont apportées dans le groupe de données, la propriété <xref:System.Data.DataRow.RowState%2A> des lignes modifiées est définie.  Les versions d'origine et actuelle des enregistrements sont établies et conservées. Vous pouvez y accéder par l'intermédiaire de la propriété <xref:System.Data.DataRowView.RowVersion%2A>.  Les métadonnées stockées dans ces propriétés représentant les modifications sont nécessaires pour envoyer les mises à jour appropriées à la source de données.  
  
 Si les modifications reflètent l'état actuel de la source de données, vous n'avez plus besoin de conserver ces informations.  Généralement, le groupe de données et sa source sont synchrones à deux moments :  
  
-   Immédiatement après le chargement des informations dans le groupe de données, comme lors de la lecture des données à partir de la source.  
  
-   Après l'envoi des modifications du groupe de données à la source de données \(mais pas avant, car, dans ce cas, les informations de modifications requises pour envoyer les modifications à la base de données seraient perdues\).  
  
 Vous pouvez valider les modifications en attente du groupe de données en appelant la méthode <xref:System.Data.DataSet.AcceptChanges%2A>.  Généralement, <xref:System.Data.DataSet.AcceptChanges%2A> est appelée dans vos applications à l'occasion des événements suivants.  
  
-   Après le chargement du groupe de données.  Si vous chargez un groupe de données en appelant la méthode `Fill` d'un TableAdapter, cet adaptateur valide automatiquement les modifications.  Cependant, si vous chargez un groupe de données en y fusionnant un autre groupe de données, vous devez valider les modifications manuellement.  
  
    > [!NOTE]
    >  Lorsque vous appelez la méthode `Fill`, vous pouvez empêcher l'adaptateur de valider automatiquement les données en attribuant la valeur `false` à la propriété `AcceptChangesDuringFill` de l'adaptateur.  S'il a la valeur `false`, la valeur <xref:System.Data.DataRowState> est attribuée au <xref:System.Data.DataRow.RowState%2A> de chaque ligne insérée lors du remplissage.  
  
-   Après l'envoi des modifications du groupe de données à un autre processus, tel qu'un service Web XML.  
  
    > [!CAUTION]
    >  Cette méthode de validation des modifications efface toutes les informations de modification.  Ne validez aucune modification avant d'avoir réalisé les opérations pour lesquelles vos applications dépendent des modifications effectuées dans le groupe de données.  
  
 Cette méthode :  
  
-   Écrit la version <xref:System.Data.DataRowVersion> d'un enregistrement dans sa version <xref:System.Data.DataRowVersion>, en remplaçant la version d'origine.  
  
-   Supprime toute ligne dont la propriété <xref:System.Data.DataRow.RowState%2A> a la valeur <xref:System.Data.DataRowState>.  
  
-   Affecte à la propriété <xref:System.Data.DataRow.RowState%2A> d'un enregistrement la valeur <xref:System.Data.DataRowState>.  
  
 La méthode <xref:System.Data.DataSet.AcceptChanges%2A> est disponible à trois niveaux.  Vous pouvez l'appeler sur un objet <xref:System.Data.DataRow>, pour valider uniquement les modifications de cette ligne.  Vous pouvez également l'appeler sur un objet <xref:System.Data.DataTable> pour valider toutes les lignes d'une table ou sur l'objet <xref:System.Data.DataSet> pour valider toutes les modifications en attente de tous les enregistrements de toutes les tables du groupe de données.  
  
 Le tableau suivant décrit les modifications qui sont validées en fonction de l'objet sur lequel la méthode est appelée.  
  
|Méthode|Résultat|  
|-------------|--------------|  
|<xref:System.Data.DataRow.AcceptChanges%2A?displayProperty=fullName>|Les modifications ne sont validées que dans la ligne concernée.|  
|<xref:System.Data.DataTable.AcceptChanges%2A?displayProperty=fullName>|Les modifications sont validées dans toutes les lignes de la table.|  
|<xref:System.Data.DataSet.AcceptChanges%2A?displayProperty=fullName>|Les modifications sont validées dans toutes les lignes de toutes les tables du groupe de données.|  
  
> [!NOTE]
>  Lorsque vous chargez un groupe de données en appelant la méthode `Fill` d'un TableAdapter, vous n'avez pas à accepter explicitement les modifications ; par défaut, la méthode `Fill` appelle la méthode `AcceptChanges` après avoir rempli la table de données.  
  
 Une méthode connexe, la méthode `RejectChanges`, annule les modifications en recopiant la version <xref:System.Data.DataRowVersion> dans la version <xref:System.Data.DataRowVersion> des enregistrements et en attribuant à nouveau la valeur <xref:System.Data.DataRowState> au <xref:System.Data.DataRow.RowState%2A> de chaque enregistrement.  
  
## Validation des données  
 Pour vérifier que les données de votre application répondent aux exigences des processus auxquels elles sont passées, il est souvent nécessaire d'effectuer des validations.  Ceci peut impliquer la vérification de la validité des entrées d'un utilisateur dans un formulaire, la validation des données envoyées à votre application par une autre application, voire la vérification de la conformité des informations calculées dans votre composant aux contraintes de votre source de données et aux spécifications de l'application.  
  
 Vous pouvez valider les données de plusieurs façons :  
  
-   Dans la couche métier, en ajoutant du code à vos applications pour valider les données.  Vous pouvez effectuer cette opération dans le groupe de données.  Il offre certains avantages de la validation dans la couche données \(tels que la possibilité de valider les modifications des données au fur et à mesure que des modifications sont apportées aux valeurs des colonnes et des lignes\).  Pour plus d'informations, consultez [Validation de données dans des groupes de données](../data-tools/validate-data-in-datasets.md).  
  
-   Dans la couche de présentation, en ajoutant la validation aux formulaires.  Pour plus d'informations, consultez [Validation des entrées d'utilisateur dans les Windows Forms](../Topic/User%20Input%20Validation%20in%20Windows%20Forms.md).  
  
-   Dans la couche données, en envoyant les données à la source de données \(la base de données, par exemple\) et en lui permettant de les accepter ou de les rejeter.  Si vous travaillez avec une base de données possédant des fonctionnalités évoluées de validation des données et fournissant des informations relatives aux erreurs, vous pouvez valider les données, quelle que soit leur provenance, ce qui peut représenter une approche pratique.  Cependant, cette approche peut ne pas répondre aux exigences de validation propre à l'application.  En outre, la validation des données par la source de données peut entraîner de nombreux allers\-retours vers la source de données, en fonction de la manière dont votre application aborde la résolution des erreurs de validation déclenchées par la couche données.  
  
    > [!IMPORTANT]
    >  Lorsque vous utilisez des commandes de données avec une propriété <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> possédant la valeur <xref:System.Data.CommandType>, vérifiez attentivement les informations envoyées par un client avant de les passer à la base de données.  Des utilisateurs malveillants peuvent tenter d'envoyer \(injecter\) des instructions SQL modifiées ou supplémentaires afin d'accéder à la base de données ou de l'endommager.  Avant de transférer la saisie d'un utilisateur vers une base de données, vous devez toujours vérifier la validité des informations ; il est recommandé de toujours utiliser des requêtes ou des procédures stockées paramétrées lorsque cela est possible.  Pour plus d'informations, consultez [Script Exploits Overview](../Topic/Script%20Exploits%20Overview.md).  
  
 Après avoir effectué des modifications dans un groupe de données, vous pouvez transmettre ces modifications à une source de données.  La plupart du temps, vous réalisez cette opération en appelant la méthode `Update` d'un TableAdapter \(ou adaptateur de données\).  La méthode parcourt chaque enregistrement d'une table de données, détermine le type de mise à jour requis \(mise à jour, insertion ou suppression\), le cas échéant, puis exécute la commande appropriée.  
  
## Transmission d'une mise à jour à la source de données  
 Pour illustrer la façon dont les mises à jour sont réalisées, supposons que votre application utilise un groupe de données ne contenant qu'une seule table de données.  L'application extrait deux lignes de la base de données.  Après récupération, la table de données en mémoire ressemble à ceci :  
  
```  
(RowState)     CustomerID   Name             Status  
(Unchanged)    c200         Robert Lyon      Good  
(Unchanged)    c400         Nancy Buchanan    Pending  
```  
  
 Votre application modifie l'état de Nancy Buchanan en « Preferred ». La valeur de la propriété <xref:System.Data.DataRow.RowState%2A> de cette ligne passe de <xref:System.Data.DataRowState> à <xref:System.Data.DataRowState>.  La valeur de la propriété <xref:System.Data.DataRow.RowState%2A> de la première ligne reste <xref:System.Data.DataRowState>.  La table de données ressemble maintenant à ceci :  
  
```  
(RowState)     CustomerID   Name             Status  
(Unchanged)    c200         Robert Lyon      Good  
(Modified)     c400         Nancy Buchanan    Preferred  
```  
  
 Votre application appelle maintenant la méthode `Update` pour transmettre le groupe de données à la base de données.  Cette méthode examine chaque ligne.  Pour la première ligne, la méthode ne transmet pas d'instruction SQL à la base de données, car cette ligne n'a pas été modifiée depuis son extraction de la base de données.  
  
 Pour la seconde ligne, la méthode `Update` appelle automatiquement la commande de données appropriée et la transmet à la base de données.  La syntaxe particulière de l'instruction SQL dépend du langage SQL pris en charge par le magasin de données sous\-jacent.  Mais il est intéressant de considérer les caractéristiques suivantes de l'instruction SQL transmise :  
  
-   L'instruction SQL transmise est une instruction UPDATE.  L'adaptateur de données sait qu'il faut utiliser une instruction UPDATE, car la valeur de la propriété <xref:System.Data.DataRow.RowState%2A> est <xref:System.Data.DataRowState>.  
  
-   L'instruction SQL transmise comprend une clause WHERE indiquant que la cible de l'instruction UPDATE est la ligne dont le `CustomerID = 'c400'`.  Cette partie de l'instruction SELECT distingue la ligne cible des autres lignes, car `CustomerID` est la clé primaire de la table cible.  Les informations de la clause WHERE proviennent de la version d'origine de l'enregistrement \(`DataRowVersion.Original`\), si des valeurs nécessaires à l'identification de la ligne ont été modifiées.  
  
-   L'instruction SQL transmise comprend une clause SET pour définir les nouvelles valeurs des colonnes modifiées.  
  
    > [!NOTE]
    >  Si la valeur du nom d'une procédure stockée a été attribuée à la propriété `UpdateCommand` du TableAdapter, l'adaptateur ne construit pas d'instruction SQL.  Il appelle la procédure stockée avec les paramètres passés appropriés.  
  
## Passage de paramètres  
 Les valeurs des enregistrements à mettre à jour dans la base de données sont généralement passées à l'aide de paramètres.  Lorsque la méthode `Update` du TableAdapter exécute une instruction UPDATE, elle doit remplir les valeurs de paramètres.  Ces valeurs sont obtenues à partir de la collection `Parameters` pour la commande de données appropriée \(l'objet `UpdateCommand` du TableAdapter, dans le cas présent\).  
  
 Si vous avez utilisé les outils Visual Studio pour générer un adaptateur de données, l'objet `UpdateCommand` contiendra une collection de paramètres correspondant à chaque espace réservé de paramètre dans l'instruction.  
  
 La propriété <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A?displayProperty=fullName> de chaque paramètre pointe vers une colonne dans la table de données.  Par exemple, la propriété `SourceColumn` des paramètres `au_id` et `Original_au_id` a pour valeur la colonne qui contient l'ID d'auteur dans la table de données.  Lorsque la méthode `Update` de l'adaptateur s'exécute, elle lit la colonne ID de l'auteur de l'enregistrement qui est mis à jour et remplit les valeurs dans l'instruction.  
  
 Dans une instruction UPDATE, vous devez spécifier les nouvelles valeurs \(celles qui seront écrites dans l'enregistrement\) ainsi que les anciennes valeurs \(de sorte que l'enregistrement à mettre à jour puisse être recherché dans la base de données\).  Il y a donc deux paramètres pour chaque valeur : un pour la clause SET et un autre pour la clause WHERE.  Les deux paramètres lisent les données de l'enregistrement en cours de mise à jour, mais ils obtiennent des versions différentes de la valeur de colonne en fonction de la [propriété SqlParameter.SourceVersion](https://msdn.microsoft.com/en-us/library/system.data.sqlclient.sqlparameter.sourceversion.aspx) du paramètre.  Le paramètre destiné à la clause SET obtient la version actuelle tandis que le paramètre destiné à la clause WHERE obtient la version d'origine.  
  
> [!NOTE]
>  Vous pouvez également définir vous\-même dans le code les valeurs dans la collection `Parameters`, en général dans un gestionnaire d'événements pour l'événement <xref:System.Data.DataTable.RowChanging> de l'adaptateur de données.  
  
## Mise à jour de tables connexes  
 Si votre groupe de données contient plusieurs tables, il vous faut les mettre à jour individuellement en appelant séparément la méthode `Update` de chaque adaptateur de données.  Si les tables ont une relation parent\-enfant, vous devrez probablement envoyer les mises à jour au groupe de données dans un ordre précis.  Il arrive souvent que vous ayez ajouté les enregistrements parents et les enregistrements enfants connexes à un groupe de données — par exemple, un nouvel enregistrement relatif à un client et au moins un enregistrement de commande le concernant.  Si la base de données met elle\-même en œuvre des règles d'intégrité relationnelle, des erreurs seront déclenchées si vous envoyez les nouveaux enregistrements enfants à la base de données avant la création de l'enregistrement parent.  
  
 Inversement, si vous supprimez des enregistrements connexes dans le groupe de données, il vous faut généralement envoyer les mises à jour dans l'ordre inverse : d'abord la table enfant et puis la table parente.  Sinon, la base de données risque de déclencher une erreur, car les règles d'intégrité référentielle vous empêcheront de supprimer un enregistrement parent s'il existe des enregistrements enfants.  
  
 En règle générale, l'envoi de mises à jour des tables connexes doit respecter l'ordre suivant :  
  
1.  Table enfant : suppression des enregistrements.  
  
2.  Table parente : insertion, mise à jour et suppression des enregistrements.  
  
3.  Table enfant : insertion et mise à jour des enregistrements.  
  
4.  Pour plus d'informations, consultez [Procédure pas à pas : enregistrement de données dans une base de données \(plusieurs tables\)](../data-tools/save-data-to-a-database-multiple-tables.md).  
  
## Contrôle d'accès concurrentiel  
 Les groupes de données étant déconnectés de la source de données, vous ne verrouillez pas les enregistrements dans la source de données.  Par conséquent, lorsque vous souhaitez mettre à jour la base de données, si votre application doit gérer le contrôle d'accès concurrentiel, vous devez rapprocher les enregistrements du groupe de données et ceux de la base de données.  Par exemple, vous pouvez constater que des enregistrements de la base de données ont été modifiés depuis le dernier remplissage du groupe de données.  Dans ce cas, vous devez exécuter la logique appropriée à l'application pour spécifier les actions à réaliser pour l'enregistrement de la base de données ou l'enregistrement modifié contenu dans le groupe de données.  
  
## Voir aussi  
 [Vue d'ensemble de TableAdapter](../data-tools/tableadapter-overview.md)   
 [Comment : mettre à jour les données à l'aide d'un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)   
 [Vue d'ensemble d'applications de données dans Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Connexion aux données dans Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Préparation de votre application pour recevoir des données](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Extraction de données dans votre application](../data-tools/fetching-data-into-your-application.md)   
 [Liaison de contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modification des données dans votre application](../data-tools/editing-data-in-your-application.md)   
 [Validation des données](../Topic/Validating%20Data.md)   
 [Enregistrement des données](../data-tools/saving-data.md)