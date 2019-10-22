---
title: Supprimer les avertissements à l’aide de l’attribut SuppressMessage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- VC.Project.VCFxCopTool.InputAssemblyFileName
- VC.Project.VCFxCopTool.FxCopModuleSuppressionsFile
- VC.Project.VCFxCopTool.FxCopUseTypeNameInSuppression
- VC.Project.VCFxCopTool.OutputFile
helpviewer_keywords:
- code analysis, source suppression
- source suppression
- SuppressMessage attribute
- code analysis, SuppressMessage attribute
ms.assetid: a38c57a2-d29d-43c0-84ff-3308b2484ce6
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8df4972cb1d54b88d6e716254574ea95bcaed4b7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672443"
---
# <a name="suppress-warnings-by-using-the-suppressmessage-attribute"></a>Supprimer des avertissements à l'aide de l'attribut SuppressMessage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il est souvent utile d’indiquer que l’avertissement n’est pas applicable pour permettre aux membres de l’équipe de savoir que le code a été révisé et qu’il a été déterminé que l’avertissement doit être supprimé. In source suppression (ISS) permet à un développeur de placer l’attribut qui supprime un avertissement près de l’emplacement qui a généré l’avertissement. Vous pouvez ajouter l’attribut ISS directement au fichier source ou vous pouvez utiliser le menu contextuel dans l’IDE [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

## <a name="in-this-section"></a>Dans cette section

|||
|-|-|
|[Vue d’ensemble de la suppression à la source](../code-quality/in-source-suppression-overview.md)|Découvrez ISS et comment l’utiliser dans votre code.|
|[Guide pratique pour supprimer des avertissements à l’aide de l’élément Menu](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)|Découvrez comment supprimer des avertissements dans l’IDE [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] à l’aide du menu contextuel.|

## <a name="related-sections"></a>Rubriques connexes
 [Analyse de la qualité d’un code managé](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)
