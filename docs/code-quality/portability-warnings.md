---
title: avertissements liés à la portabilité
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.PortabilityRules
helpviewer_keywords:
- portability warnings
- managed code analysis warnings, portability warnings
- warnings, portability
ms.assetid: 902e859a-2153-4970-baaa-8a5b4a11806f
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e3e1959066f81663d66e8af2af8039080d8cace6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649128"
---
# <a name="portability-warnings"></a>avertissements liés à la portabilité
Les avertissements de portabilité prennent en charge la portabilité sur différents systèmes d’exploitation.

## <a name="in-this-section"></a>Dans cette section

|Règle|Description|
|----------|-----------------|
|[CA1900 : Les champs de type valeur doivent être portables](../code-quality/ca1900.md)|Cette règle vérifie que les structures déclarées à l’aide d’un attribut de disposition explicite s’aligneront correctement lorsqu’elles sont marshalées vers du code non managé sur les systèmes d’exploitation 64 bits.|
|[CA1901 : Les déclarations P/Invoke doivent être portables](../code-quality/ca1901.md)|Cette règle évalue la taille de chaque paramètre et la valeur de retour d’un P/Invoke, puis vérifie que leur taille est correcte lorsqu’elle est marshalée en code non managé sur les systèmes d’exploitation 32 bits et 64 bits.|
|[CA1903 : Utiliser l’API seulement à partir de l’infrastructure cible](../code-quality/ca1903.md)|Un membre ou un type utilise un membre ou un type qui a été introduit dans un Service Pack qui ne figurait pas dans le Framework ciblé du projet.|
