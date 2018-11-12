---
title: Cascade de paramètres | Outil de test Microsoft IntelliTest pour les développeurs
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Settings waterfall
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 27eb9b7e3cda7c05515f5a7413b067dce2b8567e
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51000398"
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