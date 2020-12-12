---
title: Directive de sortie T4
description: Découvrez que dans les modèles de texte Visual Studio, la directive de sortie est utilisée pour définir l’extension de nom de fichier et l’encodage du fichier transformé.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b9849a326549aa534d9cd558337b825b7e0b8d1f
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363638"
---
# <a name="t4-output-directive"></a>Directive de sortie T4

Dans les modèles de texte Visual Studio, la `output` directive est utilisée pour définir l’extension de nom de fichier et l’encodage du fichier transformé.

 Par exemple, si votre projet Visual Studio inclut un fichier de modèle nommé **MyTemplate.TT** qui contient la directive suivante :

 `<#@output extension=".cs"#>`

 Ensuite, Visual Studio génère un fichier nommé **MyTemplate.cs**

 La directive `output` n'est pas obligatoire dans un modèle de texte au moment de l'exécution (prétraité). Au lieu de cela, votre application obtient la chaîne générée en appelant `TextTransform()`. Pour plus d’informations, consultez [génération de texte au moment de l’exécution avec des modèles de texte T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

## <a name="using-the-output-directive"></a>Utilisation de la directive Output

```
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>
```

 Il ne doit pas y avoir plus d'une directive `output` dans chaque modèle de texte.

## <a name="extension-attribute"></a>attribut d’extension
 Spécifie l’extension de nom de fichier du fichier de sortie texte généré.

 La valeur par défaut est **. cs**

 Exemples : `<#@ output extension=".txt" #>`

 `<#@ output extension=".htm" #>`

 `<#@ output extension=".cs" #>`

 `<#@ output extension=".vb" #>`

 Valeurs acceptables : toute extension de nom de fichier valide.

## <a name="encoding-attribute"></a>attribut d’encodage
 Spécifie l'encodage à utiliser lors de la génération du fichier de sortie. Par exemple :

 `<#@ output encoding="utf-8"#>`

 La valeur par défaut est l'encodage utilisé par le fichier de modèle de texte.

 Valeurs acceptables : `us-ascii`

 `utf-16BE`

 `utf-16`

 `utf-8`

 `utf-7`

 `utf-32`

 `0` (Valeur système par défaut)

 En général, vous pouvez utiliser la chaîne WebName ou le nombre CodePage de n'importe lequel des encodages retournés par <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=fullName>.
