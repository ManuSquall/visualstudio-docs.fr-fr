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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9991adc9d770487c646c97da81b6245ae65ba5f5
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60075374"
---
# <a name="relationships-in-datasets"></a>Relations dans les jeux de données
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeux de données qui contiennent des données connexes tables utilisent <xref:System.Data.DataRelation> objets pour représenter une relation parent/enfant entre les tables et pour retourner des enregistrements connexes à partir de l’autre. Ajout de tables associées aux jeux de données à l’aide de la **Assistant de Configuration de Source de données**, ou le **Concepteur de Dataset**, crée et configure le <xref:System.Data.DataRelation> objet pour vous.  
  
 Le <xref:System.Data.DataRelation> objet effectue deux fonctions :  
  
- Elle peut rendre disponible les enregistrements liés à un enregistrement que vous travaillez. Il fournit des enregistrements enfants si vous êtes dans un enregistrement parent (<xref:System.Data.DataRow.GetChildRows%2A>) et un enregistrement parent si vous travaillez avec un enregistrement enfant (<xref:System.Data.DataRow.GetParentRow%2A>).  
  
- Il peut appliquer des contraintes d’intégrité référentielle, telles que la suppression des enregistrements enfants connexes lorsque vous supprimez un enregistrement parent.  
  
  Il est important de comprendre la différence entre une vraie jointure et la fonction d’un <xref:System.Data.DataRelation> objet. Dans une jointure true, les enregistrements des tables parentes et enfants et sont placés dans un seul jeu d’enregistrements. Lorsque vous utilisez un <xref:System.Data.DataRelation> de l’objet, aucun nouveau jeu d’enregistrements n’est créé. Au lieu de cela, le DataRelation effectue le suivi de la relation entre les tables et synchronise les enregistrements parents et enfants.  
  
## <a name="datarelation-objects-and-constraints"></a>Contraintes des objets DataRelation  
 Un <xref:System.Data.DataRelation> objet est également utilisé pour créer et appliquer les contraintes suivantes :  
  
- Une contrainte unique, ce qui garantit qu’une colonne dans la table ne contient aucun doublon.  
  
- Une contrainte de clé étrangère, qui peut être utilisée pour maintenir l’intégrité référentielle entre une table parent et enfant dans un jeu de données.  
  
  Les contraintes que vous spécifiez dans un <xref:System.Data.DataRelation> objet sont implémentées en créant les objets appropriés automatiquement ou en définissant des propriétés. Si vous créez une contrainte foreign key à l’aide de la <xref:System.Data.DataRelation> objet, les instances de la <xref:System.Data.ForeignKeyConstraint> classe sont ajoutés à la <xref:System.Data.DataRelation> l’objet <xref:System.Data.DataRelation.ChildKeyConstraint%2A> propriété.  
  
  Une contrainte unique est implémentée en définissant simplement le <xref:System.Data.DataColumn.Unique%2A> propriété d’une colonne de données à `true` ou en ajoutant une instance de la <xref:System.Data.UniqueConstraint> classe à la <xref:System.Data.DataRelation> l’objet <xref:System.Data.DataRelation.ParentKeyConstraint%2A> propriété. Pour plus d’informations sur l’interruption de contraintes dans un jeu de données, consultez [désactiver les contraintes pendant le remplissage d’un jeu de données](../data-tools/turn-off-constraints-while-filling-a-dataset.md).  
  
### <a name="referential-integrity-rules"></a>Règles d’intégrité référentielle  
 Dans le cadre de la contrainte de clé étrangère, vous pouvez spécifier des règles d’intégrité référentielle qui sont appliquées dans trois cas :  
  
- Lorsqu’un enregistrement parent est mis à jour  
  
- Lorsqu’un enregistrement parent est supprimé  
  
- Quand une modification est acceptée ou rejetée  
  
  Les règles que vous pouvez apporter sont spécifiés dans le <xref:System.Data.Rule> énumération et sont répertoriées dans le tableau suivant.  
  
|Règle de la contrainte de clé étrangère|Action|  
|----------------------------------|------------|  
|<xref:System.Data.Rule>|La modification (mise à jour ou suppression) apportée à l’enregistrement parent est également apportée dans les enregistrements associés dans la table enfant.|  
|<xref:System.Data.Rule>|Enregistrements enfants ne sont pas supprimés, mais la clé étrangère dans les enregistrements enfants est définie <xref:System.DBNull>. Avec ce paramètre, les enregistrements enfants peuvent être laissées en tant que « orphelins », autrement dit, ils n’ont aucune relation avec des enregistrements parents. **Remarque :**  À l’aide de cette règle peut entraîner des données non valides dans la table enfant.|  
|<xref:System.Data.Rule>|La clé étrangère dans les enregistrements enfants connexes est définie à sa valeur par défaut (comme établi par la colonne <xref:System.Data.DataColumn.DefaultValue%2A> propriété).|  
|<xref:System.Data.Rule>|Aucune modification est apportée aux enregistrements enfants connexes. Avec ce paramètre, les enregistrements enfants peuvent contenir des références à des enregistrements de parent non valide.|  
  
 Pour plus d’informations sur les mises à jour dans les tables de jeu de données, consultez [enregistrer les données dans la base de données](../data-tools/save-data-back-to-the-database.md).  
  
### <a name="constraint-only-relations"></a>Relations de contrainte uniquement  
 Lorsque vous créez un <xref:System.Data.DataRelation> de l’objet, vous avez la possibilité de spécifier que la relation d’être utilisée que pour appliquer des contraintes, autrement dit, il ne sera pas utilisé pour accéder aux enregistrements connexes. Vous pouvez utiliser cette option pour générer un jeu de données qui est légèrement plus efficace et qui contient des méthodes moins celle avec la fonctionnalité d’enregistrements connexes. Toutefois, vous ne serez pas en mesure d’accéder aux enregistrements connexes. Par exemple, une relation de contrainte uniquement vous empêche de supprimer un enregistrement parent qui a toujours des enregistrements enfants, et vous ne peut pas accéder aux enregistrements enfants par le biais du parent.  
  
## <a name="manually-creating-a-data-relation-in-the-dataset-designer"></a>Création manuelle d’une relation de données dans le Concepteur de Dataset  
 Lorsque vous créez des tables de données en utilisant les outils de conception de données dans Visual Studio, les relations sont créées automatiquement si les informations peuvent être collectées à partir de la source de vos données. Si vous ajoutez manuellement des tables de données à partir de la **DataSet** onglet de la **boîte à outils**, vous devrez peut-être créer la relation manuellement. Pour plus d’informations sur la création de <xref:System.Data.DataRelation> objets par programme, consultez [Ajout de DataRelations](http://msdn.microsoft.com/library/a4a564fb-c1c4-4135-b6c2-b030e51195e4).  
  
 Relations entre les tables de données apparaissent sous forme de lignes dans le **Concepteur de Dataset**, avec un glyphe de clé et de l’infini représentant l’aspect un-à-plusieurs de la relation. Par défaut, le nom de la relationshipCommentEnd Id = « 1c8c78e19b7fa441 » n’apparaît pas sur l’aire de conception.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-create-a-relationship-between-two-data-tables"></a>Pour créer une relation entre deux tables de données  
  
1. Ouvrez votre dataset dans le **Concepteur de DataSet**. Pour plus d'informations, voir [Procédure : Ouvrir un jeu de données dans le Concepteur de Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2. Faites glisser un **Relation** de l’objet à partir de la **DataSet** boîte à outils vers la table de données enfant dans la relation.  
  
     Le **Relation** boîte de dialogue s’ouvre, remplissage de la **Table enfant** boîte avec la table que vous avez fait glisser le **Relation** sur l’objet.  
  
3. Sélectionnez la table parente à partir de la **Table parente** boîte. La table parente contient des enregistrements sur le côté « un » d’une relation un-à-plusieurs.  
  
4. Vérifiez que la table enfant correcte s’affiche dans le **Table enfant** boîte. La table enfant contient des enregistrements sur le côté « plusieurs » d’une relation un-à-plusieurs.  
  
5. Tapez un nom pour la relation dans le **nom** zone, ou laissez le nom par défaut basé sur les tables sélectionnées. Ceci est le nom de la valeur réelle <xref:System.Data.DataRelation> objet dans le code.  
  
6. Sélectionnez les colonnes qui joignent les tables dans le **colonnes clés** et **les colonnes clés étrangères** répertorie.  
  
7. Indiquez si vous souhaitez créer une relation, contrainte ou les deux. Pour plus d’informations, consultez [Introduction aux objets DataRelation](http://msdn.microsoft.com/library/89d8a881-8265-41f2-a88b-61311ab06192).  
  
8. Activez ou désactivez le **Relation imbriquée** boîte. En sélectionnant cette option définit la <xref:System.Data.DataRelation.Nested%2A> propriété `true`, et entraîne des lignes de la relation d’imbrication dans la colonne parente lorsque ces lignes sont écrites en tant que données XML ou synchronisés avec l’enfant <xref:System.Xml.XmlDataDocument>. Pour plus d’informations, consultez [d’imbrication de DataRelations](http://msdn.microsoft.com/library/9530f9c9-dd98-4b93-8cdb-40d7f1e8d0ab).  
  
9. Définissez les règles à appliquer lorsque vous apportez des modifications aux enregistrements dans ces tables. Pour plus d'informations, consultez <xref:System.Data.Rule>.  
  
10. Cliquez sur **OK** pour créer la relation. Une ligne de relation s’affiche dans le concepteur entre les deux tables.  
  
#### <a name="to-display-a-relation-name-in-the-dataset-designer"></a>Pour afficher un nom de relation dans le Concepteur de Dataset  
  
1. Ouvrez votre dataset dans le **Concepteur de DataSet**. Pour plus d'informations, voir [Procédure : Ouvrir un jeu de données dans le Concepteur de Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2. À partir de la **données** menu, sélectionnez le **afficher les étiquettes de Relation** commande pour afficher le nom de la relation. Désactivez cette commande pour masquer le nom de la relation.
