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
ms.openlocfilehash: 3eebefeab6b78955b03d4546a60dd811f5e9ae4e
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547652"
---
# <a name="supported-visual-studio-editions-for-visualization-amp-modeling-sdk"></a>Éditions de Visual Studio prises en charge pour le &amp; Kit de développement logiciel de modélisation de visualisation
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les listes suivantes répertorient les éditions de Visual Studio prises en charge par [!INCLUDE[dsl](../includes/dsl-md.md)] dans les environnements de création et de déploiement. Pour plus d’informations sur ces éditions, consultez le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [Centre de développement](https://msdn.microsoft.com/vstudio/products/)Microsoft.

## <a name="authoring-edition"></a>Édition de création
 Pour définir un DSL, vous devez avoir installé les composants suivants :

|Produit|Télécharger le lien|
|-|-|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[https://www.visualstudio.com/](https://www.visualstudio.com/)|
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[SDK Visual Studio](../extensibility/visual-studio-sdk.md)|
|Kit de développement logiciel (SDK) Visual Studio Visualization and Modeling|[Téléchargement du SDK Modeling](https://www.microsoft.com/download/details.aspx?id=48148)|
## <a name="deployment-editions"></a>Éditions de déploiement
 [!INCLUDE[dsl](../includes/dsl-md.md)]prend en charge les configurations suivantes pour déployer les langages spécifiques à un domaine que vous générez :

- Visual Studio Enterprise

- Visual Studio Professional

- Package redistribuable Visual Studio Shell (mode intégré) package redistribuable

- Package redistribuable Visual Studio Shell (mode isolé) package redistribuable

> [!NOTE]
> Pour qu’un DSL puisse s’exécuter sur un produit de l’interpréteur de commandes, vous devez définir le champ de l' **édition vs pris en charge** dans le manifeste de l’extension. Pour plus d’informations, consultez [Déploiement de solutions de langage spécifique à un domaine](../modeling/deploying-domain-specific-language-solutions.md).

## <a name="see-also"></a>Voir aussi
 [Glossaire des Outils Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
