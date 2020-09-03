---
title: Avertissements de la documentation
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
ms.openlocfilehash: 4946c69bbbe4bf1c240967ebd93ef58cfa79e333
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72807100"
---
# <a name="documentation-warnings"></a>Avertissements de la documentation

Les avertissements de documentation prennent en charge l’écriture de bibliothèques bien documentées via l’utilisation correcte des [Commentaires de documentation XML](/dotnet/csharp/codedoc) pour les API visibles de l’extérieur.

## <a name="in-this-section"></a>Contenu de cette section

| Règle | Description |
| - | - |
| [CA1200 : Éviter d’utiliser des balises cref avec un préfixe](../code-quality/ca1200.md) | L’attribut [cref](/dotnet/csharp/programming-guide/xmldoc/cref-attribute) dans une balise de documentation XML signifie « référence du code ». Il indique que le texte interne de la balise est un élément de code tel qu’un type, une méthode ou une propriété. Évitez `cref` d’utiliser des balises avec des préfixes, car cela empêche le compilateur de vérifier les références. Cela empêche également l’environnement de développement intégré (IDE) de Visual Studio de rechercher et de mettre à jour ces références de symboles lors des refactorisations. |

## <a name="see-also"></a>Voir aussi

- [Avertissements d’analyse du code](../code-quality/code-analysis-for-managed-code-warnings.md)
