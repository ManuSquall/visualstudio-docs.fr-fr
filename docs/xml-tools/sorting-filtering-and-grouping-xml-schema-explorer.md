---
title: Tri, filtrage et regroupement dans l’Explorateur de schémas XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 4a914de0-9ffc-4526-9603-92e460e52513
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f4354e58e8de2d877e726b4615bac3832bfc37d2
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="sorting-filtering-and-grouping-xml-schema-explorer"></a>Tri, filtrage et regroupement (Explorateur de schémas XML)

Cette rubrique décrit les options qui sont disponibles via le **tri, filtrage et regroupement Options** menu dans la barre d’outils de l’Explorateur de schémas XML.

## <a name="filter-options"></a>Options du filtre

 Les options de filtrage suivantes sont disponibles. Par défaut, le **afficher les espaces de noms** et **afficher les fichiers de schéma** sont sélectionnées.

-   **Afficher les espaces de noms**.

-   **Afficher les fichiers de schéma**.

-   **Afficher les compositeurs (séquence/choix/tous)**.

## <a name="sorting-options"></a>Options de tri

 Les options de tri suivantes sont disponibles. La valeur par défaut est **trier par Type**. Les options Trier par ne s'appliquent pas aux fichiers et aux espaces de noms.

-   **Trier par Type**.

-   **Trier par nom**.

-   **Ordre du document**.

### <a name="sort-by-type"></a>Trier par type

 Lorsque le **trier par Type** option est sélectionnée, les nœuds globaux sont triés dans l’ordre suivant. Les nœuds sont ensuite triés par ordre alphabétique dans chaque groupe.

1.  Nœuds `import`.

2.  Nœuds `include`.

3.  Nœuds `redefine`.

4.  Nœuds `attribute`.

5.  Nœuds `attributeGroup`.

6.  Nœuds `complexType`.

7.  Nœuds `simpleType`.

8.  Nœuds `element`.

9. Nœuds `group`.

### <a name="sort-by-name"></a>Trier par nom

 Lorsque le **trier par nom** option est sélectionnée, les nœuds globaux sont triés dans l’ordre suivant :

1.  Nœuds `import` (par ordre alphabétique des espaces de noms).

2.  Nœuds `include` (par ordre alphabétique des attributs `schemaLocation`).

3.  Nœuds `redefine` (par ordre alphabétique des attributs `schemaLocation`).

4.  Autres nœuds globaux par ordre alphabétique.

### <a name="document-order"></a>Ordre du document

 Le **l’ordre du Document** option est disponible lorsque le **afficher les fichiers de schéma** option est sélectionnée. Lorsque **l’ordre du Document** est sélectionnée, les nœuds globaux sont affichés dans l’ordre dans lequel ils apparaissent dans le fichier de schéma.

## <a name="persisting-sortfilter-options"></a>Persistance des options de tri/filtrage

 Les options de tri, de filtrage et de regroupement sont enregistrées dans le Registre pour chaque utilisateur, indépendamment de la solution ou des fichiers ouverts lors de la modification des paramètres.