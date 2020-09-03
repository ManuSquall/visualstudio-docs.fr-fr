---
title: Explorateur de schémas XML-Rechercher dans le jeu de schémas
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ec1395e0-d03c-4130-810d-f2db656937bd
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8378ebaccefaedfcc3d83f23bcab56f7417264dd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75592501"
---
# <a name="search-the-schema-set"></a>Effectuer des recherches dans le jeu de schémas

L' **Explorateur de schémas XML** vous permet d’effectuer des recherches dans le jeu de schémas de l’une des manières suivantes :

- Recherche par mot clé

- Recherche spécifique au schéma

## <a name="keyword-search"></a>recherches par mot clé ;

Pour effectuer des recherches par mot clé, entrez une sous-chaîne dans la zone de texte **Rechercher dans schémas** de la barre d’outils de l' **Explorateur de schémas XML** .

![Recherche par mot clé de l'Explorateur de schémas XML](../xml-tools/media/schemaexplorersearch.gif)

L' **Explorateur de schémas XML** recherche les attributs suivants dans le jeu de schémas :

- Tout attribut `name` ou `ref` qui correspond au mot clé spécifié. Vous pouvez rechercher des éléments, des attributs, des types, etc., par nom.

- Attributs `schemaLocation` d'instructions d'inclusion.

- Attributs `namespace` d'instructions d'importation.

## <a name="schema-specific-search"></a>Recherche spécifique au schéma

L' **Explorateur de schémas XML** comprend également des recherches intégrées auxquelles vous pouvez accéder à l’aide du menu contextuel (clic droit) de l' **Explorateur de schémas XML**. Pour plus d’informations sur les menus contextuels disponibles, consultez [menus contextuels](../xml-tools/context-menus-xml-schema-explorer.md). Vous pouvez également effectuer une recherche spécifique au schéma à partir de la vue de départ. Pour plus d’informations, consultez la section « Détails du jeu de schémas » dans la rubrique [vue de départ](../xml-tools/start-view.md) .

## <a name="display-and-navigate-search-results"></a>Afficher et parcourir les résultats de la recherche

Une fois la recherche terminée, le volet de synthèse des résultats est ajouté à la barre d'outils avec les résultats de la recherche. Les résultats de la recherche sont également mis en surbrillance dans l' **Explorateur de schémas XML** et marqués par des graduations sur la barre de défilement verticale. Vous pouvez parcourir les résultats de la recherche en utilisant les boutons **aller au résultat de la recherche suivant** et **aller au résultat de la recherche précédent** dans le volet des résultats Résumé de la barre d’outils de l' **Explorateur de schémas XML** . en utilisant les touches du clavier **F3** et **MAJ** + **F3**; ou en cliquant sur les graduations dans la barre de défilement.

Vous pouvez ajouter les résultats de la recherche à l’espace de travail en cliquant sur le bouton **Ajouter les nœuds en surbrillance à l’espace de travail** dans le volet des résultats de résumé.

![Résultat de la recherche dans l'Explorateur de schémas XML](../xml-tools/media/schemaexplorersearchresult.gif)

## <a name="clear-search-results"></a>Effacer les résultats de la recherche

Pour effacer les résultats de la recherche, cliquez sur le bouton **x** dans le volet de synthèse des résultats de la barre d’outils recherche de l' **Explorateur de schémas XML** .

## <a name="see-also"></a>Voir aussi

- [Explorateur de schémas XML](../xml-tools/xml-schema-explorer.md)
