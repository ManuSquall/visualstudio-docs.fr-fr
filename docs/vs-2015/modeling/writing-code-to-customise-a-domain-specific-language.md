---
title: Écriture de code pour personnaliser un langage spécifique à un domaine | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming
ms.assetid: a4a17f5b-9c97-4575-b2d1-3182c1896b72
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4448e9a1c65ccba4a9ae48d0271f9fd91fc011b6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662971"
---
# <a name="writing-code-to-customise-a-domain-specific-language"></a>Écriture de code pour personnaliser un langage spécifique à un domaine
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette section vous montre comment utiliser du code personnalisé pour accéder, modifier ou créer un modèle dans un langage spécifique à un domaine.

 Il existe plusieurs contextes dans lesquels vous pouvez écrire du code qui fonctionne avec un DSL :

- **Commandes personnalisées.** Vous pouvez créer une commande que les utilisateurs peuvent appeler en cliquant avec le bouton droit sur le diagramme et en modifiant le modèle. Pour plus d’informations, consultez [Comment : ajouter une commande au menu contextuel](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).

- **Métrage.** Vous pouvez écrire du code qui vérifie que le modèle est dans un état correct. Pour plus d’informations, consultez [validation dans un langage spécifique à un domaine](../modeling/validation-in-a-domain-specific-language.md).

- **Substitution du comportement par défaut.** Vous pouvez modifier de nombreux aspects du code généré à partir de DslDefinition. DSL. Pour plus d’informations, consultez [substitution et extension des classes générées](../modeling/overriding-and-extending-the-generated-classes.md).

- **Transformation de texte.** Vous pouvez écrire des modèles de texte qui contiennent du code qui accède à un modèle et génère un fichier texte, par exemple pour générer du code de programme. Pour plus d’informations, consultez [génération de code à partir d’un langage spécifique à un domaine](../modeling/generating-code-from-a-domain-specific-language.md).

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
 [Personnalisation et extension d’un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md)
