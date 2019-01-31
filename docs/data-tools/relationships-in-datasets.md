---
title: DataRelation permet de créer des relations entre les jeux de données
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 8f349887512cdfb9a98d64b0880eda45ecd5c186
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54970225"
---
# <a name="create-relationships-between-datasets"></a>Créer des relations entre les datasets
Jeux de données qui contiennent des données connexes tables utilisent <xref:System.Data.DataRelation> objets pour représenter une relation parent/enfant entre les tables et pour retourner des enregistrements connexes à partir de l’autre. Ajout de tables associées aux jeux de données à l’aide de la **Assistant de Configuration de Source de données**, ou le **Concepteur de Dataset**, crée et configure le <xref:System.Data.DataRelation> objet pour vous.

Le <xref:System.Data.DataRelation> objet effectue deux fonctions :

-   Elle peut rendre disponible les enregistrements liés à un enregistrement que vous travaillez. Il fournit des enregistrements enfants si vous êtes dans un enregistrement parent (<xref:System.Data.DataRow.GetChildRows%2A>) et un enregistrement parent si vous travaillez avec un enregistrement enfant (<xref:System.Data.DataRow.GetParentRow%2A>).

-   Il peut appliquer des contraintes d’intégrité référentielle, telles que la suppression des enregistrements enfants connexes lorsque vous supprimez un enregistrement parent.

Il est important de comprendre la différence entre une vraie jointure et la fonction d’un <xref:System.Data.DataRelation> objet. Dans une jointure true, les enregistrements des tables parentes et enfants et sont placés dans un seul jeu d’enregistrements. Lorsque vous utilisez un <xref:System.Data.DataRelation> de l’objet, aucun nouveau jeu d’enregistrements n’est créé. Au lieu de cela, le DataRelation effectue le suivi de la relation entre les tables et synchronise les enregistrements parents et enfants.

## <a name="datarelation-objects-and-constraints"></a>Contraintes des objets DataRelation
Un <xref:System.Data.DataRelation> objet est également utilisé pour créer et appliquer les contraintes suivantes :

-   Une contrainte unique, ce qui garantit qu’une colonne dans la table ne contient aucun doublon.

-   Une contrainte de clé étrangère, qui peut être utilisée pour maintenir l’intégrité référentielle entre une table parent et enfant dans un jeu de données.

Les contraintes que vous spécifiez dans un <xref:System.Data.DataRelation> objet sont implémentées en créant les objets appropriés automatiquement ou en définissant des propriétés. Si vous créez une contrainte foreign key à l’aide de la <xref:System.Data.DataRelation> objet, les instances de la <xref:System.Data.ForeignKeyConstraint> classe sont ajoutés à la <xref:System.Data.DataRelation> l’objet <xref:System.Data.DataRelation.ChildKeyConstraint%2A> propriété.

Une contrainte unique est implémentée en définissant simplement le <xref:System.Data.DataColumn.Unique%2A> propriété d’une colonne de données à `true` ou en ajoutant une instance de la <xref:System.Data.UniqueConstraint> classe à la <xref:System.Data.DataRelation> l’objet <xref:System.Data.DataRelation.ParentKeyConstraint%2A> propriété. Pour plus d’informations sur l’interruption de contraintes dans un jeu de données, consultez [désactiver les contraintes pendant le remplissage d’un jeu de données](../data-tools/turn-off-constraints-while-filling-a-dataset.md).

### <a name="referential-integrity-rules"></a>Règles d’intégrité référentielle
Dans le cadre de la contrainte de clé étrangère, vous pouvez spécifier des règles d’intégrité référentielle qui sont appliquées dans trois cas :

-   Lorsqu’un enregistrement parent est mis à jour

-   Lorsqu’un enregistrement parent est supprimé

-   Quand une modification est acceptée ou rejetée

Les règles que vous pouvez apporter sont spécifiés dans le <xref:System.Data.Rule> énumération et sont répertoriées dans le tableau suivant.

|Règle de la contrainte de clé étrangère|Action|
| - |------------|
|<xref:System.Data.Rule.Cascade>|La modification (mise à jour ou suppression) apportée à l’enregistrement parent est également apportée dans les enregistrements associés dans la table enfant.|
|<xref:System.Data.Rule.SetNull>|Enregistrements enfants ne sont pas supprimés, mais la clé étrangère dans les enregistrements enfants est définie <xref:System.DBNull>. Avec ce paramètre, les enregistrements enfants peuvent être laissées en tant que « orphelins », autrement dit, ils n’ont aucune relation avec des enregistrements parents. **Remarque :** À l’aide de cette règle peut entraîner des données non valides dans la table enfant.|
|<xref:System.Data.Rule.SetDefault>|La clé étrangère dans les enregistrements enfants connexes est définie à sa valeur par défaut (comme établi par la colonne <xref:System.Data.DataColumn.DefaultValue%2A> propriété).|
|<xref:System.Data.Rule.None>|Aucune modification est apportée aux enregistrements enfants connexes. Avec ce paramètre, les enregistrements enfants peuvent contenir des références à des enregistrements de parent non valide.|

Pour plus d’informations sur les mises à jour dans les tables de jeu de données, consultez [enregistrer les données dans la base de données](../data-tools/save-data-back-to-the-database.md).

### <a name="constraint-only-relations"></a>Relations de contrainte uniquement
Lorsque vous créez un <xref:System.Data.DataRelation> de l’objet, vous avez la possibilité de spécifier que la relation d’être utilisée que pour appliquer des contraintes, autrement dit, il ne sera pas utilisé pour accéder aux enregistrements connexes. Vous pouvez utiliser cette option pour générer un jeu de données qui est légèrement plus efficace et qui contient des méthodes moins celle avec la fonctionnalité d’enregistrements connexes. Toutefois, vous ne serez pas en mesure d’accéder aux enregistrements connexes. Par exemple, une relation de contrainte uniquement vous empêche de supprimer un enregistrement parent qui a toujours des enregistrements enfants, et vous ne peut pas accéder aux enregistrements enfants par le biais du parent.

## <a name="manually-creating-a-data-relation-in-the-dataset-designer"></a>Création manuelle d’une relation de données dans le Concepteur de Dataset
Lorsque vous créez des tables de données en utilisant les outils de conception de données dans Visual Studio, les relations sont créées automatiquement si les informations peuvent être collectées à partir de la source de vos données. Si vous ajoutez manuellement des tables de données à partir de la **DataSet** onglet de la **boîte à outils**, vous devrez peut-être créer la relation manuellement. Pour plus d’informations sur la création de <xref:System.Data.DataRelation> objets par programme, consultez [Ajout de DataRelations](/dotnet/framework/data/adonet/dataset-datatable-dataview/adding-datarelations).

Relations entre les tables de données apparaissent sous forme de lignes dans le **Concepteur de Dataset**, avec un glyphe de clé et de l’infini représentant l’aspect un-à-plusieurs de la relation. Par défaut, le nom de la relation n’apparaît pas sur l’aire de conception.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-create-a-relationship-between-two-data-tables"></a>Pour créer une relation entre deux tables de données

1.  Ouvrez votre dataset dans le **Concepteur de DataSet**. Pour plus d’informations, consultez [Procédure pas à pas : Création d’un jeu de données dans le Concepteur de Dataset](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2.  Faites glisser un **Relation** de l’objet à partir de la **DataSet** boîte à outils vers la table de données enfant dans la relation.

     Le **Relation** boîte de dialogue s’ouvre, remplissage de la **Table enfant** boîte avec la table que vous avez fait glisser le **Relation** sur l’objet.

3.  Sélectionnez la table parente à partir de la **Table parente** boîte. La table parente contient des enregistrements sur le côté « un » d’une relation un-à-plusieurs.

4.  Vérifiez que la table enfant correcte s’affiche dans le **Table enfant** boîte. La table enfant contient des enregistrements sur le côté « plusieurs » d’une relation un-à-plusieurs.

5.  Tapez un nom pour la relation dans le **nom** zone, ou laissez le nom par défaut basé sur les tables sélectionnées. Ceci est le nom de la valeur réelle <xref:System.Data.DataRelation> objet dans le code.

6.  Sélectionnez les colonnes qui joignent les tables dans le **colonnes clés** et **les colonnes clés étrangères** répertorie.

7.  Indiquez si vous souhaitez créer une relation, contrainte ou les deux.

8.  Activez ou désactivez le **Relation imbriquée** boîte. En sélectionnant cette option définit la <xref:System.Data.DataRelation.Nested%2A> propriété `true`, et entraîne des lignes de la relation d’imbrication dans la colonne parente lorsque ces lignes sont écrites en tant que données XML ou synchronisés avec l’enfant <xref:System.Xml.XmlDataDocument>. Pour plus d’informations, consultez [d’imbrication de DataRelations](/dotnet/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations).

9. Définissez les règles à appliquer lorsque vous apportez des modifications aux enregistrements dans ces tables. Pour plus d'informations, consultez <xref:System.Data.Rule>.

10. Cliquez sur **OK** pour créer la relation. Une ligne de relation s’affiche dans le concepteur entre les deux tables.

#### <a name="to-display-a-relation-name-in-the-dataset-designer"></a>Pour afficher un nom de relation dans le Concepteur de Dataset

1.  Ouvrez votre dataset dans le **Concepteur de DataSet**. Pour plus d’informations, consultez [Procédure pas à pas : Création d’un jeu de données dans le Concepteur de Dataset](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2.  À partir de la **données** menu, sélectionnez le **afficher les étiquettes de Relation** commande pour afficher le nom de la relation. Désactivez cette commande pour masquer le nom de la relation.

## <a name="see-also"></a>Voir aussi

- [Créer et configurer des datasets dans Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)