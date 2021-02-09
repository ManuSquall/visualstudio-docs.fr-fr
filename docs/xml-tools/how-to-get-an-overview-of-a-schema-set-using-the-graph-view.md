---
title: Obtenir une vue d’ensemble d’un jeu de schémas
description: 'Concepteur de schémas XML : Découvrez comment utiliser la vue du graphique dans l’Explorateur de schémas XML pour afficher une vue d’ensemble des nœuds d’un jeu de schémas et les relations entre les nœuds.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c0df4b0d-52ef-4a6c-9676-1d8311aad7c7
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 896522f6d7f057d359cb5502c42edf34d0a2d823
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897454"
---
# <a name="how-to-get-an-overview-of-a-schema-set-by-using-the-graph-view"></a>Comment : obtenir une vue d’ensemble d’un jeu de schémas à l’aide de la vue du graphique

Cette rubrique explique comment utiliser la [vue du graphique](../xml-tools/graph-view.md) pour afficher une vue de haut niveau des nœuds dans un jeu de schémas et les relations entre les nœuds.

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Pour créer un fichier XSD et afficher l'élément racine dans la vue de modèle de contenu

1. Créez un fichier de schéma XML et enregistrez le fichier en tant que *Relationships. xsd*.

2. Cliquez sur le lien **utiliser l’éditeur XML pour afficher et modifier le fichier de schéma XML sous-jacent** dans la vue de départ.

3. Copiez l’exemple de code XML à partir de [exemple de schéma XML : relations](../xml-tools/sample-xsd-file-relationships.md) , puis collez-le pour remplacer le code qui a été ajouté par défaut au nouveau fichier XSD.

4. Cliquez avec le bouton droit n’importe où dans l’éditeur XML et sélectionnez **Concepteur de vues**.

5. Sélectionnez la vue du graphique dans la **barre d’outils XSD**.

6. Sélectionnez nœud du **jeu de schémas** dans l' **Explorateur de schémas XML** et faites glisser le nœud sur l’aire de conception de la vue du graphique. Tous les nœuds globaux doivent apparaître, ainsi que les flèches connectant les nœuds qui ont des relations.

     ![Vue Graphique](../xml-tools/media/relationshipingraphview.gif)

7. Cliquez sur n'importe quel nœud sur l'aire de conception, puis examinez la barre de fil d'Ariane (breadcrumb) pour déterminer l'emplacement du nœud sélectionné dans le jeu de schémas.

8. Rick-cliquez sur un nœud d’élément sur l’aire de conception, puis sélectionnez **générer un exemple de code XML** pour afficher le document de l’instance XML.
