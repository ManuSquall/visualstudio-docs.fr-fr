---
title: Analyse du code pour les avertissements liés au code managé
ms.date: 08/31/2020
ms.topic: reference
f1_keywords:
- vc.project.vcfxcoptool.enablefxcop
helpviewer_keywords:
- managed code analyis, warnings
- warnings, managed code analysis
- managed code analysis warnings
- code analysis,managed code
ms.assetid: 3c2741ff-0d3a-42e6-acd5-d42310bd03c4
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 566b9827f42f646cd9350cfc015a460485212a09
ms.sourcegitcommit: a18c7e9b367c2f92f6e54c3eaef442775d457667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90094328"
---
# <a name="net-code-analysis-rules"></a>Règles d’analyse du code .NET
L’analyse du code .NET fournit des règles qui indiquent des violations de la qualité du code ou des suggestions pour améliorer la qualité du code. Les règles sont organisées dans des zones de règles telles que la conception, la localisation, les performances et la sécurité. Certaines règles sont spécifiques à l’utilisation de l’API .NET, tandis que les règles restantes concernent la qualité du code générique. Cette section fournit des discussions et des exemples détaillés pour chaque règle.

 Le tableau suivant indique le type d’informations fourni pour chaque diagnostic.

|Élément|Description|
|----------|-----------------|
|Type|TypeName de la règle.|
|ID de la règle|Identificateur unique de la règle. RuleId et Category sont utilisés pour la suppression à la source d’un avertissement.|
|Category|Catégorie de l’avertissement.|
|Modification avec rupture|Indique si la correction d’une violation de la règle constitue une modification avec rupture. Une modification avec rupture signifie qu’un assembly qui présente une dépendance à la cible ayant provoqué la violation ne se recompile pas avec la nouvelle version corrigée ou peut échouer au moment de l’exécution en raison de la modification. Lorsque plusieurs correctifs sont disponibles et qu’au moins un correctif est une modification avec rupture et qu’un correctif n’est pas, les deux options « interruption » et « sans rupture » sont spécifiées.|
|Cause|Code managé spécifique qui contraint la règle à générer un avertissement.|
|Description|Décrit les problèmes sous-jacents à l’avertissement.|
|Comment corriger les violations|Explique comment modifier le code source pour satisfaire la règle et l’empêcher de générer un avertissement.|
|Quand supprimer les avertissements|Décrit les circonstances dans lesquelles il est possible de supprimer un avertissement de la règle en toute sécurité.|
|Exemple de code|Exemples qui violent la règle et exemples corrigés qui satisfont la règle.|
|Avertissements connexes|Avertissements connexes.|

## <a name="in-this-section"></a>Dans cette section

|Category|Description|
|-|-|
|[Règles par ID](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)|Répertorie toutes les règles par RuleID|
|[Règles de conception](../code-quality/design-warnings.md)|Règles qui prennent en charge la conception de bibliothèque correcte, comme spécifié par les instructions de conception .NET.|
|[Règles de documentation](../code-quality/documentation-warnings.md)|Règles qui prennent en charge la conception de bibliothèque bien documentée via l’utilisation correcte des commentaires de documentation XML.|
|[Règles de globalisation](../code-quality/globalization-warnings.md)|Règles qui prennent en charge des bibliothèques et des applications mondialisables.|
|[Règles de maintenance](../code-quality/maintainability-warnings.md)|Règles qui prennent en charge la maintenance des bibliothèques et des applications.|
|[Règles d’affectation de noms](../code-quality/naming-warnings.md)|Règles qui prennent en charge l’adhésion aux conventions d’affectation des noms des règles de conception .NET.|
|[Règles de performance](../code-quality/performance-warnings.md)|Règles qui prennent en charge les bibliothèques et les applications à hautes performances.|
|[Règles de portabilité et d’interopérabilité](../code-quality/interoperability-warnings.md)|Règles qui prennent en charge la portabilité sur différentes plateformes et interaction avec les clients COM.|
|[Publier les règles](../code-quality/publish-warnings.md)|Règles qui prennent en charge la publication appropriée des applications .NET.|
|[Règles de fiabilité](../code-quality/reliability-warnings.md)|Règles qui prennent en charge la fiabilité des bibliothèques et des applications, telles que la mémoire et l’utilisation des threads.|
|[Règles de sécurité](../code-quality/security-warnings.md)|Règles qui prennent en charge des bibliothèques et des applications plus sûres.|
|[Règles d’utilisation](../code-quality/usage-warnings.md)|Règles qui prennent en charge l’utilisation appropriée de .NET.|
