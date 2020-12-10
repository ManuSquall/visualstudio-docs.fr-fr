---
title: Examiner le modèle de contenu de nœuds
description: Découvrez comment utiliser la vue de modèle de contenu dans le concepteur de schémas XML pour examiner le modèle de contenu des nœuds dans un schéma XML.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c42ddac8-b0e3-48d6-9832-112a19d6c104
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f3ce3d1a47125c446521ceb60a851322c37209d0
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995276"
---
# <a name="how-to-examine-the-content-model-of-nodes-by-using-the-content-model-view"></a>Comment : examiner le modèle de contenu des nœuds à l’aide de la vue de modèle de contenu

Cette rubrique explique comment explorer vos nœuds à l’aide de la [vue de modèle de contenu](../xml-tools/content-model-view.md).

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Pour créer un fichier XSD et afficher l'élément racine dans la vue de modèle de contenu

1. Créez un fichier de schéma XML.

2. Cliquez sur **utiliser l’éditeur XML pour afficher et modifier le fichier de schéma XML sous-jacent** dans la vue de départ.

3. Copiez l’exemple de code XML à partir de exemple de schéma [XML : schéma de bon de commande](../xml-tools/sample-xsd-file-purchase-order-schema.md) , puis collez-le pour remplacer le code qui a été ajouté par défaut au nouveau fichier XSD.

4. Sélectionnez l' `purchaseOrder` élément dans l’Explorateur de schémas en cliquant avec le bouton droit sur l' `purchaseOrder` élément dans l’éditeur XML et en sélectionnant **afficher dans l’Explorateur XML**.

5. Cliquez avec le bouton droit sur `purchaseOrder` dans l’Explorateur XML et sélectionnez **afficher dans la vue de modèle de contenu**.

     La vue de modèle de contenu affiche l'élément `purchaseOrder` sur son aire de conception.

6. Développez les nœuds`shipTo`, `billTo` et `items` en double-cliquant sur chaque nœud ou en cliquant sur la flèche double à droite de chaque nœud.

     Les nœuds de l'élément `purchaseOrder` sont maintenant développés et vous pouvez consulter le modèle de contenu de l'élément.

7. Cliquez sur n'importe quel nœud sous l'élément `purchaseOrder`, puis examinez la barre de fil d'Ariane (breadcrumb) pour déterminer l'emplacement du nœud sélectionné dans le jeu de schémas.

8. Cliquez sur le bouton **afficher la documentation** dans la barre d’outils XSD pour activer ou désactiver la documentation. Vous pouvez également cliquer avec le bouton droit sur l'aire de conception pour basculer vers la documentation.

9. Cliquez avec le bouton droit sur le `purchaseOrder` nœud, puis sélectionnez **générer un exemple de code XML** pour afficher le document de l’instance XML.
