---
title: Extraits de code C# | Microsoft Docs
ms.custom: 
ms.date: 06/05/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- snippets [C#]
- code snippets [C#]
- Code Snippet Inserter [C#]
- C#, code snippets
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 0328ceb6c1420b038ca424c42dd408e36da6f891
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="c-code-snippets"></a>Extraits de code C#

Les extraits de code sont des extraits prêts à l’emploi que vous pouvez rapidement insérer dans votre code. Par exemple, l’extrait de code `for` crée une boucle `for` vide. Certains extraits de code sont des extraits « Entourer de ». Il vous permettent de sélectionner des lignes de code, puis de choisir un extrait de code qui incorpore les lignes sélectionnées. Par exemple, quand vous sélectionnez des lignes de code et que vous activez l’extrait de code `for`, cela crée une boucle `for` avec ces lignes de code dans le bloc de boucle. Les extraits de code peuvent accélérer, simplifier et fiabiliser l’écriture de code de programme.

 Vous pouvez insérer un extrait de code à l’emplacement du curseur, ou insérer un extrait de code « Entourer de » autour du code actuellement sélectionné. L’outil d’insertion d’extraits de code est appelé par le biais de la commande **Insérer un extrait de code** ou **Entourer de** du menu **IntelliSense**, ou à l’aide des raccourcis clavier **Ctrl**+**K**,**X** ou **Ctrl**+**K**,**S** (respectivement).

 L’outil d’insertion d’extraits de code affiche le nom de l’extrait de code pour tous les extraits de code disponibles. Il inclut également une boîte de dialogue d’entrée où vous pouvez taper le nom de l’extrait de code, ou une partie du nom. Il met en évidence la correspondance la plus proche avec un nom d’extrait de code. Une pression sur la touche **Tab** fait disparaître l’outil d’insertion d’extraits de code et insère l’extrait de code sélectionné. Une pression sur la touche **Échap** ou un clic sur le bouton de la souris dans l’Éditeur de code fait disparaître l’outil d’insertion d’extraits de code sans insérer d’extrait de code.

## <a name="default-code-snippets"></a>Extraits de code par défaut

Par défaut, les extraits de code suivants sont inclus dans Visual Studio pour C#.

|Nom (ou raccourci)|Description|Emplacements valides où insérer l’extrait de code|
|--------------------------|-----------------|---------------------------------------|
|#if|Crée une directive [#if](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-if) et une directive [#endif](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-endif).|N’importe où.|
|#region|Crée une directive [#region](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-region) et une directive [#endregion](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-endregion).|N’importe où.|
|~|Crée un [finaliseur](/dotnet/csharp/programming-guide/classes-and-structs/destructors) (destructeur) pour la classe conteneur.|Dans une classe.|
|Attribut|Crée une déclaration pour une classe qui dérive de <xref:System.Attribute>.|Dans un espace de noms (notamment l’espace de noms global), une classe ou un struct.|
|checked|Crée un bloc [checked](/dotnet/csharp/language-reference/keywords/checked).|Dans une méthode, un indexeur, un accesseur de propriété ou un accesseur d’événement.|
|class|Crée une déclaration de classe.|Dans un espace de noms (notamment l’espace de noms global), une classe ou un struct.|
|ctor|Crée un constructeur pour la classe conteneur.|Dans une classe.|
|cw|Crée un appel à <xref:System.Console.WriteLine%2A>.|Dans une méthode, un indexeur, un accesseur de propriété ou un accesseur d’événement.|
|do|Crée une boucle [do](/dotnet/csharp/language-reference/keywords/do) `while`.|Dans une méthode, un indexeur, un accesseur de propriété ou un accesseur d’événement.|
|else|Crée un bloc [else](/dotnet/csharp/language-reference/keywords/if-else).|Dans une méthode, un indexeur, un accesseur de propriété ou un accesseur d’événement.|
|enum|Crée une déclaration [enum](/dotnet/csharp/language-reference/keywords/enum).|Dans un espace de noms (notamment l’espace de noms global), une classe ou un struct.|
|equals|Crée une déclaration de méthode qui substitue la méthode <xref:System.Object.Equals%2A> définie dans la classe <xref:System.Object>.|Dans une classe ou un struct.|
|exception|Crée une déclaration pour une classe qui dérive d’une exception (<xref:System.Exception> par défaut).|Dans un espace de noms (notamment l’espace de noms global), une classe ou un struct.|
|for|Crée une boucle [for](/dotnet/csharp/language-reference/keywords/for).|Dans une méthode, un indexeur, un accesseur de propriété ou un accesseur d’événement.|
|foreach|Crée une boucle [foreach](/dotnet/csharp/language-reference/keywords/foreach-in).|Dans une méthode, un indexeur, un accesseur de propriété ou un accesseur d’événement.|
|forr|Crée une boucle [for](/dotnet/csharp/language-reference/keywords/for) qui décrémente la variable de boucle après chaque itération.|Dans une méthode, un indexeur, un accesseur de propriété ou un accesseur d’événement.|
|if|Crée un bloc [if](/dotnet/csharp/language-reference/keywords/if-else).|Dans une méthode, un indexeur, un accesseur de propriété ou un accesseur d’événement.|
|indexer|Crée une déclaration d’indexeur.|Dans une classe ou un struct.|
|interface|Crée une déclaration [interface](/dotnet/csharp/language-reference/keywords/interface).|Dans un espace de noms (notamment l’espace de noms global), une classe ou un struct.|
|invoke|Crée un bloc qui appelle un événement en toute sécurité.|Dans une méthode, un indexeur, un accesseur de propriété ou un accesseur d’événement.|
|iterator|Crée un itérateur.|Dans une classe ou un struct.|
|iterindex|Crée une paire itérateur/indexeur « named » à l’aide d’une classe imbriquée.|Dans une classe ou un struct.|
|lock|Crée un bloc [lock](/dotnet/csharp/language-reference/keywords/lock-statement).|Dans une méthode, un indexeur, un accesseur de propriété ou un accesseur d’événement.|
|mbox|Crée un appel à <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName>. Vous devrez peut-être ajouter une référence à System.Windows.Forms.dll.|Dans une méthode, un indexeur, un accesseur de propriété ou un accesseur d’événement.|
|namespace|Crée une déclaration [namespace](/dotnet/csharp/language-reference/keywords/namespace).|Dans un espace de noms (notamment l’espace de noms global).|
|prop|Crée une déclaration de [propriété implémentée automatiquement](/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties).|Dans une classe ou un struct.|
|propfull|Crée une déclaration de propriété avec des accesseurs `get` et `set`.|Dans une classe ou un struct.|
|propg|Crée une [propriété implémentée automatiquement](/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties) en lecture seule avec un accesseur `set` private.|Dans une classe ou un struct.|
|sim|Crée une déclaration de méthode Main [static](/dotnet/csharp/language-reference/keywords/static) [int](/dotnet/csharp/language-reference/keywords/int).|Dans une classe ou un struct.|
|struct|Crée une déclaration [struct](/dotnet/csharp/language-reference/keywords/struct).|Dans un espace de noms (notamment l’espace de noms global), une classe ou un struct.|
|svm|Crée une déclaration de méthode Main [static](/dotnet/csharp/language-reference/keywords/static) [void](/dotnet/csharp/language-reference/keywords/void).|Dans une classe ou un struct.|
|switch|Crée un bloc [switch](/dotnet/csharp/language-reference/keywords/switch).|Dans une méthode, un indexeur, un accesseur de propriété ou un accesseur d’événement.|
|try|Crée un bloc [try-catch](/dotnet/csharp/language-reference/keywords/try-catch).|Dans une méthode, un indexeur, un accesseur de propriété ou un accesseur d’événement.|
|tryf|Crée un bloc [try-finally](/dotnet/csharp/language-reference/keywords/try-finally).|Dans une méthode, un indexeur, un accesseur de propriété ou un accesseur d’événement.|
|unchecked|Crée un bloc [unchecked](/dotnet/csharp/language-reference/keywords/unchecked).|Dans une méthode, un indexeur, un accesseur de propriété ou un accesseur d’événement.|
|unsafe|Crée un bloc [unsafe](/dotnet/csharp/language-reference/keywords/unsafe).|Dans une méthode, un indexeur, un accesseur de propriété ou un accesseur d’événement.|
|using|Crée une directive [using](/dotnet/csharp/language-reference/keywords/using-directive).|Dans un espace de noms (notamment l’espace de noms global).|
|while|Crée une boucle [while](/dotnet/csharp/language-reference/keywords/while).|Dans une méthode, un indexeur, un accesseur de propriété ou un accesseur d’événement.|

## <a name="see-also"></a>Voir aussi

[Fonctions des extraits de code](../ide/code-snippet-functions.md)  
[Extraits de code](../ide/code-snippets.md)  
[Paramètres de modèle](../ide/template-parameters.md)  
[Guide pratique pour utiliser des extraits de code Entourer de](../ide/how-to-use-surround-with-code-snippets.md)
