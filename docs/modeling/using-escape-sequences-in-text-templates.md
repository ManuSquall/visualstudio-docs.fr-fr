---
title: Utilisation de séquences d'échappement dans des modèles de texte
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, escape sequences
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 83e6e5cf163037077d0517e5f7ea460f9124f27c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75594043"
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
