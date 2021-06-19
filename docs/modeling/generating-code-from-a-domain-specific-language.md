---
title: Génération de code à partir d'un langage spécifique à un domaine
description: Découvrez comment Domain-Specific Language Tools offre un moyen puissant de générer du code, des documents et d’autres artefacts à partir des données représentées dans les modèles.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6eee4fe2400bac1534bdc9c208fa60d9af8d3cfd
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388839"
---
# <a name="generating-code-from-a-domain-specific-language"></a>Génération de code à partir d'un langage spécifique à un domaine

Microsoft [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] offre un moyen puissant de générer du code, des documents, des fichiers de configuration et d’autres artefacts à partir des données représentées dans les modèles. À l’aide de [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] , vous pouvez créer un ensemble de classes qui représentent vos données, et vous pouvez écrire vos modèles de texte dans des classes dont les noms et les propriétés reflètent ces données.

Par exemple, Fabrikam possède un fichier XML contenant les noms des clients et les adresses de messagerie. Leurs développeurs créent un modèle dans lequel Customer est une classe, avec les propriétés Name et email. Elles écrivent plusieurs modèles de texte pour traiter les données, y compris ce fragment qui produit une table de tous les clients dans le cadre d’une page HTML :

```
<table>
<# foreach (Customer c in ContactList) {  #>
  <tr><td> <#= c.FullName #> </td>
      <td> <#= c.EmailAddress #> </td> </tr>
<# } #>  </table>
```

Lorsque la base de données du client est traitée, le fichier XML est lu dans le magasin de modèles. Un *processeur de directive*, créé à l’aide de [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] , rend la classe Customer disponible pour le code dans le modèle de texte. De nombreux modèles de texte peuvent être exécutés sur le même magasin.

Les modèles de texte sont essentiels à [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] . Ils sont utilisés pour générer le code source des éléments du modèle de domaine, ainsi que pour le VSPackage et les contrôles utilisés pour intégrer les outils à Visual Studio.

Cette section décrit quelques-unes des façons de créer, de modifier et de déboguer des modèles de texte utilisés dans [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] .

## <a name="in-this-section"></a>Dans cette section

[Accès aux modèles à partir de modèles de texte](../modeling/accessing-models-from-text-templates.md)\
Fournit des informations de base sur la référence à un langage spécifique à un domaine dans des modèles de texte.

[Procédure pas à pas : débogage d’un modèle de texte qui accède à un modèle](../modeling/walkthrough-debugging-a-text-template-that-accesses-a-model.md)\
Décrit comment effectuer des procédures de dépannage et de débogage sur un modèle de texte qui fait référence à un langage spécifique à un domaine.

[Procédure pas à pas : connexion d’un hôte à un processeur de directive généré](../modeling/walkthrough-connecting-a-host-to-a-generated-directive-processor.md)\
Décrit comment connecter un hôte personnalisé à un processeur de directive généré.

[Commande DslTextTransform](../modeling/the-dsltexttransform-command.md)\
Décrit le fichier de commandes qui exécute l’exécutable TextTransform sur la ligne de commande pour les modèles de texte qui font référence à des langages spécifiques à un domaine.

## <a name="reference"></a>Informations de référence

[Écriture d’un modèle de texte T4](../modeling/writing-a-t4-text-template.md)\
Fournit la syntaxe des directives de modèle de texte et des blocs de contrôle.

## <a name="related-sections"></a>Sections connexes

[Génération de code au moment du design à l’aide de modèles de texte T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)\
Explique le processus de transformation du modèle de texte.

[Génération de code dans un processus de génération](../modeling/code-generation-in-a-build-process.md)\
Lisez cette rubrique si vous générez des fichiers à partir d’un DSL sur un serveur de builds.
