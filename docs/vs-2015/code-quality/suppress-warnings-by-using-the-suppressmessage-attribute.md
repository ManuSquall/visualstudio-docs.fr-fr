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
ms.openlocfilehash: a5d64a27759cf844550297beb19b026bbeaa0e40
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546820"
---
# <a name="suppress-warnings-by-using-the-suppressmessage-attribute"></a>Supprimer des avertissements à l'aide de l'attribut SuppressMessage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il est souvent utile d’indiquer que l’avertissement n’est pas applicable pour permettre aux membres de l’équipe de savoir que le code a été révisé et qu’il a été déterminé que l’avertissement doit être supprimé. In source suppression (ISS) permet à un développeur de placer l’attribut qui supprime un avertissement près de l’emplacement qui a généré l’avertissement. Vous pouvez ajouter l’attribut ISS directement au fichier source ou vous pouvez utiliser le menu contextuel dans l' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE.

## <a name="in-this-section"></a>Dans cette section

|Titre|Description|
|-|-|
|[Vue d’ensemble de la suppression à la source](../code-quality/in-source-suppression-overview.md)|Découvrez ISS et comment l’utiliser dans votre code.|
|[Comment : supprimer des avertissements à l’aide de l’élément de menu](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)|Découvrez comment supprimer des avertissements dans l' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE à l’aide du menu contextuel.|

## <a name="related-sections"></a>Sections connexes
 [Analyse de la qualité d’un code managé](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)
