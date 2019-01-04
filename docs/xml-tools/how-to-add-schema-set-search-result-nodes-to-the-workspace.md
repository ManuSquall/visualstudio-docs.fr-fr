---
title: Ajouter des nœuds de résultats de recherche de jeu de schémas XML à l’espace de travail
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9e9f004943474f9b1c0fb449c1aec23f70034c3a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53875032"
---
# <a name="how-to-add-schema-set-search-result-nodes-to-the-workspace"></a>Procédure : Ajouter des nœuds de résultat de recherche de jeu de schémas à l’espace de travail

Cette rubrique explique comment ajouter des nœuds qui sont mises en surbrillance dans le **Explorateur de schémas XML** comme résultat d’une recherche par mot clé dans l’espace de travail.

> [!NOTE]
> Seuls des nœuds globaux peuvent être ajoutés à la [espace de travail](../xml-tools/xml-schema-designer-workspace.md).


 Cet exemple utilise l’exemple [schéma d’ordre d’achat](../xml-tools/sample-xsd-file-purchase-order-schema.md).

## <a name="to-add-schema-set-result-nodes"></a>Pour ajouter des nœuds de résultat de jeu de schémas

1.  Suivez les étapes de [Comment : Créer et modifier un fichier de schéma XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2.  Tapez « purchaseOrder » dans la zone de texte de recherche de la [Explorateur XML](../xml-tools/xml-schema-explorer.md) barre d’outils et cliquez sur le bouton de recherche.

     ![Recherche par mot clé de l'Explorateur de schémas XML](../xml-tools/media/schemaexplorersearch.gif)

     Les résultats de recherche sont mis en surbrillance dans le **Explorateur de schémas XML** et marqués par des graduations sur la barre de défilement verticale.

3.  Ajouter les résultats de recherche à l’espace de travail en cliquant sur le **ajouter des nœuds en surbrillance à l’espace de travail** bouton dans le volet de synthèse des résultats.

     ![Résultat de la recherche de l'Explorateur de schémas XML](../xml-tools/media/schemaexplorersearchresult.gif)

     Le `purchaseOrder` nœud et le `PurchaseOrderType` nœud apparaissent en regard de chacun des autres sur l’aire de conception de la [vue du graphique](../xml-tools/graph-view.md). Étant donné que les deux nœuds sont associés (l'élément `purchaseOrder` est du type `PurchaseOrderType`), une flèche est dessinée entre eux.