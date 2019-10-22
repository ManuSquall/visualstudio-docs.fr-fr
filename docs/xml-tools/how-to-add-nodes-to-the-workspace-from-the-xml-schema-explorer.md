---
title: Ajouter des nœuds à l’espace de travail à partir de l’Explorateur de schémas XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3b5a5749-9693-4b29-b0c2-8e07e0e55514
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 77e1890df09443e133f9e528905b76374f6070bc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646039"
---
# <a name="how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer"></a>Procédure : ajouter des nœuds à l’espace de travail à partir de l’Explorateur de schémas XML

Cette rubrique explique comment ajouter des nœuds à l' [espace de travail du concepteur de schémas XML](../xml-tools/xml-schema-designer-workspace.md) à partir de l’Explorateur de **schémas XML**. Pour ce faire, vous pouvez faire glisser et déposer des nœuds de l' **Explorateur de schémas XML** vers une vue du concepteur XSD, ou en utilisant le menu contextuel **de l’Explorateur de schémas XML** . Vous pouvez également ajouter des nœuds mis en surbrillance suite à une recherche effectuée par l' **Explorateur de schémas XML**. Pour plus d’informations, consultez [Comment : ajouter des nœuds de résultat de recherche de jeu de schémas à l’espace de travail](../xml-tools/how-to-add-schema-set-search-result-nodes-to-the-workspace.md).

> [!NOTE]
> Seuls les nœuds globaux peuvent être ajoutés à l' [espace de travail du concepteur de schémas XML](../xml-tools/xml-schema-designer-workspace.md).

## <a name="to-add-nodes-through-the-xml-explorer-context-menu"></a>Pour ajouter des nœuds via le menu contextuel de l’Explorateur XML

1. Suivez les étapes décrites dans [Comment : créer et modifier un fichier de schéma XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2. Cliquez avec le bouton droit sur le nœud `PurchaseOrderType` dans l’Explorateur XSD. Sélectionnez **afficher dans la vue du graphique**.

     Le nœud `purchaseOrderType` apparaît sur l'aire de conception de la vue du graphique.

## <a name="to-drag-and-drop-a-node-on-to-a-view"></a>Pour faire glisser-déplacer un nœud sur une vue

1. Cliquez avec le bouton droit sur le nœud `PurchaseOrderType` dans la vue du graphique. Sélectionnez **afficher dans l’Explorateur de schémas XML**.

     Le nœud est mis en surbrillance dans l' **Explorateur de schémas XML**.

2. Cliquez avec le bouton droit sur le nœud `PurchaseOrderType` dans l **'Explorateur de schémas XML** , puis sélectionnez **afficher toutes les références**.

     Le nœud `purchaseOrder` est mis en surbrillance.

3. Faites glisser le nœud `purchaseOrder` sur la vue du graphique.

     Le nœud `purchaseOrder` et le nœud `PurchaseOrderType` apparaissent en regard l'un de l'autre sur l'aire de conception de la vue du graphique. Étant donné que les deux nœuds sont associés (l'élément `purchaseOrder` est du type `PurchaseOrderType`), une flèche est dessinée entre eux.

## <a name="to-add-nodes-using-the-schema-explorer-search-capability"></a>Pour ajouter des nœuds à l'aide de la fonction de recherche de l'Explorateur de schémas

1. Tapez « purchaseOrder » dans la zone de texte Rechercher de la barre d’outils de l' [Explorateur XML](../xml-tools/xml-schema-explorer.md) , puis cliquez sur le bouton Rechercher.

     ![Recherche par mot clé de l'Explorateur de schémas XML](../xml-tools/media/schemaexplorersearch.gif)

     Les résultats de la recherche sont mis en surbrillance dans l' **Explorateur de schémas XML** et marqués par des graduations sur la barre de défilement verticale.

2. Ajoutez les résultats de la recherche à l’espace de travail en cliquant sur le bouton **Ajouter les nœuds en surbrillance à l’espace de travail** dans le volet de synthèse des résultats.

     ![Résultat de la recherche de l'Explorateur de schémas XML](../xml-tools/media/schemaexplorersearchresult.gif)

     Le nœud `purchaseOrder` et le nœud `PurchaseOrderType` s’affichent à côté l’un de l’autre sur l’aire de conception de la [vue du graphique](../xml-tools/graph-view.md). Étant donné que les deux nœuds sont associés (l'élément `purchaseOrder` est du type `PurchaseOrderType`), une flèche est dessinée entre eux.

## <a name="see-also"></a>Voir aussi

- [Explorateur de schémas XML](../xml-tools/xml-schema-explorer.md)