---
title: Quand implémenter un VSPackage de contrôle de code source
description: En savoir plus sur les choix de plug-ins de contrôle de code source et les VSPackages de contrôle de code source disponibles pour étendre les solutions de contrôle de code source Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, about source control packages
ms.assetid: 60b3326e-e7e2-4729-95fc-b682e7ad5c99
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 89e2ea0db7f162c70261ab2ba9aab187f9c11bd0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090887"
---
# <a name="determine-whether-to-implement-a-source-control-vspackage"></a>Déterminer si un VSPackage de contrôle de code source doit être implémenté

Cette section décrit les choix des plug-ins de contrôle de code source et des packages de contrôle de code source pour étendre les solutions de contrôle de code source et fournit des instructions générales sur le choix d’un chemin d’intégration approprié.

## <a name="small-source-control-solution-with-limited-resources"></a>Petite solution de contrôle de code source avec des ressources limitées

 Si vous avez des ressources limitées et que vous ne pouvez pas vous occuper de la surcharge liée à l’écriture d’un package de contrôle de code source, vous pouvez créer des plug-ins basés sur des API de plug-in de contrôle de code source. Vous pouvez ainsi travailler côte à côte avec les packages de contrôle de code source et basculer entre les plug-ins de contrôle de code source et les packages à la demande. Pour plus d’informations, consultez [inscription et sélection](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).

## <a name="large-source-control-solution-with-a-rich-feature-set"></a>Solution de contrôle de code source importante avec un ensemble de fonctionnalités enrichi

 Si vous souhaitez implémenter une solution de contrôle de code source qui fournit un modèle de contrôle de code source riche qui n’est pas capturé correctement à l’aide de l’API de plug-in de contrôle de code source, vous pouvez considérer un package de contrôle de code source comme le chemin d’intégration. Cela s’applique surtout si vous préférez remplacer le package de l’adaptateur de contrôle de code source (qui communique avec les plug-ins de contrôle de code source et fournit une interface utilisateur de contrôle de code source de base) avec les vôtres afin que vous puissiez gérer les événements de contrôle de code source de manière personnalisée. Si vous disposez déjà d’une interface utilisateur de contrôle de code source satisfaisante et que vous souhaitez conserver cette expérience dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , l’option de package de contrôle de code source vous permet de le faire. Le package de contrôle de code source n’est pas générique et est conçu uniquement pour être utilisé avec l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.

 Si vous souhaitez implémenter une solution de contrôle de code source qui offre une flexibilité et un contrôle plus riche de la logique et de l’interface utilisateur du contrôle de code source, vous préférerez peut-être l’itinéraire d’intégration du package de contrôle de code source. Vous pouvez :

1. Inscrivez votre propre VSPackage de contrôle de code source (voir [inscription et sélection](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)).

2. Remplacez l’interface utilisateur du contrôle de code source par défaut par votre interface utilisateur personnalisée (voir [interface utilisateur personnalisée](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)).

3. Spécifiez les glyphes à utiliser et gérez les événements de glyphes Explorateur de solutions (consultez [contrôle de glyphe](../../extensibility/internals/glyph-control-source-control-vspackage.md)).

4. Gérez les événements de modification de requête et d’enregistrement des requêtes (voir [requête modifier la requête enregistrer](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)).

## <a name="see-also"></a>Voir aussi

- [Créer un plug-in de contrôle de code source](../../extensibility/internals/creating-a-source-control-plug-in.md)
