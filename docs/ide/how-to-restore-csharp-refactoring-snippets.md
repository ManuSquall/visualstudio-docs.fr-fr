---
redirect_url: /visualstudio/csharp-ide/refactoring-csharp
ms.openlocfilehash: cb4e45847008d99aa17b5ce3dde83da036a53dbb
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
title: "Guide pratique pour restaurer les extraits de code de refactorisation C# | Microsoft Docs" ms.custom: "" ms.date: "11/04/2016" ms.reviewer: "" ms.suite: "" ms.technology: 
  - "vs-ide-general" ms.tgt_pltfrm: "" ms.topic: "article" helpviewer_keywords: 
  - "expansion unsafe"
  - "expansions, unsafe" ms.assetid: 12114273-7f2f-43d0-abcb-2d4711a3a68d caps.latest.revision: 20 author: "gewarren" ms.author: "gewarren" manager: ghogen
---
# <a name="how-to-restore-c-refactoring-snippets"></a>Comment : restaurer les extraits de code de refactorisation C#
Les opérations de refactorisation C# reposent sur des extraits de code disponibles dans le répertoire suivant :  
  
 *Répertoire d’installation*\Microsoft Visual Studio 15.0\VC#\Snippets\\*ID de langue*\Refactoring  
  
 Si ce répertoire Refactoring, ou tous les fichiers de ce répertoire, sont supprimés ou endommagés, il se peut que les opérations de refactorisation C# ne fonctionnent pas dans l'environnement IDE. Les procédures suivantes peuvent vous aider à restaurer les extraits de code de refactorisation C#.  
  
### <a name="to-verify-c-refactoring-snippets-are-available-through-the-code-snippet-manager"></a>Pour vérifier la disponibilité des extraits de code de refactorisation C# au moyen du Gestionnaire des extraits de code  
  
1.  Dans le menu **Outils**, sélectionnez **Gestionnaire des extraits de code**.  
  
2.  Dans la boîte de dialogue **Gestionnaire des extraits de code**, sélectionnez **Visual C#** dans la liste déroulante **Langage**.  
  
     Un dossier **Refactoring** doit apparaître dans la liste en arborescence des dossiers.  
  
### <a name="to-restore-refactoring-see-comment-in-code-snippet-manager"></a>Pour restaurer la refactorisation, consultez le commentaire dans le Gestionnaire des extraits de code  
  
1.  Si le dossier **Refactoring** n’apparaît pas dans la liste en arborescence des dossiers du Gestionnaire des extraits de code, utilisez cette procédure pour rajouter des extraits de code de refactorisation dans le Gestionnaire des extraits de code.  
  
2.  Dans le menu **Outils**, sélectionnez **Gestionnaire des extraits de code**.  
  
3.  Dans la boîte de dialogue **Gestionnaire des extraits de code**, sélectionnez **Visual C#** dans la liste déroulante **Langage**.  
  
4.  Cliquez sur **Ajouter**. La boîte de dialogue **Répertoire des extraits de code**, qui vous aide à localiser et spécifier le répertoire à rajouter dans le Gestionnaire des extraits de code, s’affiche.  
  
5.  Localisez le dossier **Refactoring**, dont le chemin est :  
  
     *Répertoire d’installation*\Microsoft Visual Studio 15.0\VC#\Snippets\\*ID de langue*\Refactoring  
  
     Le chemin d’accès réel est semblable au suivant pour une installation par défaut :  
  
     C:\Program Files\Microsoft Visual Studio 15.0\VC#\Snippets\1033\Refactoring.  
  
6.  Cliquez sur **Ouvrir** dans la boîte de dialogue **Répertoire des extraits de code**, puis cliquez sur **OK** dans le Gestionnaire des extraits de code.  
  
## <a name="see-also"></a>Voir aussi  
 [Extraits de code Visual C#](../ide/visual-csharp-code-snippets.md)   
 [Refactorisation (C#)](../csharp-ide/refactoring-csharp.md)   
 [Extraits de code](../ide/code-snippets.md)