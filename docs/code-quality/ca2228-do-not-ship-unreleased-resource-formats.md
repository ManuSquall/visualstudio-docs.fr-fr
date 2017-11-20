---
title: "CA2228 : Ne sont pas fournis à des formats de ressources non commercialisés | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotShipUnreleasedResourceFormats
- CA2228
helpviewer_keywords:
- CA2228
- DoNotShipUnreleasedResourceFormats
ms.assetid: 2c614edc-4e94-4b4f-8067-eea677a75cd9
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 959d88751ff250e54f6a3f89f0b4b0554add96d1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ca2228-do-not-ship-unreleased-resource-formats"></a>CA2228 : Ne distribuez pas des formats de ressources non commercialisés
|||  
|-|-|  
|TypeName|DoNotShipUnreleasedResourceFormats|  
|CheckId|CA2228|  
|Catégorie|Microsoft.Usage|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Un fichier de ressources a été généré à l’aide d’une version de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] qui est actuellement pas en charge.  
  
## <a name="rule-description"></a>Description de la règle  
 Fichiers de ressources qui ont été générées à l’aide de versions préliminaires de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] ne peut pas être utilisables par les versions prises en charge du .NET Framework.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, générez la ressource à l’aide d’une version prise en charge de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]k.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.