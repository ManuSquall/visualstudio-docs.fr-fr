---
title: Étendre les diagrammes de couches Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, creating extensions
- layer models
ms.assetid: 83fca301-b008-485a-87eb-218050e71451
caps.latest.revision: 41
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bfcec64f9401fdbf79e67bee5fe8430452632fbc
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302335"
---
# <a name="extend-layer-diagrams"></a>Extend layer diagrams
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez écrire du code pour créer et mettre à jour des diagrammes de couche et pour valider la structure de votre code de programme par rapport aux diagrammes de couche dans Visual Studio. Vous pouvez ajouter des commandes qui s’affichent dans le menu contextuel des diagrammes, personnaliser les mouvements de glisser-déplacer et accéder au modèle de couche à partir de modèles de texte. Vous pouvez empaqueter ces extensions dans une extension d’intégration Visual Studio (VSIX) et les distribuer à d’autres utilisateurs de Visual Studio.

 Pour plus d’informations sur les diagrammes de couche, consultez :

- [Informations de référence sur les diagrammes de couche](../modeling/layer-diagrams-reference.md)

- [Diagrammes de couche : recommandations](../modeling/layer-diagrams-guidelines.md)

- [Créer des diagrammes de couche à partir de votre code](../modeling/create-layer-diagrams-from-your-code.md)

- [Valider du code avec des diagrammes de couche](../modeling/validate-code-with-layer-diagrams.md)

## <a name="requirements"></a><a name="prereqs"></a>Exigences
 Vous devez avoir installé les éléments suivants sur l’ordinateur où vous voulez développer vos extensions de couche :

- Visual Studio

- [SDK Visual Studio](../extensibility/visual-studio-sdk.md)

- [Modélisation SDK pour Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=48148)

  Une version appropriée de Visual Studio doit être installée sur l’ordinateur où vous voulez exécuter vos extensions de couche. Pour plus d’informations, voir [Déployez une extension de modèle de couche.](../modeling/deploy-a-layer-model-extension.md)

  Pour connaître les versions de Visual Studio qui prennent en charge les diagrammes de couche, consultez [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="in-this-section"></a>Dans cette section
 [Ajouter des commandes et des mouvements aux diagrammes de couche](../modeling/add-commands-and-gestures-to-layer-diagrams.md)

 [Ajouter une validation d'architecture personnalisée aux diagrammes de couche](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)

 [Ajouter des propriétés personnalisées à des diagrammes de couche](../modeling/add-custom-properties-to-layer-diagrams.md)

 [Parcourir et mettre à jour les modèles de couche dans le code du programme](../modeling/navigate-and-update-layer-models-in-program-code.md)

 [Déployer une extension de modèle de couche](../modeling/deploy-a-layer-model-extension.md)

 [Dépanner les extensions des diagrammes de couche](../modeling/troubleshoot-extensions-for-layer-diagrams.md)

## <a name="see-also"></a> Voir aussi
 [Définir et installer une extension de modélisation](../modeling/define-and-install-a-modeling-extension.md) [Diagrammes de couche: Diagrammes](../modeling/layer-diagrams-reference.md) de couche de [référence: Lignes directrices](../modeling/layer-diagrams-guidelines.md) Créer des [diagrammes de couche à partir de votre code de](../modeling/create-layer-diagrams-from-your-code.md) validation de code avec des [diagrammes de couche](../modeling/validate-code-with-layer-diagrams.md) Générer des fichiers à partir [d’un modèle UML](../modeling/generate-files-from-a-uml-model.md) [Ouvrir un modèle UML en utilisant l’API Studio visuel](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md)
