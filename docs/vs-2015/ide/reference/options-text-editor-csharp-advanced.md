---
title: Options, Éditeur de texte, C#, Avancé │ Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Advanced
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.CSharp.Advanced
helpviewer_keywords:
- XML comments
- XML documentation, generating
- outlining options [C#]
- outlining options [J#]
- XML documentation, creating
ms.assetid: 947f9d9a-b0f3-408d-9866-d82895bcee31
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4f2d11e78c2402a6541bc87748ed6ba348ba80fc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662318"
---
# <a name="options-text-editor-c-advanced"></a>Options, Éditeur de texte, C#, Avancé
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Utilisez cette boîte de dialogue pour modifier les paramètres de mise en forme de l’éditeur, la refactorisation de code et les commentaires sur la documentation XML pour Visual C#. Pour accéder à cette boîte de dialogue, dans le menu **Outils**, cliquez sur **Options**, développez le dossier **Éditeur de texte**, développez **C#** , puis cliquez sur **Avancé**.

> [!NOTE]
> Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="outlining"></a>mode Plan
 Passer en mode plan lorsque les fichiers s’ouvrent lorsqu’ils sont sélectionnés, il présente automatiquement le fichier de code, qui crée des blocs de code réductibles. La première fois qu’un fichier est ouvert, les blocs #regions et les blocs de code inactifs sont réduits.

## <a name="editor-help"></a>Aide de l'éditeur
 Les erreurs de soulignement dans l’éditeur identifient les erreurs de build dans le code. Quand cette option est sélectionnée, des soulignements ondulés s’affichent dans des couleurs qui ont une signification particulière :

- Les erreurs d’analyse apparaissent en rouge.

- Les erreurs de build apparaissent en bleu.

- Les avertissements de génération apparaissent en vert.

- Les modifications [Modifier & Continuer](../../debugger/edit-and-continue.md) non valides apparaissent en violet.

  Déplacez le pointeur sur le segment de code souligné pour afficher une info-bulle contenant des informations sur l’erreur.

  Afficher les erreurs sémantiques dynamiques identifie certaines erreurs de compilation sans compilation explicite, par exemple, la déclaration et l’utilisation d’un type inconnu ou la référence à une propriété inconnue.

  Mettre en surbrillance les références au symbole sous le curseur lorsque le curseur est positionné à l’intérieur d’un symbole ou lorsque vous cliquez sur un symbole, toutes les instances de ce symbole dans le fichier de code sont mises en surbrillance.

## <a name="refactoring"></a>Refactorisation
 Vérifier les résultats de la refactorisation affiche la boîte de dialogue résultats de la **vérification** lorsque vous essayez de refactoriser du code qui contient des erreurs de build, ou lorsque la refactorisation entraîne la liaison d’une référence de code à un autre nom que sa liaison d’origine.

 Avertir des membres avec des références générées par le compilateur affiche une boîte de dialogue d’avertissement lorsque vous essayez de refactoriser un membre qui porte le même nom qu’une référence générée par le compilateur.

## <a name="xml-documentation-comments"></a>Commentaires de documentation XML
 Générer des commentaires de documentation XML pour///lorsque cette option est sélectionnée, insère le \<summary > balises de début et de fin automatiquement pour les commentaires de documentation XML après que vous avez tapé l’introduction de commentaire///. Pour plus d’informations sur la documentation XML, consultez [Commentaires sur la documentation XML](https://msdn.microsoft.com/library/803b7f7b-7428-4725-b5db-9a6cff273199).

## <a name="implement-interface"></a>Implémenter l'interface
 Entourer le code généré avec #region insère un #region \< nom de l'*interface*> membre autour des méthodes lorsque l’implémentation de l’interface ou l’implémentation explicite de l’interface est utilisée.

## <a name="organize-usings"></a>Organiser les instructions Using
 Placez d’abord les directives’System’lors du tri à l’aide de lorsque vous sélectionnez cette option, `System` directives using apparaissent avant les autres directives using. Pour plus d’informations, consultez [Trier les instructions Using](../../misc/sort-usings.md).

## <a name="see-also"></a>Voir aussi
 [Commentaires de documentation XML](https://msdn.microsoft.com/library/803b7f7b-7428-4725-b5db-9a6cff273199) [définition d’options d’éditeur spécifiques au langage](../../ide/reference/setting-language-specific-editor-options.md) [Visual C# IntelliSense](../../ide/visual-csharp-intellisense.md)
