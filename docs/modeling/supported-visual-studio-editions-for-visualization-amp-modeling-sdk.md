---
title: Prise en charge des éditions de Visual Studio pour la visualisation &amp; Modeling SDK
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, supported Visual Studio editions
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 16a00dd5c0769cb49f5281570ba11433afa56dfe
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47858858"
---
# <a name="supported-visual-studio-editions-for-visualization-amp-modeling-sdk"></a>Prise en charge des éditions de Visual Studio pour la visualisation &amp; Modeling SDK
Les éléments suivants sont des listes d’éditions de Visual Studio qui sont prises en charge avec [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] dans les environnements de création et de déploiement. Pour plus d’informations sur ces éditions, consultez Microsoft Visual Studio [centre de développement](http://go.microsoft.com/fwlink/?LinkId=75628).

## <a name="authoring-edition"></a>Édition de création
 Pour définir un DSL, vous devez avoir installé les composants suivants :

|||
|-|-|
|Visual Studio|[http://go.microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkId=185579)|
|Kit de développement logiciel Visual Studio|[http://go.microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkId=185580)|
|Kit de développement logiciel (SDK) Visual Studio Visualization and Modeling|[http://go.microsoft.com/fwlink/?LinkID=186128](http://go.microsoft.com/fwlink/?LinkID=186128)|

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="deployment-editions"></a>Éditions de déploiement
 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] prend en charge les configurations suivantes pour déployer les langages spécifiques à un domaine que vous créez :

-   Visual Studio Enterprise

-   Visual Studio Professional

-   Package redistribuable Visual Studio Shell (mode intégré) redistributable package

-   Package redistribuable Visual Studio Shell (mode isolé) package redistribuable

> [!NOTE]
>  Pour rendre un DSL puisse s’exécuter sur un produit Shell, vous devez définir le **pris en charge les éditions de Visual Studio** champ dans le manifeste d’Extension. Pour plus d’informations, consultez [déploiement de Solutions de langage spécifique à un domaine](../modeling/deploying-domain-specific-language-solutions.md).

## <a name="see-also"></a>Voir aussi

- [Glossaire des outils Domain-Specific Language](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
