---
title: Bonnes pratiques pour MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- best practices, MSBuild
- MSBuild, best practices
ms.assetid: 90ef8693-e921-410a-a377-fe4d13f58c48
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 91b2e157ee64f5e4d91bc75a5d6f8d65d4312862
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "78263147"
---
# <a name="msbuild-best-practices"></a>Bonnes pratiques pour MSBuild

Nous vous recommandons les meilleures pratiques suivantes pour l'écriture de scripts MSBuild :

- Les valeurs de propriété par défaut sont mieux gérées en utilisant l'attribut `Condition` plutôt qu'en déclarant une propriété dont la valeur par défaut peut être substituée sur la ligne de commande. Par exemple, utilisez

```xml
<MyProperty Condition="'$(MyProperty)' == ''">
   MyDefaultValue
</MyProperty>
```

- En général, évitez l’utilisation de wildcards lorsque vous sélectionnez des éléments. Spécifiez plutôt les fichiers de manière explicite. C’est parce que dans la plupart des types de projet, MSBuild élargit wildcards à divers moments, comme lors de l’ajout ou la suppression des éléments, ce qui peut conduire à un comportement inattendu. Une exception à cela est dans .NET Core SDK-style projets, qui ne traitent wildcards correctement.

## <a name="see-also"></a>Voir aussi

- [Concepts avancés](../msbuild/msbuild-advanced-concepts.md)
