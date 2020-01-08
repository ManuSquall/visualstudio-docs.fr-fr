---
title: Options, Éditeur de texte, C#, Avancé
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.CSharp.Advanced
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: c2f4c01a627fb2cd1b581331dd086e2d783d475f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596227"
---
# <a name="options-text-editor-c-advanced"></a>Options, Éditeur de texte, C#, Avancé

Utilisez la page d’options **Avancé** pour modifier les paramètres de mise en forme de l’éditeur, la refactorisation de code et les commentaires sur la documentation XML pour C#. Pour accéder à cette page d’options, choisissez **Outils** > **Options**, puis **Éditeur de texte** > **C#**  > **Avancé**.

> [!NOTE]
> Toutes les options peuvent ne pas être répertoriées ici.

## <a name="analysis"></a>Analyse

- Activer l’analyse complète de la solution

   Active l’analyse du code sur tous les fichiers dans la solution, pas simplement les fichiers de code ouverts. Pour plus d’informations, consultez [Analyse complète de la solution](../../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

## <a name="using-directives"></a>Directives Using

- Placer les directives « System » en premier lors du tri des usings

   Quand elle est sélectionnée, la commande **Supprimer et trier les instructions using** du menu contextuel trie les directives `using` et place les espaces de noms « System » en haut de la liste.

   Avant le tri :

   ```csharp
   using AutoMapper;
   using FluentValidation;
   using System.Collections.Generic;
   using System.Linq;
   using Newtonsoft.Json;
   using System;
   ```

   Après le tri :

   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Linq;
   using AutoMapper;
   using FluentValidation;
   using Newtonsoft.Json;
   ```

- Séparer les groupes de directives using

   La commande **Supprimer et trier les instructions using** du menu contextuel sépare les directives `using` en insérant une ligne vide entre les groupes de directives qui ont le même espace de noms racine.

   Avant le tri :

   ```csharp
   using AutoMapper;
   using FluentValidation;
   using System.Collections.Generic;
   using System.Linq;
   using Newtonsoft.Json;
   using System;
   ```

   Après le tri :

   ```csharp
   using AutoMapper;

   using FluentValidation;

   using Newtonsoft.Json;

   using System;
   using System.Collections.Generic;
   using System.Linq;
   ```

- Suggérer des usings pour les types dans les assemblys de référence
- Suggérer des usings pour les types dans les packages NuGet

   Quand ces options sont sélectionnées, une [Action rapide](../quick-actions.md) est disponible pour installer un package NuGet et ajouter une directive `using` pour les types non référencés.

   ![Action rapide pour installer un package NuGet dans Visual Studio](media/nuget-lightbulb.png)

## <a name="highlighting"></a>Highlighting

- Surligner les références jusqu’au symbole sous le curseur

   Quand le curseur est positionné à l’intérieur d’un symbole ou que vous cliquez sur un symbole, toutes les instances de ce symbole dans le fichier de code sont surlignées.

## <a name="outlining"></a>mode Plan

- Passer en mode Plan à l'ouverture des fichiers

   Quand cette option est sélectionnée, le fichier de code passe automatiquement en mode Plan, ce qui crée des blocs de code réductibles. La première fois qu’un fichier est ouvert, les blocs #regions et les blocs de code inactifs sont réduits.

- Afficher les séparateurs de ligne de procédure

   L’éditeur de texte indique la portée visuelle des procédures. Une ligne est tracée dans les fichiers sources *.cs* de votre projet, aux emplacements présentés dans le tableau suivant :

   |Emplacement dans le fichier source .cs|Exemple d’emplacement de la ligne|
   |---------------------------------|------------------------------|
   |Après la fermeture d’une construction de déclaration de bloc|-   À la fin d’une classe, d’une structure, d’un module, d’une interface ou d’un enum<br />-   Après une propriété, une fonction ou un sub<br />-   Pas entre les clauses get et set d’une propriété|
   |Après un ensemble de constructions de lignes uniques|-   Après les instructions import, avant une définition de type dans un fichier de classe<br />-   Après les variables déclarées dans une classe, avant toute procédure|
   |Après les déclarations de lignes uniques (déclarations pas au niveau des blocs)|-   À la suite des instructions import et inherits, des déclarations de variables, des déclarations event et delegate, et des instructions declare de DLL|

## <a name="block-structure-guides"></a>Repères de structure de bloc

Cochez ces cases pour afficher des lignes verticales en pointillés entre accolades ( **{}** ) dans votre code. Cela vous permet de voir facilement les blocs de code pour vos constructions au niveau des déclarations et au niveau du code.

## <a name="editor-help"></a>Aide de l'éditeur

- Générer des commentaires de documentation XML pour ///

   Quand cette option est sélectionnée et que vous tapez l’introduction de commentaires `///`, elle insère les éléments XML pour les commentaires de documentation XML. Pour plus d’informations sur la documentation XML, consultez [Commentaires de documentation XML (Guide de programmation C#)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments).

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour insérer des commentaires XML pour la génération de documentation](../../ide/reference/generate-xml-documentation-comments.md)
- [Commentaires de documentation XML (Guide de programmation C#)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [Documenter votre code avec des commentaires XML (Guide C#)](/dotnet/csharp/codedoc)
- [Définir les options d’éditeur spécifiques au langage](../../ide/reference/setting-language-specific-editor-options.md)
- [C# IntelliSense](../../ide/visual-csharp-intellisense.md)
