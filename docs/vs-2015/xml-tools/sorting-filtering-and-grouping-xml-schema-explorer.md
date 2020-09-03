---
title: Tri, filtrage et regroupement (Explorateur de schémas XML) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 4a914de0-9ffc-4526-9603-92e460e52513
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 99c28842a92ab598ff196e80fc96678c256e4db8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656150"
---
# <a name="sorting-filtering-and-grouping-xml-schema-explorer"></a>Tri, filtrage et regroupement (Explorateur de schémas XML)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette rubrique décrit les options disponibles dans le menu **Trier, filtrer et options de regroupement** dans la barre d’outils de l’Explorateur de schémas XML.

## <a name="filter-options"></a>Options du filtre
 Les options de filtrage suivantes sont disponibles. Par défaut, les options **afficher les espaces de noms** et afficher les fichiers de **schéma** sont sélectionnées.

- **Afficher les espaces de noms**.

- **Affichez les fichiers de schéma**.

- **Afficher les compositeurs (séquence/choix/tous)**.

## <a name="sorting-options"></a>Options de tri
 Les options de tri suivantes sont disponibles. La valeur par défaut est **Trier par type**. Les options Trier par ne s'appliquent pas aux fichiers et aux espaces de noms.

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
 Lorsque l’option **Trier par nom** est sélectionnée, les nœuds globaux sont triés dans l’ordre suivant :

1. `import` nœuds (dans l’ordre alphabétique des espaces de noms).

2. Nœuds `include` (par ordre alphabétique des attributs `schemaLocation`).

3. Nœuds `redefine` (par ordre alphabétique des attributs `schemaLocation`).

4. Autres nœuds globaux par ordre alphabétique.

### <a name="document-order"></a>Ordre du document
 L’option **ordre du document** est disponible lorsque l’option Afficher les fichiers de **schéma** est sélectionnée. Lorsque l’option **ordre du document** est sélectionnée, les nœuds globaux s’affichent dans l’ordre dans lequel ils apparaissent dans le fichier de schéma.

## <a name="persisting-sortfilter-options"></a>Persistance des options de tri/filtrage
 Les options de tri, de filtrage et de regroupement sont enregistrées dans le Registre pour chaque utilisateur, indépendamment de la solution ou des fichiers ouverts lors de la modification des paramètres.
