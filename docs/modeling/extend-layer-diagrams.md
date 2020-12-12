---
title: Étendre des diagrammes de dépendance
description: Découvrez comment vous pouvez écrire du code pour créer et mettre à jour des diagrammes de dépendance, et comment valider la structure de votre code de programme par rapport aux diagrammes de dépendance dans Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: d78b7005875f0544354c845cd27d187bdbf40d6d
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/12/2020
ms.locfileid: "97361623"
---
# <a name="extend-dependency-diagrams"></a>Étendre des diagrammes de dépendance

Vous pouvez écrire du code pour créer et mettre à jour des diagrammes de dépendance et pour valider la structure de votre code de programme par rapport aux diagrammes de dépendance dans Visual Studio. Vous pouvez ajouter des commandes qui s’affichent dans le menu contextuel des diagrammes, personnaliser les mouvements de glisser-déplacer et accéder au modèle de couche à partir de modèles de texte. Vous pouvez empaqueter ces extensions dans une extension d’intégration Visual Studio (VSIX) et les distribuer à d’autres utilisateurs de Visual Studio.

## <a name="requirements"></a>Spécifications

Vous devez avoir installé les éléments suivants sur l’ordinateur où vous voulez développer vos extensions de couche :

- Visual Studio

- [SDK Visual Studio](../extensibility/visual-studio-sdk.md)

- SDK Modeling pour Visual Studio

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Vous devez disposer d’une édition appropriée de Visual Studio installée sur l’ordinateur sur lequel vous souhaitez exécuter vos extensions de couche. Pour connaître les éditions de Visual Studio qui prennent en charge les diagrammes de dépendance, consultez [prise en charge d’édition pour les outils d’architecture et de modélisation](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="see-also"></a>Voir aussi

- [Diagrammes de dépendance : référence](../modeling/layer-diagrams-reference.md)
- [Diagrammes de dépendance : recommandations](../modeling/layer-diagrams-guidelines.md)
- [Créer des diagrammes de dépendance à partir de votre code](../modeling/create-layer-diagrams-from-your-code.md)
- [Valider du code avec des diagrammes de dépendance](../modeling/validate-code-with-layer-diagrams.md)
