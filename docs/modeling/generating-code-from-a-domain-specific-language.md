---
title: "G&#233;n&#233;ration de code &#224; partir d&#39;un langage sp&#233;cifique &#224; un domaine | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e3706cc9-2afd-456a-a879-68425a248ebc
caps.latest.revision: 13
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 13
---
# G&#233;n&#233;ration de code &#224; partir d&#39;un langage sp&#233;cifique &#224; un domaine
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Microsoft [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] offre un moyen puissant pour générer le code, des documents, des fichiers de configuration et d'autres artefacts de données représentées dans les modèles.  À l'aide de [!INCLUDE[dsl](../modeling/includes/dsl_md.md)], vous pouvez créer un ensemble de classes qui représente vos données, et vous pouvez écrire vos modèles de texte dans les classes dont les noms et les propriétés reflètent ces données.  
  
 Par exemple, Fabrikam possède un fichier XML des noms de client et les adresses de messagerie.  Leurs développeurs créent un modèle dans lequel le client est une classe, avec le nom et la messagerie électronique de propriétés.  Ils peuvent entrer plusieurs modèles de texte pour traiter les données, y compris ce fragment qui produit un tableau de tous les clients dans le cadre d'une page HTML :  
  
```  
<table>  
<# foreach (Customer c in ContactList) {  #>  
  <tr><td> <#= c.FullName #> </td>   
      <td> <#= c.EmailAddress #> </td> </tr>  
<# } #>  </table>  
```  
  
 Lorsque la base de données client est traitée, le fichier XML est lu dans le magasin de modèles.  *Un processeur de directive*, créé à l'aide de [!INCLUDE[dsl](../modeling/includes/dsl_md.md)], rend la classe cliente disponible au code dans le modèle de texte. De nombreux modèles de texte peuvent être exécutés sur la même magasin.  
  
 les modèles de texte sont essentiels à [!INCLUDE[dsl](../modeling/includes/dsl_md.md)].  Ils sont utilisés pour générer le code source pour les éléments du modèle de domaine et pour le VSPackage et les contrôles qui sont utilisés pour intégrer les outils avec [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Cette section présente certaines des méthodes pour créer, modifier, et déboguer des modèles de texte utilisés dans [!INCLUDE[dsl](../modeling/includes/dsl_md.md)].  
  
## Dans cette section  
 [Accès aux modèles depuis des modèles de texte](../modeling/accessing-models-from-text-templates.md)  
  
 Fournit des informations de base à propos à faire référence au langage spécifique au domaine dans les modèles de texte.  
  
 [Procédure pas à pas : débogage d'un modèle de texte accédant à un modèle](../Topic/Walkthrough:%20Debugging%20a%20Text%20Template%20that%20Accesses%20a%20Model.md)  
  
 Décrit comment effectuer la résolution des problèmes et le débogage sur un modèle de texte qui fait référence à un langage spécifique au domaine.  
  
 [Procédure pas à pas : connexion d'un hôte à un processeur de directive généré](../modeling/walkthrough-connecting-a-host-to-a-generated-directive-processor.md)  
  
 décrit comment connecter un hôte personnalisé à un processeur de directive généré.  
  
 [La commande DslTextTransform](../modeling/the-dsltexttransform-command.md)  
  
 Décrit le fichier de commandes d'exécution du fichier exécutable de TextTransform sur la ligne de commande pour les modèles de texte qui référencent des langages spécifiques.  
  
## Référence  
 [Writing a T4 Text Template](../modeling/writing-a-t4-text-template.md)  
  
 Fournit la syntaxe des blocs de contrôle et des directives de modèle de texte.  
  
## Rubriques connexes  
 [Design\-Time Code Generation by using T4 Text Templates](../modeling/design-time-code-generation-by-using-t4-text-templates.md)  
  
 explique le processus de transformation de modèle de texte.  
  
 [Code Generation in a Build Process](../modeling/code-generation-in-a-build-process.md)  
  
 Lisez cette rubrique si vous générez des fichiers d'un DÉSOLÉ sur un serveur de builds.