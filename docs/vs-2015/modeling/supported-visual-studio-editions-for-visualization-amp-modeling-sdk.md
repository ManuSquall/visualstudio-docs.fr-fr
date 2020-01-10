---
title: Éditions de Visual Studio prises en charge pour la visualisation et la modélisation SDK | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, supported Visual Studio editions
ms.assetid: 7c313ba0-031d-45b8-8220-eead61754747
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0692efefcc92e3316ccf725c586fc6566b09a6ef
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850777"
---
# <a name="supported-visual-studio-editions-for-visualization-amp-modeling-sdk"></a>Éditions de Visual Studio prises en charge pour la visualisation &amp; SDK de modélisation
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les éléments suivants sont des listes d’éditions de Visual Studio qui sont prises en charge avec [!INCLUDE[dsl](../includes/dsl-md.md)] dans les environnements de création et de déploiement. Pour plus d’informations sur ces éditions, consultez le [Centre de développement](https://msdn.microsoft.com/vstudio/products/)Microsoft [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

## <a name="authoring-edition"></a>Édition de création
 Pour définir un DSL, vous devez avoir installé les composants suivants :

|||
|-|-|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185579](https://www.visualstudio.com/)|
|Kit de développement Visual Studio SDK|[http://go.microsoft.com/fwlink/?LinkId=185580](https://docs.microsoft.com/azure/devops/integrate/index?view=azure-devops&viewFallbackFrom=vsts)|
|Kit de développement logiciel (SDK) Visual Studio Visualization and Modeling|[http://go.microsoft.com/fwlink/?LinkID=186128](https://docs.microsoft.com/samples/browse/?redirectedfrom=MSDN-samples)|

## <a name="deployment-editions"></a>Éditions de déploiement
 [!INCLUDE[dsl](../includes/dsl-md.md)] prend en charge les configurations suivantes pour déployer les langages spécifiques à un domaine que vous créez :

- Visual Studio Enterprise

- Visual Studio Professional

- Package redistribuable Visual Studio Shell (mode intégré) redistributable package

- Package redistribuable Visual Studio Shell (mode isolé) package redistribuable

> [!NOTE]
> Pour rendre un DSL puisse s’exécuter sur un produit Shell, vous devez définir le **pris en charge les éditions de Visual Studio** champ dans le manifeste d’Extension. Pour plus d’informations, consultez [Déploiement de solutions de langage spécifique à un domaine](../modeling/deploying-domain-specific-language-solutions.md).

## <a name="see-also"></a>Voir aussi
 [Glossaire des Outils Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
