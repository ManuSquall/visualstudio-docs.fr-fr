---
title: "Génération de Code à partir d’un langage spécifique à un domaine | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e3706cc9-2afd-456a-a879-68425a248ebc
caps.latest.revision: "13"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 98811cc3e7830dfcbf548bc34c5b3ee268e6f858
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="generating-code-from-a-domain-specific-language"></a>Génération de code à partir d'un langage spécifique à un domaine
Microsoft [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] offre un moyen puissant pour générer du code, les documents, les fichiers de configuration et les autres artefacts à partir des données représentées dans les modèles. À l’aide de [!INCLUDE[dsl](../modeling/includes/dsl_md.md)], vous pouvez créer un ensemble de classes qui représentent des données et vous pouvez écrire vos modèles de texte dans les classes dont les noms et propriétés reflètent ces données.  
  
 Par exemple, Fabrikam a un fichier XML de noms de clients et les adresses de messagerie. Les développeurs de créer un modèle dans lequel le client est une classe, avec le nom de propriété et de courrier électronique. Écriture de plusieurs modèles de texte pour traiter les données, y compris ce fragment qui génère une table de tous les clients dans le cadre d’une page HTML :  
  
```  
<table>  
<# foreach (Customer c in ContactList) {  #>  
  <tr><td> <#= c.FullName #> </td>   
      <td> <#= c.EmailAddress #> </td> </tr>  
<# } #>  </table>  
```  
  
 Lors du traitement de la base de données client, le fichier XML est lu dans le magasin de modèles. A *processeur de directive*, créé à l’aide de [!INCLUDE[dsl](../modeling/includes/dsl_md.md)], rend la classe de client disponibles pour le code dans le modèle de texte. De nombreux modèles de texte peuvent être exécutés sur le même magasin.  
  
 Modèles de texte sont essentiels pour [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]. Ils sont utilisés pour générer le code source pour les éléments du modèle de domaine, ainsi que pour le VSPackage et les contrôles qui sont utilisées pour intégrer les outils avec [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Cette section présente certaines des méthodes pour créer, modifier et déboguer des modèles de texte utilisés dans [!INCLUDE[dsl](../modeling/includes/dsl_md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
 [Accès aux modèles depuis des modèles de texte](../modeling/accessing-models-from-text-templates.md)  
  
 Fournit des informations de base sur la référence à un langage spécifique à un domaine dans les modèles de texte.  
  
 [Procédure pas à pas : débogage d’un modèle de texte accédant à un modèle](../modeling/walkthrough-debugging-a-text-template-that-accesses-a-model.md)  
  
 Décrit comment effectuer la résolution des problèmes et de débogage sur un modèle de texte qui fait référence à un langage spécifique à un domaine.  
  
 [Procédure pas à pas : connexion d’un hôte à un processeur de directives généré](../modeling/walkthrough-connecting-a-host-to-a-generated-directive-processor.md)  
  
 Décrit comment se connecter à un hôte personnalisé pour un processeur de directive généré.  
  
 [DslTextTransform, commande](../modeling/the-dsltexttransform-command.md)  
  
 Décrit le fichier de commandes qui s’exécute l’exécutable TextTransform sur la ligne de commande pour les modèles de texte qui référencent des langages spécifiques à un domaine.  
  
## <a name="reference"></a>Référence  
 [Écriture d’un modèle de texte T4](../modeling/writing-a-t4-text-template.md)  
  
 Fournit la syntaxe des directives de modèle de texte et les blocs de contrôle.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Génération de code au moment du design à l’aide de modèles de texte T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)  
  
 Explique le processus de transformation de modèle de texte.  
  
 [Génération de code dans un processus de génération](../modeling/code-generation-in-a-build-process.md)  
  
 Lisez cette rubrique si vous générez des fichiers à partir d’une DSL sur un serveur de builds.