---
title: Prise en charge des éditions de Visual Studio pour Visualization and Modeling SDK
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
ms.openlocfilehash: 127b45ae6a0ab28d7f83ee41449d7846858ee4a9
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591903"
---
# <a name="supported-visual-studio-editions-for-visualization--modeling-sdk"></a>Éditions de Visual Studio prises en charge pour le SDK de visualisation et de modélisation

Les éléments suivants sont des listes d’éditions de Visual Studio qui sont prises en charge avec [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] dans les environnements de création et de déploiement. Pour plus d’informations sur ces éditions, consultez Microsoft Visual Studio [centre de développement](https://visualstudio.microsoft.com/).

## <a name="authoring-edition"></a>Édition de création

Pour définir un DSL, vous devez avoir installé les composants suivants :

|||
|-|-|
|Visual Studio|[http://go.microsoft.com/fwlink/?LinkId=185579](https://visualstudio.microsoft.com/)|
|Kit de développement Visual Studio SDK|[http://go.microsoft.com/fwlink/?LinkId=185580](/azure/devops/integrate/index?view=azure-devops&viewFallbackFrom=vsts)|
|Kit de développement logiciel (SDK) Visual Studio Visualization and Modeling|[http://go.microsoft.com/fwlink/?LinkID=186128](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)|

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="deployment-editions"></a>Éditions de déploiement

[!INCLUDE[dsl](../modeling/includes/dsl_md.md)] prend en charge les configurations suivantes pour déployer les langages spécifiques à un domaine que vous créez :

- Visual Studio Enterprise

- Visual Studio Professional

- Package redistribuable Visual Studio Shell (mode intégré) redistributable package

- Package redistribuable Visual Studio Shell (mode isolé) package redistribuable

> [!NOTE]
> Pour rendre un DSL puisse s’exécuter sur un produit Shell, vous devez définir le **pris en charge les éditions de Visual Studio** champ dans le manifeste d’Extension. Pour plus d’informations, consultez [Déploiement de solutions de langage spécifique à un domaine](msi-and-vsix-deployment-of-a-dsl.md).

## <a name="see-also"></a>Voir aussi

- [Glossaire des Outils Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
