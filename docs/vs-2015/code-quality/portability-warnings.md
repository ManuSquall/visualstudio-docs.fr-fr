---
title: Les avertissements de portabilité | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.PortabilityRules
helpviewer_keywords:
- portability warnings
- managed code analysis warnings, portability warnings
- warnings, portability
ms.assetid: 902e859a-2153-4970-baaa-8a5b4a11806f
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 7c8f195f2219cfa2c81b24a3e04ddc559dc98a06
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142210"
---
# <a name="portability-warnings"></a>avertissements liés à la portabilité
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Avertissements de portabilité prennent en charge la portabilité sur différents systèmes d’exploitation.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Règle|Description|  
|----------|-----------------|  
|[CA1900 : Champs de type valeur doivent être portables](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Cette règle vérifie que les structures déclarées à l’aide d’un attribut de disposition explicite seront aligneront correctement lorsqu’elle est marshalée au code non managé sur les systèmes d’exploitation 64 bits.|  
|[CA1901 : Les déclarations P/Invoke doivent être portables](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|Cette règle évalue la taille de chaque paramètre et la valeur de retour d’un P/Invoke et vérifie que leur taille est correcte lorsqu’elle est marshalée au code non managé sur les systèmes d’exploitation 32 bits et 64 bits.|  
|[CA1903 : Utiliser uniquement l’API du framework cible](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|Un membre ou un type utilise un membre ou un type qui a été introduit dans un Service Pack qui ne figurait pas dans le Framework ciblé du projet.|
