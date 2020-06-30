---
title: Analyse du code pour les avertissements liés au code managé
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vc.project.vcfxcoptool.enablefxcop
helpviewer_keywords:
- managed code analyis, warnings
- warnings, managed code analysis
- managed code analysis warnings
- code analysis,managed code
ms.assetid: 3c2741ff-0d3a-42e6-acd5-d42310bd03c4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 383f488fcc9ebe614257b035732162100b9c7fd2
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85521054"
---
# <a name="code-analysis-for-managed-code-warnings"></a>Analyse du code pour les avertissements liés au code managé
L’outil Analyse du code managé fournit des avertissements qui indiquent des violations de règle dans les bibliothèques de code managé. Les avertissements sont organisés en domaines de règles, tels que la conception, la localisation, les performances et la sécurité. Chaque avertissement indique une violation d’une règle d’analyse du code managé. Cette section fournit des explications et des exemples détaillés de chaque avertissement d’analyse du code managé.

 Le tableau suivant indique le type d’informations fourni pour chaque avertissement.

|Élément|Description|
|----------|-----------------|
|Type|TypeName de la règle.|
|CheckId|Identificateur unique de la règle. CheckId et Category sont utilisés pour la suppression à la source d’un avertissement.|
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
|[Avertissements par CheckId](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)|Répertorie tous les avertissements par CheckId.|
|[Avertissements de chiffrement](../code-quality/cryptography-warnings.md)|Avertissements gérant la sécurité des bibliothèques et des applications via l’utilisation correcte du chiffrement.|
|[Avertissements de conception](../code-quality/design-warnings.md)|Avertissements qui prennent en charge la conception de bibliothèque correcte, comme spécifié par les instructions de conception .NET.|
|[Avertissements de documentation](../code-quality/documentation-warnings.md)|Avertissements qui prennent en charge la conception de bibliothèque bien documentée via l’utilisation correcte des commentaires de documentation XML.|
|[Avertissements de globalisation](../code-quality/globalization-warnings.md)|Avertissements gérant les applications et les bibliothèques universelles.|
|[Avertissements d’interopérabilité](../code-quality/interoperability-warnings.md)|Avertissements gérant l’interaction avec les clients COM.|
|[Avertissements de maintenabilité](../code-quality/maintainability-warnings.md)|Avertissements gérant la maintenance des bibliothèques et des applications.|
|[Avertissements relatifs à la mobilité](../code-quality/mobility-warnings.md)|Avertissements gérant l’optimisation de la consommation d’énergie.|
|[Avertissements d’attribution de noms](../code-quality/naming-warnings.md)|Avertissements qui prennent en charge l’adhésion aux conventions d’affectation des noms des règles de conception .NET.|
|[Avertissements relatifs aux performances](../code-quality/performance-warnings.md)|Avertissements gérant les hautes performances des applications et des bibliothèques.|
|[Avertissements de portabilité](../code-quality/portability-warnings.md)|Avertissements gérant la portabilité sur différentes plateformes.|
|[Avertissements de fiabilité](../code-quality/reliability-warnings.md)|Avertissements gérant la fiabilité des bibliothèques et des applications, notamment une utilisation adaptée des threads et de la mémoire.|
|[Avertissements de sécurité](../code-quality/security-warnings.md)|Avertissements gérant la sécurité des bibliothèques et des applications.|
|[Avertissements d’utilisation](../code-quality/usage-warnings.md)|Avertissements qui prennent en charge l’utilisation appropriée de .NET.|
|[Code Analysis Policy Errors](../code-quality/code-analysis-policy-errors.md)|Erreurs qui se produisent si la stratégie d’analyse du code n’est pas satisfaite au moment de l’archivage.|
