---
title: L’écriture de Code pour personnaliser un langage spécifique à un domaine | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: cb058ba2467ae852491339dc64a3fba837249688
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="writing-code-to-customise-a-domain-specific-language"></a>Écriture de code pour personnaliser un langage spécifique à un domaine
Cette section vous montre comment utiliser un code personnalisé pour accéder, modifier ou créer un modèle dans un langage spécifique à un domaine.  
  
 Il existe plusieurs contextes dans lesquels vous pouvez écrire du code qui fonctionne avec une DSL :  
  
-   **Commandes personnalisées.** Vous pouvez créer une commande que les utilisateurs peuvent appeler en cliquant sur le diagramme, et qui peut modifier le modèle. Pour plus d’informations, consultez [Comment : ajouter une commande au Menu contextuel](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).  
  
-   **Validation.** Vous pouvez écrire du code qui vérifie que le modèle est dans un état correct. Pour plus d’informations, consultez [Validation dans un langage spécifique à un domaine](../modeling/validation-in-a-domain-specific-language.md).  
  
-   **Substitution du comportement par défaut.** Vous pouvez modifier de nombreux aspects du code qui est généré à partir de DslDefinition.dsl. Pour plus d’informations, consultez [substituer et étendre les Classes générées](../modeling/overriding-and-extending-the-generated-classes.md).  
  
-   **Transformation de texte.** Vous pouvez écrire des modèles de texte qui contiennent du code qui accède à un modèle et génère un fichier texte, par exemple, pour générer le code de programme. Pour plus d’informations, consultez [génération du Code à partir d’un langage spécifique à un domaine](../modeling/generating-code-from-a-domain-specific-language.md).  
  
-   **Autres extensions de Visual Studio.** Vous pouvez écrire des extensions VSIX distinctes qui lisent et modifier des modèles. Pour plus d’informations, consultez [Comment : ouvrir un modèle à partir du fichier de Code de programme](../modeling/how-to-open-a-model-from-file-in-program-code.md)  
  
 Instances des classes que vous définissez dans DslDefinition.dsl sont conservés dans une structure de données appelée la *magasin en mémoire* (IMS) ou *magasin*. Les classes que vous définissez dans une DSL toujours prennent un magasin en tant qu’argument au constructeur. Par exemple, si votre DSL définit une classe appelée exemple :  
  
 `Example element = new Example (theStore);`  
  
 conservation des objets dans le magasin (au lieu d’objets simplement comme ordinaires) offre plusieurs avantages.  
  
-   **Transactions**. Vous pouvez regrouper une série de modifications connexes dans une transaction :  
  
     `using (Transaction t = store.TransactionManager.BeginTransaction("updates"))`  
  
     `{`  
  
     `// make several changes to Store elements here`  
  
     `t.Commit();`  
  
     `}`  
  
     Si une exception se produit pendant les modifications, afin que la dernière Commit() n’est pas effectuée, le magasin réinitialisera à son état précédent. Cela vous permet de vous assurer que les erreurs ne laissent pas le modèle dans un état incohérent. Pour plus d’informations, consultez [navigation et la mise à jour d’un modèle de Code de programme](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
-   **Les relations binaires**. Si vous définissez une relation entre deux classes, instances aux deux extrémités ont une propriété qui accède à l’autre extrémité. Les deux extrémités sont toujours synchronisées. Par exemple, si vous définissez une relation à la parenté avec des rôles nommés Parents et enfants, vous pouvez écrire :  
  
     `John.Children.Add(Mary)`  
  
     Maintenant, les deux expressions suivantes sont vraies :  
  
     `John.Children.Contains(Mary)`  
  
     `Mary.Parents.Contains(John)`  
  
     Vous pouvez également obtenir le même effet en écrivant :  
  
     `Mary.Parents.Add(John)`  
  
     Pour plus d’informations, consultez [navigation et la mise à jour d’un modèle de Code de programme](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
-   **Les règles et les événements**. Vous pouvez définir des règles qui se déclenchent chaque fois que les modifications sont apportées. Les règles sont utilisées, par exemple, pour maintenir à jour avec les éléments de modèle qu’elles présentent les formes sur le diagramme. Pour plus d’informations, consultez [réponse aux et propager les modifications](../modeling/responding-to-and-propagating-changes.md).  
  
-   **Sérialisation**. Le magasin est un moyen standard pour sérialiser les objets qu’il contient dans un fichier. Vous pouvez personnaliser les règles pour la sérialisation et la désérialisation. Pour plus d’informations, consultez [personnalisation de stockage de fichier et la sérialisation XML](../modeling/customizing-file-storage-and-xml-serialization.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Personnalisation et extension d’un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md)