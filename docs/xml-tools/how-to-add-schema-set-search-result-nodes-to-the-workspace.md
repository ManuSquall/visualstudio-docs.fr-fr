---
title: Ajouter des nœuds de résultat de recherche de jeu de schémas
description: Découvrez comment ajouter des nœuds mis en surbrillance dans l’Explorateur de schémas XML suite à une recherche par mot clé dans l’espace de travail.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cffced7a0b680932a1f2b17bd1261e160563462c
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996277"
---
# <a name="how-to-add-schema-set-search-result-nodes-to-the-workspace"></a>Comment : ajouter des nœuds de résultat de recherche de jeu de schémas à l’espace de travail

Cette rubrique explique comment ajouter des nœuds mis en surbrillance dans l' **Explorateur de schémas XML** suite à une recherche par mot clé dans l’espace de travail.

> [!NOTE]
> Seuls les nœuds globaux peuvent être ajoutés à l' [espace de travail](../xml-tools/xml-schema-designer-workspace.md).

Cet exemple utilise l’exemple de [schéma de bon de commande](../xml-tools/sample-xsd-file-purchase-order-schema.md).

## <a name="to-add-schema-set-result-nodes"></a>Pour ajouter des nœuds de résultat de jeu de schémas

1. Suivez les étapes décrites dans [Comment : créer et modifier un fichier de schéma XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2. Tapez « purchaseOrder » dans la zone de texte Rechercher de la barre d’outils de l' [Explorateur XML](../xml-tools/xml-schema-explorer.md) , puis cliquez sur le bouton Rechercher.

     ![Recherche par mot clé de l'Explorateur de schémas XML](../xml-tools/media/schemaexplorersearch.gif)

     Les résultats de la recherche sont mis en surbrillance dans l' **Explorateur de schémas XML** et marqués par des graduations sur la barre de défilement verticale.

3. Ajoutez les résultats de la recherche à l’espace de travail en cliquant sur le bouton **Ajouter les nœuds en surbrillance à l’espace de travail** dans le volet de synthèse des résultats.

     ![Résultat de la recherche dans l'Explorateur de schémas XML](../xml-tools/media/schemaexplorersearchresult.gif)

     Le `purchaseOrder` nœud et le `PurchaseOrderType` nœud apparaissent en regard l’un de l’autre sur l’aire de conception de la [vue du graphique](../xml-tools/graph-view.md). Étant donné que les deux nœuds sont associés (l'élément `purchaseOrder` est du type `PurchaseOrderType`), une flèche est dessinée entre eux.
