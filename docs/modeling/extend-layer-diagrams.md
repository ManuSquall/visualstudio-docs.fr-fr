---
title: Étendre des diagrammes de dépendance
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, creating extensions
- layer models
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5519328ef69f98737a7744f0162bdc0951433a60
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62994713"
---
# <a name="extend-dependency-diagrams"></a>Étendre des diagrammes de dépendance

Vous pouvez écrire du code pour créer et mettre à jour des diagrammes de dépendance et pour valider la structure de votre code de programme par rapport aux diagrammes de dépendance dans Visual Studio. Vous pouvez ajouter des commandes qui s’affichent dans le menu contextuel des diagrammes, personnaliser les mouvements de glisser-déplacer et accéder au modèle de couche à partir de modèles de texte. Vous pouvez empaqueter ces extensions dans une extension d’intégration Visual Studio (VSIX) et les distribuer à d’autres utilisateurs de Visual Studio.

 Pour plus d’informations sur les diagrammes de dépendance, consultez :

- [Diagrammes de dépendance : Informations de référence](../modeling/layer-diagrams-reference.md)

- [Diagrammes de dépendance : Recommandations](../modeling/layer-diagrams-guidelines.md)

- [Créer des diagrammes de dépendance à partir de votre code](../modeling/create-layer-diagrams-from-your-code.md)

- [Validation du code avec des diagrammes de dépendance](../modeling/validate-code-with-layer-diagrams.md)

## <a name="prereqs"></a> Spécifications

Vous devez avoir installé les éléments suivants sur l’ordinateur où vous voulez développer vos extensions de couche :

- Visual Studio

- [Kit de développement logiciel Visual Studio](../extensibility/visual-studio-sdk.md)

- SDK Modeling pour Visual Studio

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Une version appropriée de Visual Studio doit être installée sur l’ordinateur où vous voulez exécuter vos extensions de couche.

Pour connaître les versions de Visual Studio prennent en charge les diagrammes de dépendance, consultez [versions prises en charge pour l’architecture et les outils de modélisation](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="in-this-section"></a>Dans cette section
 [Ajout de commandes et de mouvements aux diagrammes de dépendance](../modeling/add-commands-and-gestures-to-layer-diagrams.md)

 [Ajout d’une validation d’architecture personnalisée aux diagrammes de dépendance](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)

 [Ajout de propriétés personnalisées à des diagrammes de dépendance](../modeling/add-custom-properties-to-layer-diagrams.md)

## <a name="see-also"></a>Voir aussi

- [Diagrammes de dépendance : Informations de référence](../modeling/layer-diagrams-reference.md)
- [Diagrammes de dépendance : Recommandations](../modeling/layer-diagrams-guidelines.md)
- [Créer des diagrammes de dépendance à partir de votre code](../modeling/create-layer-diagrams-from-your-code.md)
- [Validation du code avec des diagrammes de dépendance](../modeling/validate-code-with-layer-diagrams.md)
