---
title: Options, Éditeur de texte, C#, Avancé
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.CSharp.Advanced
helpviewer_keywords:
- XML comments
- XML documentation, generating
- outlining options [C#]
- XML documentation, creating
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: a7675d711a4a1df6af4643a459f49b6ef518e5b4
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31950684"
---
# <a name="options-text-editor-c-advanced"></a>Options, Éditeur de texte, C#, Avancé

Utilisez la page d’options **Avancé** pour modifier les paramètres de mise en forme de l’éditeur, la refactorisation de code et les commentaires sur la documentation XML pour C#. Pour accéder à cette page d’options, choisissez **Outils** > **Options**, puis **Éditeur de texte** > **C#** > **Avancé**.

> [!NOTE]
> Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="analysis"></a>Analyse

- Activer l’analyse complète de la solution

   Active l’analyse du code sur tous les fichiers dans la solution, pas simplement les fichiers de code ouverts. Pour plus d’informations, consultez [Analyse complète de la solution](../../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

- Effectuer l’analyse des fonctionnalités de l’éditeur dans un processus externe (expérimental)

## <a name="using-directives"></a>Directives Using

- Placer les directives « System » en premier lors du tri des usings

- Séparer les groupes de directives using

- Suggérer des usings pour les types dans les assemblys de référence

- Suggérer des usings pour les types dans les packages NuGet

## <a name="highlighting"></a>Highlighting

- Surligner les références jusqu’au symbole sous le curseur

   Quand le curseur est positionné à l’intérieur d’un symbole ou que vous cliquez sur un symbole, toutes les instances de ce symbole dans le fichier de code sont surlignées.

- Mettre en surbrillance les mots clés associés sous le curseur

## <a name="outlining"></a>mode Plan

- Passer en mode Plan à l'ouverture des fichiers

   Quand cette option est sélectionnée, le fichier de code passe automatiquement en mode Plan, ce qui crée des blocs de code réductibles. La première fois qu’un fichier est ouvert, les blocs #regions et les blocs de code inactifs sont réduits.

- Afficher les séparateurs de ligne de procédure

- Afficher le mode Plan pour les constructions au niveau des déclarations

- Afficher le mode Plan pour les constructions au niveau du code

- Afficher le mode Plan pour les commentaires et les régions du préprocesseur

- Réduire #regions lors de la réduction aux définitions

## <a name="fading"></a>Suppression

- Supprimer les instructions using inutilisées

- Supprimer le code inaccessible

## <a name="block-structure-guides"></a>Repères de structure de bloc

- Afficher les repères pour les constructions au niveau des déclarations

- Afficher les repères pour les constructions au niveau du code

## <a name="editor-help"></a>Aide de l'éditeur

- Générer des commentaires de documentation XML pour ///

   Quand cette option est sélectionnée et que vous tapez l’introduction de commentaires `///`, elle insère les éléments XML pour les commentaires de documentation XML. Pour plus d’informations sur la documentation XML, consultez [Commentaires de documentation XML (Guide de programmation C#)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments).

- Insérer \* au début des nouvelles lignes pour l’écriture de commentaires /\* \*/

- Afficher un aperçu pour le suivi des renommages

- Fractionner les littéraux de chaîne avec Entrée

- Signaler les espaces réservés non valides dans les appels de 'string.Format'

## <a name="extract-method"></a>Extraire la méthode

- Ne pas ajouter ref ou out dans un struct personnalisé

## <a name="implement-interface-or-abstract-class"></a>Implémenter une interface ou une classe abstraite

- Quand vous insérez des propriétés, des événements et des méthodes, placez-les : avec d’autres membres du même type ou à la fin

- Durant la génération des propriété : préférer les propriétés de levée d’exceptions ou préférer les propriétés automatiques

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour insérer des commentaires XML pour la génération de documentation](../../ide/reference/generate-xml-documentation-comments.md)
- [Commentaires de documentation XML (Guide de programmation C#)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [Documentation de votre code avec des commentaires XML (Guide C#)](/dotnet/csharp/codedoc)
- [Définition d’options d’éditeur spécifiques au langage](../../ide/reference/setting-language-specific-editor-options.md)
- [C# IntelliSense](../../ide/visual-csharp-intellisense.md)