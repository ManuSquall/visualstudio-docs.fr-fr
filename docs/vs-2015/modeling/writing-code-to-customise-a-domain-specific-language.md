---
title: Écrire du Code pour personnaliser un langage spécifique à un domaine | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, programming
ms.assetid: a4a17f5b-9c97-4575-b2d1-3182c1896b72
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: b9debc18c9d99c9b44b66116ff2f956296fdc19f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49293343"
---
# <a name="writing-code-to-customise-a-domain-specific-language"></a>Écriture de code pour personnaliser un langage spécifique à un domaine
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette section vous montre comment utiliser un code personnalisé pour accéder, modifier ou créer un modèle dans un langage spécifique à un domaine.  
  
 Il existe plusieurs contextes dans lesquels vous pouvez écrire du code qui fonctionne avec une solution DSL :  
  
-   **Commandes personnalisées.** Vous pouvez créer une commande que les utilisateurs peuvent appeler en cliquant sur le diagramme, et qui peut modifier le modèle. Pour plus d’informations, consultez [Comment : ajouter une commande au Menu contextuel](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).  
  
-   **Validation.** Vous pouvez écrire du code qui vérifie que le modèle est dans un état correct. Pour plus d’informations, consultez [Validation dans un langage spécifique à un domaine](../modeling/validation-in-a-domain-specific-language.md).  
  
-   **Substituer le comportement par défaut.** Vous pouvez modifier de nombreux aspects du code qui est généré à partir de DslDefinition.dsl. Pour plus d’informations, consultez [substitution et extension des Classes générées](../modeling/overriding-and-extending-the-generated-classes.md).  
  
-   **Transformation de texte.** Vous pouvez écrire des modèles de texte qui contiennent du code qui accède à un modèle et génère un fichier texte, par exemple générer le code de programme. Pour plus d’informations, consultez [génération du Code à partir d’un langage spécifique à un domaine](../modeling/generating-code-from-a-domain-specific-language.md).  
  
-   **Autres extensions Visual Studio.** Vous pouvez écrire des extensions VSIX distinctes que vous lire et modifier des modèles. Pour plus d’informations, consultez [Comment : ouvrir un modèle depuis un fichier de Code de programme](../modeling/how-to-open-a-model-from-file-in-program-code.md)  
  
 Instances des classes que vous définissez dans DslDefinition.dsl sont conservés dans une structure de données appelée la *In-Memory Store* (IMS) ou *Store*. Les classes que vous définissez dans une solution DSL toujours prennent un Store en tant qu’argument au constructeur. Par exemple, si votre DSL définit une classe appelée exemple :  
  
 `Example element = new Example (theStore);`  
  
 conservation des objets dans le Store (au lieu de simplement comme ordinaires objets) offre plusieurs avantages.  
  
-   **Transactions**. Vous pouvez regrouper une série de modifications connexes dans une transaction :  
  
     `using (Transaction t = store.TransactionManager.BeginTransaction("updates"))`  
  
     `{`  
  
     `// make several changes to Store elements here`  
  
     `t.Commit();`  
  
     `}`  
  
     Si une exception se produit pendant les modifications, afin que le Commit() finale n’est pas effectuée, le Store sera réinitialisé à son état précédent. Cela vous aide à vous assurer que les erreurs ne laissent pas le modèle dans un état incohérent. Pour plus d’informations, consultez [navigation et la mise à jour un modèle dans le Code de programme](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
-   **Les relations binaires**. Si vous définissez une relation entre deux classes, les instances aux deux extrémités ont une propriété qui accède à l’autre extrémité. Les deux extrémités sont toujours synchronisées. Par exemple, si vous définissez une relation à la parenté avec des rôles nommés Parents et enfants, vous pouvez écrire :  
  
     `John.Children.Add(Mary)`  
  
     Désormais, les deux expressions suivantes sont remplies :  
  
     `John.Children.Contains(Mary)`  
  
     `Mary.Parents.Contains(John)`  
  
     Vous pouvez également obtenir le même effet en écrivant :  
  
     `Mary.Parents.Add(John)`  
  
     Pour plus d’informations, consultez [navigation et la mise à jour un modèle dans le Code de programme](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
-   **Règles et événements**. Vous pouvez définir des règles qui se déclenchent à chaque modification de spécifié. Règles sont utilisées, par exemple, pour maintenir à jour avec les éléments de modèle qu’ils présentent les formes sur le diagramme. Pour plus d’informations, consultez [réponse en cours à et propagation des modifications](../modeling/responding-to-and-propagating-changes.md).  
  
-   **Sérialisation**. Le Store est un moyen standard pour sérialiser les objets qu’il contient dans un fichier. Vous pouvez personnaliser les règles pour sérialiser et désérialiser. Pour plus d’informations, consultez [stockage de fichiers de personnalisation et la sérialisation XML](../modeling/customizing-file-storage-and-xml-serialization.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Personnalisation et extension d’un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md)



