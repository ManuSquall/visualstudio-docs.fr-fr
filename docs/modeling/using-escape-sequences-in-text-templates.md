---
title: Utilisation de séquences d'échappement dans des modèles de texte
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, escape sequences
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4e03f5eafc00b8431725ed06da10371a93692fb5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662920"
---
# <a name="use-escape-sequences-in-text-templates"></a>Utiliser des séquences d’échappement dans des modèles de texte

Vous pouvez utiliser des séquences d’échappement dans des modèles de texte pour générer des balises de modèle de texte et (dans C# le code uniquement) pour échapper des caractères de contrôle et des guillemets.

Pour imprimer les balises d’ouverture et de fermeture d’un bloc de code standard dans le fichier de sortie, échappez les balises comme suit :

```
\<# ... \#>
```

Vous pouvez faire de même avec d’autres balises de modèle de texte et de bloc de code.

Si un bloc de texte comprend des chaînes utilisées pour échapper des balises de modèle de texte, vous pouvez utiliser les séquences d’échappement suivantes :

- Si une balise de modèle de texte est précédée d’un nombre pair de caractères d’échappement (\\), l’analyseur de modèle inclura la moitié des caractères d’échappement et inclura la séquence comme une balise de modèle de texte. Par exemple, s’il y a quatre caractères d’échappement dans le modèle de texte, il y aura deux caractères « \\ » dans le fichier généré.

- Si la balise de modèle de texte est précédée d’un nombre impair de caractères d’échappement (\\), l’analyseur de modèle inclura la moitié des caractères « \\ » et la balise proprement dite (\< # ou # >). La balise n’est pas considérée comme une balise de modèle de texte.

- Si un caractère d’échappement (\\) apparaît n’importe où dans une séquence autre que l’échappement d’un caractère de contrôle ou d’un C# guillemet (dans uniquement), le caractère est généré directement.

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour générer des modèles à partir de modèles à l’aide de séquences d’échappement](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)