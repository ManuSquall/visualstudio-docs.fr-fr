---
title: Utilisation de séquences d’échappement dans des modèles de texte | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, escape sequences
ms.assetid: 36fff542-2f42-460f-a2d5-03fc76817f3b
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8a45aa36ddce57141a7e1e851f7f0766b77015ee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659419"
---
# <a name="using-escape-sequences-in-text-templates"></a>Utilisation de séquences d'échappement dans des modèles de texte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 [Comment : générer des modèles à partir de modèles à l'aide de séquences d'échappement](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)
