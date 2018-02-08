---
title: "Options, Éditeur de texte, C#, Avancé │ Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Advanced
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.CSharp.Advanced
helpviewer_keywords:
- XML comments
- XML documentation, generating
- outlining options [C#]
- XML documentation, creating
ms.assetid: 947f9d9a-b0f3-408d-9866-d82895bcee31
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 193b61ab95daa84c5815c251c7d52103c88977e1
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2018
---
# <a name="options-text-editor-c-advanced"></a>Options, Éditeur de texte, C#, Avancé
Utilisez cette boîte de dialogue pour modifier les paramètres de mise en forme de l’éditeur, la refactorisation de code et les commentaires sur la documentation XML pour C#. Pour accéder à cette boîte de dialogue, dans le menu **Outils**, cliquez sur **Options**, développez le dossier **Éditeur de texte**, développez **C#**, puis cliquez sur **Avancé**.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="outlining"></a>mode Plan  
 Passer en mode Plan à l'ouverture des fichiers  
 Quand cette option est sélectionnée, le fichier de code passe automatiquement en mode Plan, ce qui crée des blocs de code réductibles. La première fois qu’un fichier est ouvert, les blocs #regions et les blocs de code inactifs sont réduits.  
  
## <a name="editor-help"></a>Aide de l'éditeur  
 Souligner les erreurs dans l’éditeur  
 Identifie les erreurs de build dans le code. Quand cette option est sélectionnée, des soulignements ondulés s’affichent dans des couleurs qui ont une signification particulière :  
  
-   Les erreurs d’analyse apparaissent en rouge.  
  
-   Les erreurs de build apparaissent en bleu.  
  
-   Les avertissements de génération apparaissent en vert.  
  
-   Les modifications [Modifier & Continuer](../../debugger/edit-and-continue.md) non valides apparaissent en violet.  
  
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
 Quand cette option est sélectionnée et que vous tapez l’introduction de commentaires ///, elle insère automatiquement les balises de début et de fin \<summary> pour les commentaires sur la documentation XML. Pour plus d’informations sur la documentation XML, consultez [Commentaires sur la documentation XML](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments).  
  
## <a name="implement-interface"></a>Implémenter l'interface  
 Entourer le code généré avec #region  
 Insère un membre #region \<*nom de l’interface*> autour des méthodes quand Implémenter l’interface ou Implémenter l’interface explicitement est utilisée.  
  
## <a name="organize-usings"></a>Organiser les instructions Using  
 Placer les directives « System » en premier lors du tri des usings  
 Quand cette option est sélectionnée, des directives using `System` apparaissent avant les autres directives using. Pour plus d’informations, consultez Organiser les instructions Using dans [C# IntelliSense](../../ide/visual-csharp-intellisense.md#automatic-code-generation).  
  
## <a name="see-also"></a>Voir aussi  
 [Commentaires sur la documentation XML](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)   
 [Définition d’options d’éditeur spécifiques du langage](../../ide/reference/setting-language-specific-editor-options.md)   
 [C# IntelliSense](../../ide/visual-csharp-intellisense.md)