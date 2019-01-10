---
title: Cascade de paramètres | Outil de test Microsoft IntelliTest pour les développeurs
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Settings waterfall
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: c15b440845f918c194bad334e118e25dee676431
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53936163"
---
# <a name="settings-waterfall"></a>Cascade de paramètres

Le concept de cascade de paramètres signifie que l’utilisateur peut spécifier des paramètres au niveau **Assembly**, **Attachement** et **Exploration** :

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