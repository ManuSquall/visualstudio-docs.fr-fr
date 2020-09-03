---
title: Relations dans les jeux de données | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- vbData.Microsoft.VSDesigner.DataSource.DesignRelation
- vbdata.Microsoft.VSDesigner.DataSource.DesignRelation
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- relationships, about relationships
- datasets [Visual Basic], relationships
- relationships, datasets
ms.assetid: cfe274f0-71fe-40f6-994e-7c7f6273c9ba
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: eb13ad7db9a4f13ce9bf983ce6327045f885f4d8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652882"
---
# <a name="relationships-in-datasets"></a>Relations dans les datasets
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les jeux de données qui contiennent des tables de données associées utilisent des <xref:System.Data.DataRelation> objets pour représenter une relation parent/enfant entre les tables et pour retourner les enregistrements associés les uns des autres. L’ajout de tables associées à des jeux de données à l’aide de l' **Assistant Configuration de source de données**, ou du **Concepteur de DataSet**, crée et configure l' <xref:System.Data.DataRelation> objet pour vous.

 L' <xref:System.Data.DataRelation> objet exécute deux fonctions :

- Il peut mettre à disposition les enregistrements associés à un enregistrement que vous utilisez. Il fournit des enregistrements enfants si vous êtes dans un enregistrement parent ( <xref:System.Data.DataRow.GetChildRows%2A> ) et un enregistrement parent si vous utilisez un enregistrement enfant ( <xref:System.Data.DataRow.GetParentRow%2A> ).

- Il peut appliquer des contraintes pour l’intégrité référentielle, telles que la suppression d’enregistrements enfants connexes lorsque vous supprimez un enregistrement parent.

  Il est important de comprendre la différence entre une jointure réelle et la fonction d’un <xref:System.Data.DataRelation> objet. Dans une vraie jointure, les enregistrements sont extraits des tables parent et enfant et placés dans un seul jeu d’enregistrements plat. Quand vous utilisez un <xref:System.Data.DataRelation> objet, aucun jeu d’enregistrements n’est créé. Au lieu de cela, le DataRelation effectue le suivi de la relation entre les tables et conserve la synchronisation des enregistrements parents et enfants.

## <a name="datarelation-objects-and-constraints"></a>Contraintes et objets DataRelation
 Un <xref:System.Data.DataRelation> objet est également utilisé pour créer et appliquer les contraintes suivantes :

- Contrainte unique qui garantit qu’une colonne de la table ne contient pas de doublons.

- Contrainte de clé étrangère, qui peut être utilisée pour maintenir l’intégrité référentielle entre une table parente et une table enfant dans un DataSet.

  Les contraintes que vous spécifiez dans un <xref:System.Data.DataRelation> objet sont implémentées en créant automatiquement des objets appropriés ou des propriétés de définition. Si vous créez une contrainte de clé étrangère à l’aide de l' <xref:System.Data.DataRelation> objet, les instances de la <xref:System.Data.ForeignKeyConstraint> classe sont ajoutées à la <xref:System.Data.DataRelation> propriété de l’objet <xref:System.Data.DataRelation.ChildKeyConstraint%2A> .

  Une contrainte unique est implémentée en affectant simplement à la <xref:System.Data.DataColumn.Unique%2A> propriété d’une colonne de données la valeur `true` ou en ajoutant une instance de la <xref:System.Data.UniqueConstraint> classe à la propriété de l' <xref:System.Data.DataRelation> objet <xref:System.Data.DataRelation.ParentKeyConstraint%2A> . Pour plus d’informations sur l’interruption des contraintes dans un jeu de données, consultez [Désactiver les contraintes lors du remplissage d’un DataSet](../data-tools/turn-off-constraints-while-filling-a-dataset.md).

### <a name="referential-integrity-rules"></a>Règles d’intégrité référentielle
 Dans le cadre de la contrainte de clé étrangère, vous pouvez spécifier des règles d’intégrité référentielle qui sont appliquées à trois points :

- Quand un enregistrement parent est mis à jour

- Lors de la suppression d’un enregistrement parent

- Quand une modification est acceptée ou rejetée

  Les règles que vous pouvez définir sont spécifiées dans l' <xref:System.Data.Rule> énumération et sont répertoriées dans le tableau suivant.

|Règle de contrainte de clé étrangère|Action|
|----------------------------------|------------|
|<xref:System.Data.Rule>|La modification (mise à jour ou suppression) apportée à l’enregistrement parent est également apportée aux enregistrements associés dans la table enfant.|
|<xref:System.Data.Rule>|Les enregistrements enfants ne sont pas supprimés, mais la clé étrangère dans les enregistrements enfants a la valeur <xref:System.DBNull> . Avec ce paramètre, les enregistrements enfants peuvent être laissés comme des « orphelins », c’est-à-dire qu’ils n’ont aucune relation avec les enregistrements parents. **Remarque :**  L’utilisation de cette règle peut entraîner des données non valides dans la table enfant.|
|<xref:System.Data.Rule>|La clé étrangère dans les enregistrements enfants associés est définie sur sa valeur par défaut (telle que définie par la propriété de la colonne <xref:System.Data.DataColumn.DefaultValue%2A> ).|
|<xref:System.Data.Rule>|Aucune modification n’est apportée aux enregistrements enfants associés. Avec ce paramètre, les enregistrements enfants peuvent contenir des références à des enregistrements parents non valides.|

 Pour plus d’informations sur les mises à jour dans les tables de DataSet, consultez [enregistrer des données dans la base de données](../data-tools/save-data-back-to-the-database.md).

### <a name="constraint-only-relations"></a>Relations de contrainte uniquement
 Lorsque vous créez un <xref:System.Data.DataRelation> objet, vous avez la possibilité de spécifier que la relation doit être utilisée uniquement pour appliquer des contraintes, c’est-à-dire qu’elle ne sera pas également utilisée pour accéder aux enregistrements associés. Vous pouvez utiliser cette option pour générer un jeu de données qui est légèrement plus efficace et qui contient moins de méthodes que l’autre avec la fonction related-Records. Toutefois, vous ne pourrez pas accéder aux enregistrements associés. Par exemple, une relation de contrainte uniquement vous empêche de supprimer un enregistrement parent qui possède encore des enregistrements enfants, et vous ne pouvez pas accéder aux enregistrements enfants par le biais du parent.

## <a name="manually-creating-a-data-relation-in-the-dataset-designer"></a>Création manuelle d’une relation de données dans le Concepteur de DataSet
 Lorsque vous créez des tables de données à l’aide des outils de conception de données dans Visual Studio, les relations sont créées automatiquement si les informations peuvent être collectées à partir de la source de vos données. Si vous ajoutez manuellement des tables de données à partir de l’onglet **DataSet** de la **boîte à outils**, vous devrez peut-être créer la relation manuellement. Pour plus d’informations sur la création d' <xref:System.Data.DataRelation> objets par programme, consultez [Ajout de DataRelations](https://msdn.microsoft.com/library/a4a564fb-c1c4-4135-b6c2-b030e51195e4).

 Les relations entre les tables de données apparaissent sous forme de lignes dans le **Concepteur de DataSet**, avec une clé et un glyphe infini représentant l’aspect un-à-plusieurs de la relation. Par défaut, le nom de relationshipCommentEnd ID = ' 1c8c78e19b7fa441 'n’apparaît pas sur l’aire de conception.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-create-a-relationship-between-two-data-tables"></a>Pour créer une relation entre deux tables de données

1. Ouvrez votre dataset dans le **Concepteur de DataSet**. Pour plus d’informations, consultez [Comment : ouvrir un DataSet dans le concepteur de DataSet](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).

2. Faites glisser un objet **relation** de la boîte à outils **DataSet** vers la table de données enfant dans la relation.

     La boîte de dialogue **relation** s’ouvre et remplit la zone **table enfant** avec la table sur laquelle vous avez fait glisser l’objet **relation** .

3. Sélectionnez la table parent dans la zone **table parente** . La table parente contient des enregistrements du côté « un » d’une relation un-à-plusieurs.

4. Vérifiez que la table enfant correcte est affichée dans la zone **table enfant** . La table enfant contient des enregistrements du côté « plusieurs » d’une relation un-à-plusieurs.

5. Tapez un nom pour la relation dans la zone **nom** , ou laissez le nom par défaut basé sur les tables sélectionnées. Il s’agit du nom de l' <xref:System.Data.DataRelation> objet réel dans le code.

6. Sélectionnez les colonnes qui joignent les tables dans les listes colonnes **clés** et **colonnes clés étrangères** .

7. Indiquez si vous souhaitez créer une relation, une contrainte ou les deux. Pour plus d’informations, consultez [Introduction aux objets DataRelation](https://msdn.microsoft.com/library/89d8a881-8265-41f2-a88b-61311ab06192).

8. Activez ou désactivez la case à cocher **relation imbriquée** . La sélection de cette option affecte la valeur <xref:System.Data.DataRelation.Nested%2A> à la propriété `true` et entraîne l’imbrication des lignes enfants de la relation dans la colonne parent lorsque ces lignes sont écrites sous forme de données XML ou synchronisées avec <xref:System.Xml.XmlDataDocument> . Pour plus d’informations, consultez [imbrication de DataRelations](https://msdn.microsoft.com/library/9530f9c9-dd98-4b93-8cdb-40d7f1e8d0ab).

9. Définissez les règles à appliquer lorsque vous apportez des modifications aux enregistrements de ces tables. Pour plus d'informations, consultez <xref:System.Data.Rule>.

10. Cliquez sur **OK** pour créer la relation. Une ligne de relation apparaît sur le concepteur entre les deux tables.

#### <a name="to-display-a-relation-name-in-the-dataset-designer"></a>Pour afficher un nom de relation dans le Concepteur de DataSet

1. Ouvrez votre dataset dans le **Concepteur de DataSet**. Pour plus d’informations, consultez [Comment : ouvrir un DataSet dans le concepteur de DataSet](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).

2. Dans le menu **données** , sélectionnez la commande **afficher les étiquettes de relation** pour afficher le nom de la relation. Effacez cette commande pour masquer le nom de la relation.
