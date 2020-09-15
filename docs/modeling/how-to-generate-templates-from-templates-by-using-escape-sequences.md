---
title: Générer un modèle de texte à partir d’un modèle de texte
description: Fournit des informations sur la façon de générer un modèle de texte à partir d’un autre modèle de texte à l’aide de séquences d’échappement.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, generating templates from templates
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: d7ef983525842023247433e7a3c2b51e206a1cee
ms.sourcegitcommit: a18c7e9b367c2f92f6e54c3eaef442775d457667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90100759"
---
# <a name="how-to-generate-templates-from-templates-by-using-escape-sequences"></a>Comment : générer des modèles à partir de modèles à l'aide de séquences d'échappement
Vous pouvez créer un modèle de texte qui crée un autre modèle de texte comme sortie de texte générée. Pour ce faire, vous devez utiliser des séquences d’échappement pour détourer les balises de modèle de texte. Si vous n’utilisez pas de séquences d’échappement, votre modèle de texte généré aura une signification prédéfinie. Pour plus d’informations sur l’utilisation de séquences d’échappement dans les modèles de texte, consultez [utilisation de séquences d’échappement dans des modèles de texte](../modeling/using-escape-sequences-in-text-templates.md).

### <a name="to-generate-a-text-template-from-within-a-text-template"></a>Pour générer un modèle de texte à partir d’un modèle de texte

- Utilisez la barre oblique inverse ( \\ ) comme caractère d’échappement pour produire les balises de balisage nécessaires dans le modèle de texte pour les directives, les instructions, les expressions et les fonctionnalités de classe dans un fichier de modèle de texte séparé.

    ```
    \<#@ directive \#>
    \<# statement \#>
    \<#= expression \#>
    \<#+ classfeature \#>
    ```

## <a name="example"></a> Exemple
 L’exemple suivant utilise des caractères d’échappement pour produire un modèle de texte à partir d’un modèle de texte. La `output` directive définit le type de fichier de destination sur le type de fichier de modèle de texte (. TT).

```csharp
\<#@ output extension=".tt" \#>
\<#@ assembly name="System.Xml.dll" \#>
\<#@ import namespace="System.Xml" \#>
\<#
XmlDocument xDoc = new XmlDocument();
//System.Diagnostics.Debugger.Break();
    xDoc.Load(@"E:\CSharp\Overview.xml");
    XmlAttributeCollection attributes = xDoc.Attributes;
    if (attributes != null)
    {
       foreach (XmlAttribute attr in attributes)
       {\#>
           \<#= attr.Name \#>
       \<#}
     }
\#>
```

 La sortie de texte générée est un modèle de texte.

```
<#@ output extension=".tt" #>
<#@ assembly name="System.Xml.dll" #>
<#@ import namespace="System.Xml" #>
<#
XmlDocument xDoc = new XmlDocument();
//System.Diagnostics.Debugger.Break();
    xDoc.Load(@"E:\CSharp\Overview.xml");
    XmlAttributeCollection attributes = xDoc.Attributes;
    if (attributes != null)
    {
       foreach (XmlAttribute attr in attributes)
       {#>
           <#= attr.Name #>
       <#}
     }
#>
```
