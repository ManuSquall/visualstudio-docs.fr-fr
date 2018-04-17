---
title: 'CA1716 : Les identificateurs ne doivent pas correspondre aux mots clés | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
helpviewer_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
ms.assetid: 900cc8a1-1089-4069-a4ce-10b109ac4fab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c695f66a096614621cee2f38aed3e8fd6d970bed
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="ca1716-identifiers-should-not-match-keywords"></a>CA1716 : Les identificateurs ne doivent pas correspondre à des mots clés
|||  
|-|-|  
|TypeName|IdentifiersShouldNotMatchKeywords|  
|CheckId|CA1716|  
|Category|Microsoft.Naming|  
|Modification avec rupture|Rupture|  
  
## <a name="cause"></a>Cause  
 Un nom d’un espace de noms, un type ou un membre d’interface ou virtuel correspond à un mot clé réservé dans un langage de programmation.  
  
## <a name="rule-description"></a>Description de la règle  
 Identificateurs des espaces de noms, types et virtuels et les membres d’interface ne doivent pas correspondre aux mots clés définis par les langages qui ciblent le common language runtime. Selon le langage utilisé et le mot clé, ambiguïtés et les erreurs du compilateur peuvent rendre la bibliothèque difficile à utiliser.  
  
 Cette règle vérifie par rapport aux mots clés dans les langues suivantes :  
  
-   Visual Basic  
  
-   C#  
  
-   C++/CLI  
  
 Comparaison respectant la casse est utilisé pour [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] les mots clés et une comparaison respectant la casse est utilisé pour les autres langues.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Sélectionnez un nom qui n’apparaît pas dans la liste de mots clés.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Vous pouvez supprimer un avertissement de cette règle si vous êtes sûr que l’identificateur sera confondez pas les utilisateurs de l’API, et que la bibliothèque est utilisable dans toutes les langues disponibles dans le [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].