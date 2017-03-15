---
title: "&#201;crire du Code pour personnaliser un langage sp&#233;cifique &#224; un domaine | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Domain-Specific Language, programmation"
ms.assetid: a4a17f5b-9c97-4575-b2d1-3182c1896b72
caps.latest.revision: 29
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 29
---
# &#201;crire du Code pour personnaliser un langage sp&#233;cifique &#224; un domaine
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette section indique comment utiliser le code personnalisé pour accéder, modifier, ou la création d'un modèle dans un langage spécifique au domaine.  
  
 Il existe plusieurs contextes dans lesquels vous pouvez écrire du code qui fonctionne avec un DÉSOLÉ :  
  
-   **commandes personnalisées.** vous pouvez créer une commande que les utilisateurs peuvent appeler en cliquant avec le bouton droit sur le diagramme, et qui peut modifier le modèle.  Pour plus d'informations, consultez [Comment : ajouter une commande au menu contextuel](../Topic/How%20to:%20Add%20a%20Command%20to%20the%20Shortcut%20Menu.md).  
  
-   **validation.** Vous pouvez écrire du code qui vérifie que le modèle est dans un état correct.  Pour plus d'informations, consultez [Validation dans un langage spécifique à un domaine](../modeling/validation-in-a-domain-specific-language.md).  
  
-   **substituer le comportement par défaut.** Vous pouvez modifier de nombreux aspects de code généré à partir de DslDefinition.dsl.  Pour plus d'informations, consultez [Substitution et extension des classes générées](../modeling/overriding-and-extending-the-generated-classes.md).  
  
-   **Transformation de texte.** Vous pouvez créer des modèles de texte qui contiennent du code qui accède à un modèle et génère un fichier texte, par exemple pour générer du code de programme.  Pour plus d'informations, consultez [Génération de code à partir d'un langage spécifique à un domaine](../modeling/generating-code-from-a-domain-specific-language.md).  
  
-   **D'autres extensions Visual Studio.** Vous pouvez écrire des extensions distinctes VSIX qui lisent et modifier des modèles.  Pour plus d'informations, consultez [Comment : ouvrir un modèle depuis un fichier dans le code de programme](../modeling/how-to-open-a-model-from-file-in-program-code.md).  
  
 Des instances de classes que vous définissez dans DslDefinition.dsl sont conservées dans une structure de données appelée *magasin \(IMS\)* en mémoire ou le magasin *.* Les classes que vous définissez dans un domaine \(prennent toujours un magasin en tant qu'argument au constructeur.  Par exemple, si votre DÉSOLÉ définit une classe appelée Example :  
  
 `Example element = new Example (theStore);`  
  
 conserver des objets dans le magasin \(au lieu de simplement en tant qu'objets ordinaires\) offre plusieurs avantages.  
  
-   **Transactions**.  Vous pouvez regrouper une série de modifications associées dans une transaction :  
  
     `using (Transaction t = store.TransactionManager.BeginTransaction("updates"))`  
  
     `{`  
  
     `// make several changes to Store elements here`  
  
     `t.Commit();`  
  
     `}`  
  
     Si une exception se produit pendant les modifications, afin que Commit\(\) final ne soit pas effectué, le magasin sera réinitialisée à son état précédent.  Cela vous permet de garantir que les erreurs laisser le modèle dans un état incohérent.  Pour plus d'informations, consultez [Navigation et mise à jour d'un modèle dans le code de programme](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
-   **relations binaires**.  Si vous définissez une relation entre deux classes, les instances aux deux extrémités ont une propriété qui accède à l'autre extrémité.  les deux extrémités sont toujours synchronisées.  Par exemple, si vous définissez une relation de condition parentale avec des rôles nommés Parents et enfants, vous pouvez écrire :  
  
     `John.Children.Add(Mary)`  
  
     Les deux expressions suivantes sont maintenant remplies :  
  
     `John.Children.Contains(Mary)`  
  
     `Mary.Parents.Contains(John)`  
  
     Vous pouvez également obtenir le même effet en écrivant :  
  
     `Mary.Parents.Add(John)`  
  
     Pour plus d'informations, consultez [Navigation et mise à jour d'un modèle dans le code de programme](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
-   **règles et événements**.  Vous pouvez définir des règles qui déclenchent chaque fois que des modifications spécifiées sont apportées.  Les règles sont utilisées, par exemple, pour contenir des formes du diagramme à jour avec les éléments de modèle qu'elles présentent.  Pour plus d'informations, consultez [Propagation et réponse aux modifications en attente](../modeling/responding-to-and-propagating-changes.md).  
  
-   **sérialisation**.  Le magasin fournit une méthode standard pour sérialiser les objets qu'il contient dans un fichier.  Vous pouvez personnaliser les règles à la sérialisation et la désérialisation.  Pour plus d'informations, consultez [Personnalisation du stockage de fichiers et de la sérialisation XML](../modeling/customizing-file-storage-and-xml-serialization.md).  
  
## Voir aussi  
 [Personnalisation et extension d'un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md)