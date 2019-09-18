---
title: Avertissements de documentation
ms.date: 09/16/2019
ms.topic: reference
f1_keywords:
- vs.codeanalysis.documentationrules
helpviewer_keywords:
- documentation warnings
- managed code analysis warnings, documentation warnings
- warnings, documentation
author: mavasani
ms.author: mavasani
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 00b42dc20b228e30a9b2632a0525a1ec8a9ddbb1
ms.sourcegitcommit: 541a0556958201ad6626bc8638406ad02640f764
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71079211"
---
# <a name="documentation-warnings"></a>Avertissements de documentation

Les avertissements de documentation prennent en charge l’écriture de bibliothèques bien documentées via l’utilisation correcte des [Commentaires de documentation XML](https://docs.microsoft.com/dotnet/csharp/codedoc) pour les API visibles de l’extérieur.

## <a name="in-this-section"></a>Dans cette section

| Règle | Description |
| - | - |
| [CA1200 : Évitez d’utiliser des balises CREF avec un préfixe](../code-quality/ca1200.md) | L’attribut [cref](https://docs.microsoft.com/dotnet/csharp/programming-guide/xmldoc/cref-attribute) dans une balise de documentation XML signifie « référence du code ». Il indique que le texte interne de la balise est un élément de code tel qu’un type, une méthode ou une propriété. Évitez d' `cref` utiliser des balises avec des préfixes, car cela empêche le compilateur de vérifier les références. Cela empêche également l’environnement de développement intégré (IDE) de Visual Studio de rechercher et de mettre à jour ces références de symboles lors des refactorisations. |

## <a name="see-also"></a>Voir aussi

- [Avertissements d’analyse du code](../code-quality/code-analysis-for-managed-code-warnings.md)
