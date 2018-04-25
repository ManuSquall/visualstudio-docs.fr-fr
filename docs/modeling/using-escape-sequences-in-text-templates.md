---
title: Utilisation de séquences d'échappement dans des modèles de texte
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, escape sequences
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: ef3cb58c9352e81fc959dfdd2ddebd354e834fbf
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2018
---
# <a name="using-escape-sequences-in-text-templates"></a>Utilisation de séquences d'échappement dans des modèles de texte
Vous pouvez utiliser des séquences d’échappement dans les modèles de texte pour générer des balises de modèle de texte et (dans le code c# uniquement) d’échappement les caractères de contrôle et des guillemets doubles.

 Pour imprimer les balises d’ouverts et de clôture pour un bloc de code standard dans le fichier de sortie, échappez les balises comme suit :

```
\<# ... \#>
```

 Vous pouvez faire de même avec d’autres balises de bloc texte modèle la directive et le code.

 Si un bloc de texte inclut des chaînes utilisées pour échapper des balises de modèle de texte, vous pouvez utiliser les séquences d’échappement suivantes :

-   Si une balise de modèle de texte est précédée d’un nombre pair de d’échappement (\\) caractères le modèle d’analyseur sera incluent la moitié des caractères d’échappement et la séquence comme une balise de modèle de texte. Par exemple, s’il existe quatre caractères d’échappement dans le modèle de texte, il y aura deux «\\» caractères dans le fichier généré.

-   Si la balise de modèle de texte est précédée d’un nombre impair d’échappement (\\) caractères, l’Analyseur de modèle inclura la moitié de la «\\» caractères ainsi que la balise elle-même (\<# ou #>). La balise n’est pas considérée comme une balise de modèle de texte.

-   Si un caractère d’échappement (\\) caractère apparaît nulle part ailleurs dans n’importe quelle séquence qu’où il échappe les caractères de contrôle ou un guillemet (en c# uniquement), le caractère affichera directement.

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour générer des modèles à partir de modèles à l’aide de séquences d’échappement](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)