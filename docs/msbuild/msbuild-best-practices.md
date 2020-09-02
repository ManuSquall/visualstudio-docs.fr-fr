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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
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

- En général, évitez d’utiliser des caractères génériques lorsque vous sélectionnez des éléments. Spécifiez plutôt les fichiers de manière explicite. En effet, dans la plupart des types de projets, MSBuild développe des caractères génériques à différents moments, par exemple lors de l’ajout ou de la suppression d’éléments, ce qui peut entraîner un comportement inattendu. Une exception est dans les projets de style kit SDK .NET Core, qui traitent correctement les caractères génériques.

## <a name="see-also"></a>Voir aussi

- [Concepts avancés](../msbuild/msbuild-advanced-concepts.md)
