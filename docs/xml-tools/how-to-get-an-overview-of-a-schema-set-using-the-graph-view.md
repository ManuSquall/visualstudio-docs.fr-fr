---
title: 'Procédure : Obtenir une vue d’ensemble d’un jeu de schémas à l’aide de la vue du graphique dans le schéma XML Concepteur'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c0df4b0d-52ef-4a6c-9676-1d8311aad7c7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5539f698ba4b4c0998d23e413d2d71ac14e810e7
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60117770"
---
# <a name="how-to-get-an-overview-of-a-schema-set-using-the-graph-view"></a>Procédure : Obtenir une vue d’ensemble d’un schéma défini à l’aide de la vue du graphique

Cette rubrique explique comment utiliser le [vue du graphique](../xml-tools/graph-view.md) pour afficher une vue d’ensemble des nœuds dans un jeu de schémas et les relations entre les nœuds.

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Pour créer un fichier XSD et afficher l'élément racine dans la vue de modèle de contenu

1. Créer un nouveau fichier de schéma XML et enregistrez le fichier sous *Relationships.xsd*.

2. Cliquez sur le **éditeur XML de l’utiliser pour afficher et modifier le fichier de schéma XML sous-jacent** lien sur la vue de départ.

3. Copiez le code d’exemple de schéma XML à partir de [schéma de l’exemple de code XML : relations](../xml-tools/sample-xsd-file-relationships.md) et collez-le pour remplacer le code qui a été ajouté au nouveau fichier XSD par défaut.

4. Avec le bouton droit n’importe où dans l’éditeur XML et sélectionnez **Concepteur de vues**.

5. Sélectionnez la vue du graphique à partir de la **barre d’outils XSD**.

6. Sélectionnez **jeu de schémas** nœud dans le **Explorateur de schémas XML** et faites glisser le nœud à l’aire de conception de la vue du graphique. Tous les nœuds globaux doivent apparaître, ainsi que les flèches connectant les nœuds qui ont des relations.

     ![Vue Graphique](../xml-tools/media/relationshipingraphview.gif)

7. Cliquez sur n'importe quel nœud sur l'aire de conception, puis examinez la barre de fil d'Ariane (breadcrumb) pour déterminer l'emplacement du nœud sélectionné dans le jeu de schémas.

8. Cliquez sur n’importe quel nœud d’élément sur l’aire de conception et sélectionnez **générer un exemple de code XML** pour voir le document d’instance XML.