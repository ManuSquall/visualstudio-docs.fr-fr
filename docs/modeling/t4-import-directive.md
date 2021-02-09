---
title: Directive d'importation T4
description: Découvrez que dans un modèle de texte T4 Visual Studio, la directive import vous permet de faire référence à des éléments d’un autre espace de noms sans fournir de nom complet.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d9eb50261b346d8751a76817d97d59a798d17236
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899663"
---
# <a name="t4-import-directive"></a>Directive d'importation T4

Dans les blocs de code d’un modèle de texte T4 Visual Studio, la `import` directive vous permet de faire référence à des éléments d’un autre espace de noms sans fournir de nom complet. Cela équivaut à `using` en C# ou à `imports` en [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)].

Pour obtenir une vue d’ensemble générale de l’écriture de modèles de texte T4, consultez [écriture d’un modèle de texte T4](../modeling/writing-a-t4-text-template.md).

## <a name="using-the-import-directive"></a>Utilisation de la directive d'importation

```
<#@ import namespace="namespace" #>
```

 Dans cet exemple, le code du modèle peut omettre un espace de noms explicite pour les membres de System.IO :

```
<#@ import namespace="System.IO" #>
<#
   string fileContent = File.ReadAllText("C:\x.txt"); // System.IO.File
#>
The file contains: <#=  fileContent #>
```

## <a name="standard-imports"></a>Importations standard
 L'espace de noms suivant est importé automatiquement, afin que vous n'ayez pas besoin d'écrire une directive d'importation pour lui :

- `System`

  De plus, si vous utilisez une directive personnalisée, le processeur de directive peut importer automatiquement des espaces de noms.

  Par exemple, si vous écrivez des modèles pour un langage spécifique à un domaine (DSL), vous n’avez pas besoin d’importer des directives pour les espaces de noms suivants :

- `Microsoft.VisualStudio.Modeling`

- L’espace de noms de votre DSL

## <a name="see-also"></a>Voir aussi

- [Directive d’assembly T4](../modeling/t4-assembly-directive.md)
