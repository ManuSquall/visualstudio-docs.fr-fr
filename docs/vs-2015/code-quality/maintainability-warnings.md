---
title: Avertissements de maintenabilité | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.maintainabilityrules
helpviewer_keywords:
- warnings, maintainability
- managed code analysis warnings, maintainability warnings
- maintainability warnings
ms.assetid: 537e70ca-a88c-49df-bfc7-0ee63bbe4f16
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e448a72e2ff92b3e3028829d4b1e7658c304ee3c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667898"
---
# <a name="maintainability-warnings"></a>avertissements liés à la facilité de maintenance
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les avertissements de maintenabilité prennent en charge la gestion des bibliothèques et des applications.

## <a name="in-this-section"></a>Dans cette section

|Règle|Description|
|----------|-----------------|
|[CA1500 : Les noms de variables ne doivent pas être identiques aux noms de champs](../code-quality/ca1500-variable-names-should-not-match-field-names.md)|Une méthode d’instance déclare un paramètre ou une variable locale dont le nom correspond à un champ d’instance du type déclarant, ce qui génère des erreurs.|
|[CA1501 : Éviter l'excès d'héritage](../code-quality/ca1501-avoid-excessive-inheritance.md)|Un type est imbriqué de plus de quatre niveaux dans sa hiérarchie d'héritage. Les hiérarchies de type profondément imbriquées peuvent être difficiles à suivre, comprendre et gérer.|
|[CA1502 : Éviter l'excès de complexité](../code-quality/ca1502-avoid-excessive-complexity.md)|Cette règle évalue le nombre de chemins linéairement indépendants dans la méthode, déterminé par le nombre et la complexité des branches conditionnelles.|
|[CA1504 : Vérifier les noms de champs trompeurs](../code-quality/ca1504-review-misleading-field-names.md)|Le nom d’un champ d’instance commence par « s_ », ou le nom d’un champ statique (partagé dans [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ) commence par « m_ ».|
|[CA1505 : Éviter le code impossible à maintenir](../code-quality/ca1505-avoid-unmaintainable-code.md)|Un type ou une méthode a une faible valeur d'indice de maintenabilité. Un faible indice de maintenabilité indique qu'un type ou qu'une méthode est probablement difficile à maintenir et qu'il/elle se prête bien à une nouvelle conception.|
|[CA1506 : Éviter les couplages de classe excessifs](../code-quality/ca1506-avoid-excessive-class-coupling.md)|Cette règle mesure l'accouplement de classes en comptant le nombre de références de type uniques contenues dans un type ou une méthode.|

## <a name="see-also"></a>Voir aussi
 [Mesures de la complexité et de la facilité de maintenance du code managé](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
