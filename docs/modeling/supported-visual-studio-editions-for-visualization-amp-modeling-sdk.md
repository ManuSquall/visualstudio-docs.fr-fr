---
title: Éditions de Visual Studio prises en charge pour la visualisation et la modélisation SDK
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, supported Visual Studio editions
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1fdfe698096da53abf28aa583c816d9238810333
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72609347"
---
# <a name="supported-visual-studio-editions-for-visualization--modeling-sdk"></a>Éditions de Visual Studio prises en charge pour le SDK de visualisation et de modélisation

Les listes suivantes répertorient les éditions de Visual Studio prises en charge avec [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] dans les environnements de création et de déploiement. Pour plus d’informations sur ces éditions, consultez le [Centre de développement](http://go.microsoft.com/fwlink/?LinkId=75628)Microsoft Visual Studio.

## <a name="authoring-edition"></a>Édition de création

Pour définir un DSL, vous devez avoir installé les composants suivants :

|||
|-|-|
|Visual Studio|[http://go.microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkId=185579)|
|SDK Visual Studio|[http://go.microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkId=185580)|
|Kit de développement logiciel (SDK) Visual Studio Visualization and Modeling|[http://go.microsoft.com/fwlink/?LinkID=186128](http://go.microsoft.com/fwlink/?LinkID=186128)|

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="deployment-editions"></a>Éditions de déploiement

[!INCLUDE[dsl](../modeling/includes/dsl_md.md)] prend en charge les configurations suivantes pour déployer les langages spécifiques à un domaine que vous créez :

- Visual Studio Enterprise

- Visual Studio Professional

- Package redistribuable du package redistribuable du shell Visual Studio (mode intégré)

- Package redistribuable Visual Studio Shell (mode isolé) package redistribuable

> [!NOTE]
> Pour qu’un DSL puisse s’exécuter sur un produit de l’interpréteur de commandes, vous devez définir le champ de l' **édition vs pris en charge** dans le manifeste de l’extension. Pour plus d’informations, consultez [Déploiement de solutions de langage spécifique à un domaine](msi-and-vsix-deployment-of-a-dsl.md).

## <a name="see-also"></a>Voir aussi

- [Glossaire des Outils Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)