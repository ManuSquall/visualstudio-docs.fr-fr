---
title: Utilisation de séquences d'échappement dans des modèles de texte
description: Découvrez comment vous pouvez utiliser des séquences d’échappement dans des modèles de texte pour générer des balises de modèle de texte et des caractères de contrôle d’échappement et des guillemets dans le code C# uniquement.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, escape sequences
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8b007a9b5ccf41a27cda7d9833064eb60394c4dc
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/12/2020
ms.locfileid: "97361324"
---
# <a name="use-escape-sequences-in-text-templates"></a>Utiliser des séquences d’échappement dans des modèles de texte

Vous pouvez utiliser des séquences d’échappement dans des modèles de texte pour générer des balises de modèle de texte et (dans du code C# uniquement) pour échapper des caractères de contrôle et des guillemets.

Pour imprimer les balises d’ouverture et de fermeture d’un bloc de code standard dans le fichier de sortie, échappez les balises comme suit :

```
\<# ... \#>
```

Vous pouvez faire de même avec d’autres balises de modèle de texte et de bloc de code.

Si un bloc de texte comprend des chaînes utilisées pour échapper des balises de modèle de texte, vous pouvez utiliser les séquences d’échappement suivantes :

- Si une balise de modèle de texte est précédée d’un nombre pair de caractères d’échappement ( \\ ), l’analyseur de modèle inclura la moitié des caractères d’échappement et inclura la séquence comme une balise de modèle de texte. Par exemple, s’il y a quatre caractères d’échappement dans le modèle de texte, il y aura deux \\ caractères «» dans le fichier généré.

- Si la balise de modèle de texte est précédée d’un nombre impair de caractères d’échappement ( \\ ), l’analyseur de modèle inclura la moitié des \\ caractères «» plus la balise proprement dite ( \<# or #> ). La balise n’est pas considérée comme une balise de modèle de texte.

- Si un caractère d’échappement ( \\ ) apparaît n’importe où dans une séquence autre que l’échappement d’un caractère de contrôle ou d’un guillemet (en C# uniquement), le caractère sera généré directement.

## <a name="see-also"></a>Voir aussi

- [Comment : générer des modèles à partir de modèles à l'aide de séquences d'échappement](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)
