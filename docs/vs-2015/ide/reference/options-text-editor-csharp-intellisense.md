---
title: Options, Éditeur de texte, C#, IntelliSense | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Intellisense
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Intellisense
helpviewer_keywords:
- IntelliSense [J#], options
- underlines, wavy
- IntelliSense [C#], options
- IntelliSense [C#], wavy underlines
- wavy underlines
- Text Editor Options dialog box, IntelliSense
ms.assetid: 3466dedb-e5f4-424c-8dd8-e4941b2f4fc2
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 31c9909e5ea9364e806fdd2d7a39903bf1468abb
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49262169"
---
# <a name="options-text-editor-c-intellisense"></a>Options, Éditeur de texte, C#, IntelliSense
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Utilisez la page de propriétés **IntelliSense** pour modifier les paramètres qui affectent le comportement d’IntelliSense pour Visual C#. Pour accéder à la page de propriétés **IntelliSense**, cliquez sur **Options** dans le menu **Outils**, cliquez sur **C#** dans le dossier **Éditeur de texte**, puis cliquez sur **IntelliSense**.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 La page de propriétés **IntelliSense** contient les propriétés suivantes :  
  
## <a name="completion-lists"></a>Listes de saisie semi-automatique  
 **Afficher la liste de saisie semi-automatique après la saisie d’un caractère**  
 Quand cette option est sélectionnée et que vous commencez à taper, IntelliSense affiche automatiquement la liste de saisie semi-automatique. Quand cette option n’est pas sélectionnée, vous pouvez utiliser la saisie semi-automatique IntelliSense à partir du menu **IntelliSense** ou en appuyant sur Ctrl+espace.  
  
 **Placer les mots clés dans les listes de saisie semi-automatique**  
 Quand cette option est sélectionnée, IntelliSense ajoute les mots clés C#, par exemple, [class](http://msdn.microsoft.com/library/b95d8815-de18-4c3f-a8cc-a0a53bdf8690), à la liste de saisie semi-automatique.  
  
 **Placer les extraits de code dans les listes de saisie semi-automatique**  
 Quand cette option est sélectionnée, IntelliSense ajoute des alias pour les extraits de code C# à la liste de saisie semi-automatique. Si l’alias d’extrait de code est identique à un mot clé, par exemple, [class](http://msdn.microsoft.com/library/b95d8815-de18-4c3f-a8cc-a0a53bdf8690), le mot clé est remplacé par le raccourci. Pour plus d’informations, consultez [Extraits de code Visual C#](../../ide/visual-csharp-code-snippets.md).  
  
## <a name="selection-in-completion-lists"></a>Sélection dans la liste de saisie semi-automatique  
 **Validé en tapant les caractères suivants :**  
 Spécifie tous les caractères qui exécutent la saisie semi-automatique IntelliSense pour l’élément sélectionné dans la liste de saisie semi-automatique, une fois qu’ils ont été entrés.  
  
 **Validé en appuyant sur la barre d’espace**  
 Spécifie d’inclure l’action d’appuyer sur la barre d’espace pour exécuter la saisie semi-automatique IntelliSense pour l’élément sélectionné dans la liste de saisie semi-automatique.  
  
 **Ajouter une ligne avec entrée après le mot complet tapé**  
 Spécifie que si vous tapez tous les caractères d’une entrée dans la liste de saisie semi-automatique et que vous appuyez sur Entrée, une ligne est automatiquement créée et le curseur se déplace vers la nouvelle ligne.  
  
 Par exemple, si vous tapez `else` et appuyez sur Entrée, voici ce qui apparaît dans l’éditeur :  
  
 `else`  
  
 `|` (emplacement du curseur)  
  
 Toutefois, si vous tapez uniquement `el` et appuyez sur Entrée, voici ce qui apparaît dans l’éditeur :  
  
 `else|` (emplacement du curseur)  
  
## <a name="intellisense-member-selection"></a>Sélection de membres IntelliSense  
 **Présélectionner le dernier membre utilisé**  
 Quand cette option est sélectionnée, IntelliSense présélectionne les membres que vous avez récemment sélectionnés dans la zone Liste des membres contextuelle pour la saisie automatique du nom d’objet, pendant votre session actuelle dans l’environnement de développement intégré (IDE). L'historique des membres utilisés récemment est effacé entre chaque session dans l'IDE. Pour plus d’informations, consultez [IntelliSense pour les membres les plus récemment utilisés](../../misc/intellisense-for-most-recently-used-members.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Général, Environnement, boîte de dialogue Options](../../ide/reference/general-environment-options-dialog-box.md)   
 [Commentaires sur la documentation XML](http://msdn.microsoft.com/library/803b7f7b-7428-4725-b5db-9a6cff273199)   
 [Utilisation de la fonctionnalité IntelliSense](../../ide/using-intellisense.md)



