---
title: Les avertissements de portabilité | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
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
ms.openlocfilehash: 3b7c38f8380fc8e52707b9c4817880b1ce86b4b9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49173076"
---
# <a name="portability-warnings"></a>avertissements liés à la portabilité
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Avertissements de portabilité prennent en charge la portabilité sur différents systèmes d’exploitation.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Règle|Description|  
|----------|-----------------|  
|[CA1900 : Les champs de type valeur doivent être portables](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Cette règle vérifie que les structures déclarées à l’aide d’un attribut de disposition explicite seront aligneront correctement lorsqu’elle est marshalée au code non managé sur les systèmes d’exploitation 64 bits.|  
|[CA1901 : Les déclarations P/Invoke doivent être portables](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|Cette règle évalue la taille de chaque paramètre et la valeur de retour d’un P/Invoke et vérifie que leur taille est correcte lorsqu’elle est marshalée au code non managé sur les systèmes d’exploitation 32 bits et 64 bits.|  
|[CA1903 : Utiliser l’API seulement à partir de l’infrastructure cible](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|Un membre ou un type utilise un membre ou un type qui a été introduit dans un Service Pack qui ne figurait pas dans le Framework ciblé du projet.|



