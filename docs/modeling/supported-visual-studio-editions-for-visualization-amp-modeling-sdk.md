---
title: Éditions de Visual Studio prises en charge pour la visualisation et la modélisation SDK
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, supported Visual Studio editions
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 908a224feb9f6ad463ae14812b3a8550bf932e35
ms.sourcegitcommit: c31815e140f2ec79e00a9a9a19900778ec11e860
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2020
ms.locfileid: "92298553"
---
# <a name="supported-visual-studio-editions-for-visualization--modeling-sdk"></a>Éditions de Visual Studio prises en charge pour le SDK de visualisation et de modélisation

Les listes suivantes répertorient les éditions de Visual Studio prises en charge par [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] dans les environnements de création et de déploiement. Pour plus d’informations sur ces éditions, consultez le [Centre de développement](https://visualstudio.microsoft.com/)Microsoft Visual Studio.

## <a name="authoring-edition"></a>Édition de création

Pour définir un DSL, vous devez avoir installé les composants suivants :

|Produit|Télécharger le lien|
|-|-|
|Visual Studio|[http://go.microsoft.com/fwlink/?LinkId=185579](https://visualstudio.microsoft.com/)|
|Kit de développement logiciel Visual Studio|[http://go.microsoft.com/fwlink/?LinkId=185580](/azure/devops/integrate/index?view=azure-devops&viewFallbackFrom=vsts&preserve-view=true)|
|Kit de développement logiciel (SDK) Visual Studio Visualization and Modeling|[http://go.microsoft.com/fwlink/?LinkID=186128](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)|

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="deployment-editions"></a>Éditions de déploiement

[!INCLUDE[dsl](../modeling/includes/dsl_md.md)] prend en charge les configurations suivantes pour déployer les langages spécifiques à un domaine que vous générez :

- Visual Studio Enterprise

- Visual Studio Professional

- Package redistribuable Visual Studio Shell (mode intégré) package redistribuable

- Package redistribuable Visual Studio Shell (mode isolé) package redistribuable

> [!NOTE]
> Pour qu’un DSL puisse s’exécuter sur un produit de l’interpréteur de commandes, vous devez définir le champ de l' **édition vs pris en charge** dans le manifeste de l’extension. Pour plus d’informations, consultez [Déploiement de solutions de langage spécifique à un domaine](msi-and-vsix-deployment-of-a-dsl.md).

## <a name="see-also"></a>Voir aussi

- [Glossaire des Outils Domain-Specific Language](/previous-versions/bb126564(v=vs.100))