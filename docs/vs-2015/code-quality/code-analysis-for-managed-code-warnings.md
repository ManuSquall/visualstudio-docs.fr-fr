---
title: Analyse du code pour les avertissements liés au code managé | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vc.project.vcfxcoptool.enablefxcop
helpviewer_keywords:
- managed code analyis, warnings
- warnings, managed code analysis
- managed code analysis warnings
- code analysis,managed code
ms.assetid: 3c2741ff-0d3a-42e6-acd5-d42310bd03c4
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: fddcff8bb51216097689a86bd25718a0727c2b45
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672936"
---
# <a name="code-analysis-for-managed-code-warnings"></a>Analyse du code pour les avertissements liés au code managé
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L’outil Analyse du code managé fournit des avertissements qui indiquent des violations de règle dans les bibliothèques de code managé. Les avertissements sont organisés en domaines de règles, tels que la conception, la localisation, les performances et la sécurité. Chaque avertissement indique une violation d’une règle d’analyse du code managé. Cette section fournit des explications et des exemples détaillés de chaque avertissement d’analyse du code managé.

 Le tableau suivant indique le type d’informations fourni pour chaque avertissement.

|Élément|Description|
|----------|-----------------|
|Tapez|TypeName de la règle.|
|CheckId|Identificateur unique de la règle. CheckId et Category sont utilisés pour la suppression à la source d’un avertissement.|
|Category|Catégorie de l’avertissement.|
|Modification avec rupture|Indique si la correction d’une violation de la règle constitue une modification avec rupture. Une modification avec rupture signifie qu’un assembly qui présente une dépendance à la cible ayant provoqué la violation ne se recompile pas avec la nouvelle version corrigée ou peut échouer au moment de l’exécution en raison de la modification. Quand plusieurs corrections sont possibles et qu’au moins l’une d’elles est une modification avec rupture et qu’une autre ne l’est pas, les caractéristiques « Avec rupture » et « Sans rupture » sont toutes deux spécifiées.|
|Cause|Code managé spécifique qui contraint la règle à générer un avertissement.|
|Description|Décrit les problèmes sous-jacents à l’avertissement.|
|Comment corriger les violations|Explique comment modifier le code source pour satisfaire la règle et l’empêcher de générer un avertissement.|
|Quand supprimer les avertissements|Décrit les circonstances dans lesquelles il est possible de supprimer un avertissement de la règle en toute sécurité.|
|Exemple de code|Exemples qui violent la règle et exemples corrigés qui satisfont la règle.|
|Avertissements connexes|Avertissements connexes.|

## <a name="in-this-section"></a>Dans cette section

|||
|-|-|
|[Avertissements par CheckId](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)|Répertorie tous les avertissements par CheckId.|
|[Avertissements relatifs au chiffrement](../code-quality/cryptography-warnings.md)|Avertissements gérant la sécurité des bibliothèques et des applications via l’utilisation correcte du chiffrement.|
|[Avertissements liés à la conception](../code-quality/design-warnings.md)|Avertissements gérant la conception correcte des bibliothèques, telle qu’elle est spécifiée dans les règles de conception de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .|
|[Avertissements liés à la globalisation](../code-quality/globalization-warnings.md)|Avertissements gérant les applications et les bibliothèques universelles.|
|[Avertissements liés à l’interopérabilité](../code-quality/interoperability-warnings.md)|Avertissements gérant l’interaction avec les clients COM.|
|[Avertissements liés à la facilité de maintenance](../code-quality/maintainability-warnings.md)|Avertissements gérant la maintenance des bibliothèques et des applications.|
|[Mobility Warnings](../code-quality/mobility-warnings.md)|Avertissements gérant l’optimisation de la consommation d’énergie.|
|[Avertissements liés à l’affectation de noms](../code-quality/naming-warnings.md)|Avertissements gérant le respect des conventions d’affectation des noms définies dans les règles de conception de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .|
|[Avertissements liés aux performances](../code-quality/performance-warnings.md)|Avertissements gérant les hautes performances des applications et des bibliothèques.|
|[Avertissements liés à la portabilité](../code-quality/portability-warnings.md)|Avertissements gérant la portabilité sur différentes plateformes.|
|[Avertissements liés à la fiabilité](../code-quality/reliability-warnings.md)|Avertissements gérant la fiabilité des bibliothèques et des applications, notamment une utilisation adaptée des threads et de la mémoire.|
|[Avertissements liés à la sécurité](../code-quality/security-warnings.md)|Avertissements gérant la sécurité des bibliothèques et des applications.|
|[Avertissements liés à l’utilisation](../code-quality/usage-warnings.md)|Avertissements gérant l’utilisation adéquate de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].|
|[Erreurs de stratégie d’analyse du code](../code-quality/code-analysis-policy-errors.md)|Erreurs qui se produisent si la stratégie d’analyse du code n’est pas satisfaite au moment de l’archivage.|
