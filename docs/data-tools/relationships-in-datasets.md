---
title: Utiliser DataRelation pour créer des relations entre les jeux de données
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vbData.Microsoft.VSDesigner.DataSource.DesignRelation
- vbdata.Microsoft.VSDesigner.DataSource.DesignRelation
helpviewer_keywords:
- relationships, about relationships
- datasets [Visual Basic], relationships
- relationships, datasets
ms.assetid: cfe274f0-71fe-40f6-994e-7c7f6273c9ba
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: a9d733892b3bc62c272f31b0d7cc1aa10fbf229d
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586313"
---
# <a name="create-relationships-between-datasets"></a>Créer des relations entre les datasets
Les jeux de données qui contiennent des tables de données associées utilisent des objets <xref:System.Data.DataRelation> pour représenter une relation parent/enfant entre les tables et pour retourner les enregistrements associés les uns des autres. L’ajout de tables associées à des jeux de données à l’aide de l' **Assistant Configuration de source de données**, ou du **Concepteur de DataSet**, crée et configure l’objet <xref:System.Data.DataRelation> pour vous.

L’objet <xref:System.Data.DataRelation> exécute deux fonctions :

- Il peut mettre à disposition les enregistrements associés à un enregistrement que vous utilisez. Il fournit des enregistrements enfants si vous êtes dans un enregistrement parent (<xref:System.Data.DataRow.GetChildRows%2A>) et un enregistrement parent si vous utilisez un enregistrement enfant (<xref:System.Data.DataRow.GetParentRow%2A>).

- Il peut appliquer des contraintes pour l’intégrité référentielle, telles que la suppression d’enregistrements enfants connexes lorsque vous supprimez un enregistrement parent.

Il est important de comprendre la différence entre une jointure réelle et la fonction d’un objet <xref:System.Data.DataRelation>. Dans une vraie jointure, les enregistrements sont extraits des tables parent et enfant et placés dans un seul jeu d’enregistrements plat. Quand vous utilisez un objet <xref:System.Data.DataRelation>, aucun jeu d’enregistrements n’est créé. Au lieu de cela, le DataRelation effectue le suivi de la relation entre les tables et conserve la synchronisation des enregistrements parents et enfants.

## <a name="datarelation-objects-and-constraints"></a>Contraintes et objets DataRelation
Un objet <xref:System.Data.DataRelation> est également utilisé pour créer et appliquer les contraintes suivantes :

- Contrainte unique qui garantit qu’une colonne de la table ne contient pas de doublons.

- Contrainte de clé étrangère, qui peut être utilisée pour maintenir l’intégrité référentielle entre une table parente et une table enfant dans un DataSet.

Les contraintes que vous spécifiez dans un objet <xref:System.Data.DataRelation> sont implémentées en créant automatiquement des objets appropriés ou des propriétés de définition. Si vous créez une contrainte de clé étrangère à l’aide de l’objet <xref:System.Data.DataRelation>, les instances de la classe <xref:System.Data.ForeignKeyConstraint> sont ajoutées à la propriété <xref:System.Data.DataRelation.ChildKeyConstraint%2A> de l’objet <xref:System.Data.DataRelation>.

Une contrainte unique est implémentée soit en définissant simplement la propriété <xref:System.Data.DataColumn.Unique%2A> d’une colonne de données sur `true`, soit en ajoutant une instance de la classe <xref:System.Data.UniqueConstraint> à la propriété <xref:System.Data.DataRelation.ParentKeyConstraint%2A> de l’objet <xref:System.Data.DataRelation>. Pour plus d’informations sur l’interruption des contraintes dans un jeu de données, consultez [Désactiver les contraintes lors du remplissage d’un DataSet](../data-tools/turn-off-constraints-while-filling-a-dataset.md).

### <a name="referential-integrity-rules"></a>Règles d’intégrité référentielle
Dans le cadre de la contrainte de clé étrangère, vous pouvez spécifier des règles d’intégrité référentielle qui sont appliquées à trois points :

- Quand un enregistrement parent est mis à jour

- Lors de la suppression d’un enregistrement parent

- Quand une modification est acceptée ou rejetée

Les règles que vous pouvez définir sont spécifiées dans l’énumération <xref:System.Data.Rule> et sont répertoriées dans le tableau suivant.

|Règle de contrainte de clé étrangère|Action|
| - |------------|
|<xref:System.Data.Rule.Cascade>|La modification (mise à jour ou suppression) apportée à l’enregistrement parent est également apportée aux enregistrements associés dans la table enfant.|
|<xref:System.Data.Rule.SetNull>|Les enregistrements enfants ne sont pas supprimés, mais la clé étrangère dans les enregistrements enfants est définie sur <xref:System.DBNull>. Avec ce paramètre, les enregistrements enfants peuvent être laissés comme des « orphelins », c’est-à-dire qu’ils n’ont aucune relation avec les enregistrements parents. **Remarque :** L’utilisation de cette règle peut entraîner des données non valides dans la table enfant.|
|<xref:System.Data.Rule.SetDefault>|La clé étrangère dans les enregistrements enfants associés est définie sur sa valeur par défaut (telle que définie par la propriété <xref:System.Data.DataColumn.DefaultValue%2A> de la colonne).|
|<xref:System.Data.Rule.None>|Aucune modification n’est apportée aux enregistrements enfants associés. Avec ce paramètre, les enregistrements enfants peuvent contenir des références à des enregistrements parents non valides.|

Pour plus d’informations sur les mises à jour dans les tables de DataSet, consultez [enregistrer des données dans la base de données](../data-tools/save-data-back-to-the-database.md).

### <a name="constraint-only-relations"></a>Relations de contrainte uniquement
Lorsque vous créez un objet <xref:System.Data.DataRelation>, vous avez la possibilité de spécifier que la relation doit être utilisée uniquement pour appliquer des contraintes, c’est-à-dire qu’elle ne sera pas également utilisée pour accéder aux enregistrements associés. Vous pouvez utiliser cette option pour générer un jeu de données qui est légèrement plus efficace et qui contient moins de méthodes que l’autre avec la fonction related-Records. Toutefois, vous ne pourrez pas accéder aux enregistrements associés. Par exemple, une relation de contrainte uniquement vous empêche de supprimer un enregistrement parent qui possède encore des enregistrements enfants, et vous ne pouvez pas accéder aux enregistrements enfants par le biais du parent.

## <a name="manually-creating-a-data-relation-in-the-dataset-designer"></a>Création manuelle d’une relation de données dans le Concepteur de DataSet
Lorsque vous créez des tables de données à l’aide des outils de conception de données dans Visual Studio, les relations sont créées automatiquement si les informations peuvent être collectées à partir de la source de vos données. Si vous ajoutez manuellement des tables de données à partir de l’onglet **DataSet** de la **boîte à outils**, vous devrez peut-être créer la relation manuellement. Pour plus d’informations sur la création d’objets <xref:System.Data.DataRelation> par programme, consultez [Ajout de DataRelations](/dotnet/framework/data/adonet/dataset-datatable-dataview/adding-datarelations).

Les relations entre les tables de données apparaissent sous forme de lignes dans le **Concepteur de DataSet**, avec une clé et un glyphe infini représentant l’aspect un-à-plusieurs de la relation. Par défaut, le nom de la relation n’apparaît pas sur l’aire de conception.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-create-a-relationship-between-two-data-tables"></a>Pour créer une relation entre deux tables de données

1. Ouvrez votre dataset dans le **Concepteur de DataSet**. Pour plus d’informations, consultez [procédure pas à pas : création d’un DataSet dans le concepteur de DataSet](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. Faites glisser un objet **relation** de la boîte à outils **DataSet** vers la table de données enfant dans la relation.

     La boîte de dialogue **relation** s’ouvre et remplit la zone **table enfant** avec la table sur laquelle vous avez fait glisser l’objet **relation** .

3. Sélectionnez la table parent dans la zone **table parente** . La table parente contient des enregistrements du côté « un » d’une relation un-à-plusieurs.

4. Vérifiez que la table enfant correcte est affichée dans la zone **table enfant** . La table enfant contient des enregistrements du côté « plusieurs » d’une relation un-à-plusieurs.

5. Tapez un nom pour la relation dans la zone **nom** , ou laissez le nom par défaut basé sur les tables sélectionnées. Il s’agit du nom de l’objet <xref:System.Data.DataRelation> réel dans le code.

6. Sélectionnez les colonnes qui joignent les tables dans les listes colonnes **clés** et **colonnes clés étrangères** .

7. Indiquez si vous souhaitez créer une relation, une contrainte ou les deux.

8. Activez ou désactivez la case à cocher **relation imbriquée** . La sélection de cette option affecte à la propriété <xref:System.Data.DataRelation.Nested%2A> la valeur `true`et entraîne l’imbrication des lignes enfants de la relation dans la colonne parent lorsque ces lignes sont écrites sous forme de données XML ou synchronisées avec <xref:System.Xml.XmlDataDocument>. Pour plus d’informations, consultez [imbrication de DataRelations](/dotnet/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations).

9. Définissez les règles à appliquer lorsque vous apportez des modifications aux enregistrements de ces tables. Pour plus d'informations, consultez <xref:System.Data.Rule>.

10. Cliquez sur **OK** pour créer la relation. Une ligne de relation apparaît sur le concepteur entre les deux tables.

#### <a name="to-display-a-relation-name-in-the-dataset-designer"></a>Pour afficher un nom de relation dans le Concepteur de DataSet

1. Ouvrez votre dataset dans le **Concepteur de DataSet**. Pour plus d’informations, consultez [procédure pas à pas : création d’un DataSet dans le concepteur de DataSet](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. Dans le menu **données** , sélectionnez la commande **afficher les étiquettes de relation** pour afficher le nom de la relation. Effacez cette commande pour masquer le nom de la relation.

## <a name="see-also"></a>Voir aussi

- [Créer et configurer des datasets dans Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)
