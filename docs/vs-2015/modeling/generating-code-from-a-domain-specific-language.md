---
title: Génération de code à partir d’un langage spécifique à un domaine | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: e3706cc9-2afd-456a-a879-68425a248ebc
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 32cafb9e68fc2535ed3b570022a59d284f4c4cae
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666112"
---
# <a name="generating-code-from-a-domain-specific-language"></a>Génération de code à partir d'un langage spécifique à un domaine
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Microsoft [!INCLUDE[dsl](../includes/dsl-md.md)] offre un moyen puissant de générer du code, des documents, des fichiers de configuration et d’autres artefacts à partir des données représentées dans les modèles. À l’aide de [!INCLUDE[dsl](../includes/dsl-md.md)], vous pouvez créer un ensemble de classes qui représentent vos données, et vous pouvez écrire vos modèles de texte dans des classes dont les noms et les propriétés reflètent ces données.

 Par exemple, Fabrikam possède un fichier XML contenant les noms des clients et les adresses de messagerie. Leurs développeurs créent un modèle dans lequel Customer est une classe, avec les propriétés Name et email. Elles écrivent plusieurs modèles de texte pour traiter les données, y compris ce fragment qui produit une table de tous les clients dans le cadre d’une page HTML :

```
<table>
<# foreach (Customer c in ContactList) {  #>
  <tr><td> <#= c.FullName #> </td>
      <td> <#= c.EmailAddress #> </td> </tr>
<# } #>  </table>
```

 Lorsque la base de données du client est traitée, le fichier XML est lu dans le magasin de modèles. Un *processeur de directive*, créé à l’aide de [!INCLUDE[dsl](../includes/dsl-md.md)], rend la classe Customer disponible pour le code dans le modèle de texte. De nombreux modèles de texte peuvent être exécutés sur le même magasin.

 Les modèles de texte sont essentiels pour [!INCLUDE[dsl](../includes/dsl-md.md)]. Ils sont utilisés pour générer le code source pour les éléments du modèle de domaine, ainsi que pour le VSPackage et les contrôles utilisés pour intégrer les outils avec [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

 Cette section décrit quelques-unes des façons de créer, de modifier et de déboguer des modèles de texte utilisés dans [!INCLUDE[dsl](../includes/dsl-md.md)].

## <a name="in-this-section"></a>Dans cette section
 [Accès aux modèles depuis des modèles de texte](../modeling/accessing-models-from-text-templates.md)

 Fournit des informations de base sur la référence à un langage spécifique à un domaine dans des modèles de texte.

 [Procédure pas à pas : débogage d’un modèle de texte accédant à un modèle](../modeling/walkthrough-debugging-a-text-template-that-accesses-a-model.md)

 Décrit comment effectuer des procédures de dépannage et de débogage sur un modèle de texte qui fait référence à un langage spécifique à un domaine.

 [Procédure pas à pas : connexion d’un hôte à un processeur de directives généré](../modeling/walkthrough-connecting-a-host-to-a-generated-directive-processor.md)

 Décrit comment connecter un hôte personnalisé à un processeur de directive généré.

 [DslTextTransform, commande](../modeling/the-dsltexttransform-command.md)

 Décrit le fichier de commandes qui exécute l’exécutable TextTransform sur la ligne de commande pour les modèles de texte qui font référence à des langages spécifiques à un domaine.

## <a name="reference"></a>Reference
 [Écriture d’un modèle de texte T4](../modeling/writing-a-t4-text-template.md)

 Fournit la syntaxe des directives de modèle de texte et des blocs de contrôle.

## <a name="related-sections"></a>Rubriques connexes
 [Génération de code au moment du design à l’aide de modèles de texte T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)

 Explique le processus de transformation du modèle de texte.

 [Génération de code dans un processus de génération](../modeling/code-generation-in-a-build-process.md)

 Lisez cette rubrique si vous générez des fichiers à partir d’un DSL sur un serveur de builds.
