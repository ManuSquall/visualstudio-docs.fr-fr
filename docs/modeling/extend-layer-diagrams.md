---
title: Étendre des diagrammes de dépendance
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, creating extensions
- layer models
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 305c562c7600dc6955ce0307db92f4e257fc1c21
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302944"
---
# <a name="extend-dependency-diagrams"></a>Étendre des diagrammes de dépendance

Vous pouvez écrire du code pour créer et mettre à jour des diagrammes de dépendance et valider la structure de votre code de programme contre les diagrammes de dépendance dans Visual Studio. Vous pouvez ajouter des commandes qui s’affichent dans le menu contextuel des diagrammes, personnaliser les mouvements de glisser-déplacer et accéder au modèle de couche à partir de modèles de texte. Vous pouvez empaqueter ces extensions dans une extension d’intégration Visual Studio (VSIX) et les distribuer à d’autres utilisateurs de Visual Studio.

## <a name="requirements"></a>Spécifications

Vous devez avoir installé les éléments suivants sur l’ordinateur où vous voulez développer vos extensions de couche :

- Visual Studio

- [SDK Visual Studio](../extensibility/visual-studio-sdk.md)

- Modélisation SDK pour Visual Studio

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Vous devez avoir une édition appropriée de Visual Studio installé sur l’ordinateur où vous voulez exécuter vos extensions de couche. Pour voir quelles éditions de Visual Studio supportent les diagrammes de dépendance, voir [le support Edition pour l’architecture et les outils de modélisation.](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)

## <a name="see-also"></a>Voir aussi

- [Diagrammes de dépendance : référence](../modeling/layer-diagrams-reference.md)
- [Diagrammes de dépendance : recommandations](../modeling/layer-diagrams-guidelines.md)
- [Créer des diagrammes de dépendance à partir de votre code](../modeling/create-layer-diagrams-from-your-code.md)
- [Valider du code avec des diagrammes de dépendance](../modeling/validate-code-with-layer-diagrams.md)
