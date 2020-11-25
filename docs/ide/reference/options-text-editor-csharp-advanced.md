---
title: Options, Éditeur de texte, C#, Avancé
description: Découvrez comment utiliser la page avancé de la section C# pour modifier les paramètres de mise en forme de l’éditeur, la refactorisation du code et les commentaires de documentation XML pour C#.
ms.custom: SEO-VS-2020
ms.date: 11/13/2020
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.CSharp.Advanced
author: akhera99
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 6e8c235c62eeba394902698ecbfc412ed37b0979
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96039890"
---
# <a name="options-text-editor-c-advanced"></a>Options, Éditeur de texte, C#, Avancé

Utilisez la page d’options **Avancé** pour modifier les paramètres de mise en forme de l’éditeur, la refactorisation de code et les commentaires sur la documentation XML pour C#. Pour accéder à cette page d’options, choisissez **Outils**  >  **options**, puis **éditeur de texte**  >  **C#**  >  **avancé**.

> [!NOTE]
> Toutes les options peuvent ne pas être répertoriées ici.

## <a name="analysis"></a>Analyse

- Analyse du code en temps réel ou étendue de l’analyse en arrière-plan

   Configurez l’étendue de l’analyse en arrière-plan pour le code managé. Pour plus d’informations, consultez [Comment : configurer l’étendue de l’analyse du code en temps réel pour le code managé](../../code-quality/configure-live-code-analysis-scope-managed-code.md).

## <a name="using-directives"></a>Directives Using

- Placer les directives « System » en premier lors du tri des usings

   Lorsque cette option est sélectionnée, la commande **supprimer et trier** les instructions using du menu contextuel trie les `using` directives et place les espaces de noms « System » en haut de la liste.

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

::: moniker range=">=vs-2019"                                              
- Suggérer des usings pour les types dans les assemblys .NET Framework
::: moniker-end
                                         
::: moniker range="vs-2017"                                                
- Suggérer des usings pour les types dans les assemblys de référence
::: moniker-end                                                            

- Suggérer des usings pour les types dans les packages NuGet

   Quand ces options sont sélectionnées, une [Action rapide](../quick-actions.md) est disponible pour installer un package NuGet et ajouter une directive `using` pour les types non référencés.

   ![Action rapide pour installer un package NuGet dans Visual Studio](media/nuget-lightbulb.png)

## <a name="highlighting"></a>Mettre en surbrillance

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

Activez ces cases à cocher pour afficher les lignes verticales en pointillés entre les accolades ( **{}** ) dans votre code. Cela vous permet de voir facilement les blocs de code pour vos constructions au niveau des déclarations et au niveau du code.

## <a name="editor-help"></a>Aide de l'éditeur
::: moniker range=">=vs-2019"
- Indicateurs de nom de paramètre Inline 
    
    Lorsque cette option est sélectionnée, les indicateurs de nom de paramètre sont insérés pour les littéraux, les littéraux castés et les instanciations d’objets avant chaque argument dans les appels de fonction.  
    
    ![Indicateurs de nom de paramètre Inline pour CSharp](media/inline-parameter-name-hints-csharp.png)

- Indicateurs de type Inline 
    
    Quand cette option est sélectionnée, les indicateurs de type sont insérés pour les variables avec des types inférés et des types de paramètres lambda.  
    
    ![Indicateurs de type inline pour CSharp](media/inline-type-hints-csharp.png)
::: moniker-end
- Générer des commentaires de documentation XML pour ///

   Quand cette option est sélectionnée et que vous tapez l’introduction de commentaires `///`, elle insère les éléments XML pour les commentaires de documentation XML. Pour plus d’informations sur la documentation XML, consultez [Commentaires de documentation XML (Guide de programmation C#)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments).

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour insérer des commentaires XML pour la génération de documentation](../../ide/reference/generate-xml-documentation-comments.md)
- [Commentaires de documentation XML (Guide de programmation C#)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [Documenter votre code avec des commentaires XML (Guide C#)](/dotnet/csharp/codedoc)
- [Définir les options d’éditeur spécifiques au langage](../../ide/reference/setting-language-specific-editor-options.md)
- [C# IntelliSense](../../ide/visual-csharp-intellisense.md)
