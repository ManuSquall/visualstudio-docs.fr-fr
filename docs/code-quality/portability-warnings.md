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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 072858a9faafe312fd7c8314e7f25cf581c40844
ms.sourcegitcommit: e95dd8cedcd180e0bce6a75c86cf861757918290
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72163073"
---
# <a name="portability-warnings"></a>avertissements liés à la portabilité
Les avertissements de portabilité prennent en charge la portabilité sur différents systèmes d’exploitation.

## <a name="in-this-section"></a>Dans cette section

|Règle|Description|
|----------|-----------------|
|@NO__T 0CA1900 : Les champs de type valeur doivent être portables @ no__t-0|Cette règle vérifie que les structures déclarées à l’aide d’un attribut de disposition explicite s’aligneront correctement lorsqu’elles sont marshalées vers du code non managé sur les systèmes d’exploitation 64 bits.|
|@NO__T 0CA1901 : Les déclarations P/Invoke doivent être portables @ no__t-0|Cette règle évalue la taille de chaque paramètre et la valeur de retour d’un P/Invoke, puis vérifie que leur taille est correcte lorsqu’elle est marshalée en code non managé sur les systèmes d’exploitation 32 bits et 64 bits.|
|@NO__T 0CA1903 : Utiliser uniquement l’API du Framework ciblé @ no__t-0|Un membre ou un type utilise un membre ou un type qui a été introduit dans un Service Pack qui ne figurait pas dans le Framework ciblé du projet.|
