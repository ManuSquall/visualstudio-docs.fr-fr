---
title: 'CA2228 : Ne sont pas fournis à des formats de ressources non commercialisés | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- DoNotShipUnreleasedResourceFormats
- CA2228
helpviewer_keywords:
- CA2228
- DoNotShipUnreleasedResourceFormats
ms.assetid: 2c614edc-4e94-4b4f-8067-eea677a75cd9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b244dda388e5044b910259a4e92266671722e562
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="ca2228-do-not-ship-unreleased-resource-formats"></a>CA2228 : Ne distribuez pas des formats de ressources non commercialisés
|||  
|-|-|  
|TypeName|DoNotShipUnreleasedResourceFormats|  
|CheckId|CA2228|  
|Category|Microsoft.Usage|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Un fichier de ressources a été généré à l’aide d’une version de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] qui est actuellement pas en charge.  
  
## <a name="rule-description"></a>Description de la règle  
 Fichiers de ressources qui ont été générées à l’aide de versions préliminaires de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] ne peut pas être utilisables par les versions prises en charge du .NET Framework.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, générez la ressource à l’aide d’une version prise en charge de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]k.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.