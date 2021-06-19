---
title: Personnaliser un langage spécifique à un domaine
description: Apprenez à utiliser du code personnalisé pour accéder, modifier ou créer un modèle dans un langage spécifique à un domaine (DSL).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2231ef94bee01558e2c26899a5d9a0c855489e94
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388046"
---
# <a name="write-code-to-customize-a-domain-specific-language"></a>Écrire du code pour personnaliser un langage spécifique à un domaine

Cette section vous montre comment utiliser du code personnalisé pour accéder, modifier ou créer un modèle dans un langage spécifique à un domaine.

Il existe plusieurs contextes dans lesquels vous pouvez écrire du code qui fonctionne avec un DSL :

- **Commandes personnalisées.** Vous pouvez créer une commande que les utilisateurs peuvent appeler en cliquant avec le bouton droit sur le diagramme et en modifiant le modèle. Pour plus d’informations, consultez [Comment : ajouter une commande au menu contextuel](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).

- **Métrage.** Vous pouvez écrire du code qui vérifie que le modèle est dans un état correct. Pour plus d’informations, consultez [validation dans un langage de Domain-Specific](../modeling/validation-in-a-domain-specific-language.md).

- **Substitution du comportement par défaut.** Vous pouvez modifier de nombreux aspects du code généré à partir de DslDefinition. DSL. Pour plus d’informations, consultez [substitution et extension des classes générées](../modeling/overriding-and-extending-the-generated-classes.md).

- **Transformation de texte.** Vous pouvez écrire des modèles de texte qui contiennent du code qui accède à un modèle et génère un fichier texte, par exemple pour générer du code de programme. Pour plus d’informations, consultez [génération de code à partir d’un langage de Domain-Specific](../modeling/generating-code-from-a-domain-specific-language.md).

- **Autres extensions Visual Studio.** Vous pouvez écrire des extensions VSIX distinctes qui lisent et modifient des modèles. Pour plus d’informations, consultez [Comment : ouvrir un modèle à partir d’un fichier dans le code de programme](../modeling/how-to-open-a-model-from-file-in-program-code.md)

Les instances des classes que vous définissez dans DslDefinition. DSL sont conservées dans une structure de données appelée *magasin en mémoire* (IMS) ou *Store*. Les classes que vous définissez dans un DSL prennent toujours un magasin comme argument pour le constructeur. Par exemple, si votre DSL définit une classe appelée exemple :

`Example element = new Example (theStore);`

le fait de conserver des objets dans le magasin (plutôt que simplement des objets ordinaires) offre plusieurs avantages.

- **Transactions**. Vous pouvez regrouper une série de modifications associées dans une transaction :

     `using (Transaction t = store.TransactionManager.BeginTransaction("updates"))`

     `{`

     `// make several changes to Store elements here`

     `t.Commit();`

     `}`

     Si une exception se produit pendant les modifications, de sorte que la validation finale () n’est pas effectuée, le magasin est rétabli à son état précédent. Cela vous permet de vous assurer que les erreurs ne laissent pas le modèle dans un état incohérent. Pour plus d’informations, consultez [navigation et mise à jour d’un modèle dans le code de programme](../modeling/navigating-and-updating-a-model-in-program-code.md).

- **Relations binaires**. Si vous définissez une relation entre deux classes, les instances aux deux extrémités ont une propriété qui navigue vers l’autre terminaison. Les deux extrémités sont toujours synchronisées. Par exemple, si vous définissez une relation Parenthood avec des rôles nommés parents et enfants, vous pouvez écrire :

     `John.Children.Add(Mary)`

     Les deux expressions suivantes sont maintenant vraies :

     `John.Children.Contains(Mary)`

     `Mary.Parents.Contains(John)`

     Vous pouvez également obtenir le même effet en écrivant :

     `Mary.Parents.Add(John)`

     Pour plus d’informations, consultez [navigation et mise à jour d’un modèle dans le code de programme](../modeling/navigating-and-updating-a-model-in-program-code.md).

- **Règles et événements**. Vous pouvez définir des règles qui se déclenchent à chaque fois que des modifications spécifiées sont apportées. Des règles sont utilisées, par exemple, pour maintenir à jour les formes sur le diagramme avec les éléments de modèle qu’elles présentent. Pour plus d’informations, consultez [réponse aux modifications et propagation](../modeling/responding-to-and-propagating-changes.md).

- **Sérialisation**. Le magasin fournit une méthode standard pour sérialiser les objets qu’il contient dans un fichier. Vous pouvez personnaliser les règles de sérialisation et de désérialisation. Pour plus d’informations, consultez [Personnalisation du stockage de fichiers et SÉRIALISATION XML](../modeling/customizing-file-storage-and-xml-serialization.md).

## <a name="see-also"></a>Voir aussi

- [Personnalisation et extension d’un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md)