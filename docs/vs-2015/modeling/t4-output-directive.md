---
title: Directive de sortie T4 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 03a14993-47ad-4f2e-8032-57db28d5842a
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 149370bfee1b142876dff881625d08083afadea4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652313"
---
# <a name="t4-output-directive"></a>Directive de sortie T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans les modèles de texte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], la directive `output` sert à définir l'extension du nom de fichier et l'encodage du fichier transformé.

 Par exemple, si votre projet [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] inclut un fichier de modèle nommé **MyTemplate.TT** qui contient la directive suivante :

 `<#@output extension=".cs"#>`

 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] générera ensuite un fichier nommé **MyTemplate.cs**

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
 Spécifie l'encodage à utiliser lors de la génération du fichier de sortie. Exemple :

 `<#@ output encoding="utf-8"#>`

 La valeur par défaut est l'encodage utilisé par le fichier de modèle de texte.

 Valeurs acceptables : `us-ascii`

 `utf-16BE`

 `utf-16`

 `utf-8`

 `utf-7`

 `utf-32`

 `0` (valeur système par défaut)

 En général, vous pouvez utiliser la chaîne WebName ou le nombre CodePage de n'importe lequel des encodages retournés par <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=fullName>.
