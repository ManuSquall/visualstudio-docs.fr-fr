---
title: "Cascade de paramètres | Outil de test Microsoft IntelliTest pour les développeurs | Microsoft Docs"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IntelliTest, Settings waterfall
ms.author: gewarren
manager: ghogen
ms.workload: multiple
author: gewarren
ms.openlocfilehash: b782987dd3bf1b96c063d43d80634289e5165af7
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2018
---
# <a name="settings-waterfall"></a>Cascade de paramètres

Le concept de cascade de paramètres signifie que l’utilisateur peut spécifier des paramètres au niveau **Assembly**, **Attachement** et **Exploration** : 

* Assembly : [PexAssemblySettings](attribute-glossary.md#pexassemblysettings)
* Attachement : [PexClass](attribute-glossary.md#pexclass)
* Exploration : [PexExplorationAttributeBase](attribute-glossary.md#pexexplorationattributebase)

Les paramètres spécifiés au niveau **Assembly** affectent tous les attachements et l’exploration sous cet assembly. Les paramètres spécifiés au niveau **Attachement** affectent toutes les explorations sous cet attachement. Les paramètres enfants l’emportent : si un paramètre est défini aux niveaux **Assembly** et **Attachement**, les paramètre du niveau **Attachement** sont utilisés.

Notez que certains paramètres sont spécifiques au niveau **Assembly** ou au niveau **Attachement**. 

**Exemple**

```
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

Postez vos idées et demandes de fonctionnalités sur **[UserVoice](https://visualstudio.uservoice.com/forums/121579-visual-studio-2015/category/157869-test-tools?query=IntelliTest)**.
