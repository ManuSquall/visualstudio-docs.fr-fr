---
title: Tri, filtrage et regroupement dans l’Explorateur de schémas XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4a914de0-9ffc-4526-9603-92e460e52513
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: daa629b4c26abf7b6ce801c30ea6f6fd41fbaa48
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926728"
---
# <a name="sorting-filtering-and-grouping-xml-schema-explorer"></a>Tri, filtrage et regroupement (Explorateur de schémas XML)

Cette rubrique décrit les options disponibles dans le menu **Trier, filtrer et options de regroupement** dans la barre d’outils de l' **Explorateur de schémas XML** .

## <a name="filter-options"></a>Options de filtre

Les options de filtrage suivantes sont disponibles. Par défaut, les options **afficher les espaces de noms** et afficher les fichiers de **schéma** sont sélectionnées.

- **Afficher les espaces de noms**.

- **Affichez les fichiers de schéma**.

- **Afficher les compositeurs (séquence/choix/tous)** .

## <a name="sorting-options"></a>Options de tri

Les options de tri suivantes sont disponibles. La valeur par défaut est **Trier par type**. Les options de **Tri par** ne s’appliquent pas aux fichiers et aux espaces de noms.

- **Trier par type**.

- **Trier par nom**.

- **Ordre du document**.

### <a name="sort-by-type"></a>Trier par type

Lorsque l’option **Trier par type** est sélectionnée, les nœuds globaux sont triés dans l’ordre suivant. Les nœuds sont ensuite triés par ordre alphabétique dans chaque groupe.

1. Nœuds `import`.

2. Nœuds `include`.

3. Nœuds `redefine`.

4. Nœuds `attribute`.

5. Nœuds `attributeGroup`.

6. Nœuds `complexType`.

7. Nœuds `simpleType`.

8. Nœuds `element`.

9. Nœuds `group`.

### <a name="sort-by-name"></a>Trier par nom

Lorsque l’option **Trier par nom** est sélectionnée, les nœuds globaux sont triés dans l’ordre suivant:

1. Nœuds `import` (par ordre alphabétique des espaces de noms).

2. Nœuds `include` (par ordre alphabétique des attributs `schemaLocation`).

3. Nœuds `redefine` (par ordre alphabétique des attributs `schemaLocation`).

4. Autres nœuds globaux par ordre alphabétique.

### <a name="document-order"></a>Ordre du document

L’option **ordre du document** est disponible lorsque l’option Afficher les fichiers de **schéma** est sélectionnée. Lorsque l’option **ordre du document** est sélectionnée, les nœuds globaux s’affichent dans l’ordre dans lequel ils apparaissent dans le fichier de schéma.

## <a name="persisting-sortfilter-options"></a>Persistance des options de tri/filtre

Les options de tri, de filtrage et de regroupement sont enregistrées dans le Registre pour chaque utilisateur, indépendamment de la solution ou des fichiers ouverts lors de la modification des paramètres.