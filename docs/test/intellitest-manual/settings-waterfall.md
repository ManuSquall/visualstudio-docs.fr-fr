---
title: Cascade de paramètres | Outil de test Microsoft IntelliTest pour les développeurs
description: En savoir plus sur les paramètres en cascade, qui organisent les paramètres au niveau de l’assembly, du contexte et de l’exploration.
ms.custom: SEO-VS-2020
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Settings waterfall
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: bdb053218b65924abfa64053a8a3c7e9e0543d49
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329508"
---
# <a name="settings-waterfall"></a>Cascade de paramètres

Le concept de cascade de paramètres signifie que l’utilisateur peut spécifier des paramètres au niveau de l' **assembly**, du **contexte** et de l' **exploration** :

* Assembly : [PexAssemblySettings](attribute-glossary.md#pexassemblysettings)
* Attachement : [PexClass](attribute-glossary.md#pexclass)
* Exploration : [PexExplorationAttributeBase](attribute-glossary.md#pexexplorationattributebase)

Les paramètres spécifiés au niveau **Assembly** affectent tous les attachements et l’exploration sous cet assembly. Les paramètres spécifiés au niveau **Attachement** affectent toutes les explorations sous cet attachement. Les paramètres enfants l’emportent&mdash;si un paramètre est défini aux niveaux **Assembly** et **Attachement**, les paramètre du niveau **Attachement** sont utilisés.

Notez que certains paramètres sont spécifiques au niveau **Assembly** ou au niveau **Attachement**.

**Exemple**

```csharp
using Microsoft.Pex.Framework;

[assembly: PexAssemblySettings(MaxBranches = 1000)] // we override the default value of maxbranches

namespace MyTests
{
    [PexClass(MaxBranches = 500)] // we override the 1000 value and set maxbranches to 500
    public partial class MyTests
    {
        [PexMethod(MaxBranches = 100)] // we override again, maxbranches = 100
        public void MyTest(...) { ... }
    }
}
```

## <a name="got-feedback"></a>Vous avez des commentaires ?

Postez vos idées et demandes de fonctionnalités sur la [Communauté des développeurs](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).
