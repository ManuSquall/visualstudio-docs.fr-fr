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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4c8b957517a7b539f74a9715b92b8a2945d3fe5c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441374"
---
# <a name="options-text-editor-c-advanced"></a>Options, Éditeur de texte, C#, Avancé
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Utilisez cette boîte de dialogue pour modifier les paramètres de mise en forme de l’éditeur, la refactorisation de code et les commentaires sur la documentation XML pour Visual C#. Pour accéder à cette boîte de dialogue, dans le menu **Outils**, cliquez sur **Options**, développez le dossier **Éditeur de texte**, développez **C#**, puis cliquez sur **Avancé**.  
  
> [!NOTE]
> Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="outlining"></a>Mode Plan  
 Passer en mode Plan à l'ouverture des fichiers  
 Quand cette option est sélectionnée, le fichier de code passe automatiquement en mode Plan, ce qui crée des blocs de code réductibles. La première fois qu’un fichier est ouvert, les blocs #regions et les blocs de code inactifs sont réduits.  
  
## <a name="editor-help"></a>Aide de l'éditeur  
 Souligner les erreurs dans l’éditeur  
 Identifie les erreurs de build dans le code. Quand cette option est sélectionnée, des soulignements ondulés s’affichent dans des couleurs qui ont une signification particulière :  
  
- Les erreurs d’analyse apparaissent en rouge.  
  
- Les erreurs de build apparaissent en bleu.  
  
- Les avertissements de génération apparaissent en vert.  
  
- Les modifications [Modifier & Continuer](../../debugger/edit-and-continue.md) non valides apparaissent en violet.  
  
  Déplacez le pointeur sur le segment de code souligné pour afficher une info-bulle contenant des informations sur l’erreur.  
  
  Afficher les erreurs sémantiques en direct  
  Identifie certaines erreurs de compilation sans compilation explicite, par exemple, la déclaration et l’utilisation d’un type inconnu ou le référencement d’une propriété inconnue.  
  
  Surligner les références jusqu’au symbole sous le curseur  
  Quand le curseur est positionné à l’intérieur d’un symbole ou que vous cliquez sur un symbole, toutes les instances de ce symbole dans le fichier de code sont surlignées.  
  
## <a name="refactoring"></a>Refactorisation  
 Vérifier les résultats de la réorganisation  
 Affiche la boîte de dialogue **Résultats de la vérification** quand vous essayez de refactoriser du code qui contient des erreurs de build ou si, sous l’effet de la refactorisation, une référence de code pourrait être liée à toute autre chose.  
  
 Avertir en cas de membres avec des références du compilateur  
 Affiche une boîte de dialogue d’avertissement si vous essayez de refactoriser un membre qui a le même nom qu’une référence générée par le compilateur.  
  
## <a name="xml-documentation-comments"></a>Commentaires de documentation XML  
 Générer des commentaires de documentation XML pour ///  
 Quand cette option est sélectionnée et que vous tapez l’introduction de commentaires ///, elle insère automatiquement les balises de début et de fin \<summary> pour les commentaires sur la documentation XML. Pour plus d’informations sur la documentation XML, consultez [Commentaires sur la documentation XML](http://msdn.microsoft.com/library/803b7f7b-7428-4725-b5db-9a6cff273199).  
  
## <a name="implement-interface"></a>Implémenter l'interface  
 Entourer le code généré avec #region  
 Insère un membre #region \<*nom de l’interface*> autour des méthodes quand Implémenter l’interface ou Implémenter l’interface explicitement est utilisée.  
  
## <a name="organize-usings"></a>Organiser les instructions Using  
 Placer les directives « System » en premier lors du tri des usings  
 Quand cette option est sélectionnée, des directives using `System` apparaissent avant les autres directives using. Pour plus d’informations, consultez [Trier les instructions Using](../../misc/sort-usings.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Commentaires sur la documentation XML](http://msdn.microsoft.com/library/803b7f7b-7428-4725-b5db-9a6cff273199)   
 [Définition d’options d’éditeur spécifiques du langage](../../ide/reference/setting-language-specific-editor-options.md)   
 [Visual C# IntelliSense](../../ide/visual-csharp-intellisense.md)
