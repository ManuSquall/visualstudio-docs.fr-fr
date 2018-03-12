---
title: "Sélecteur d’extraits de code | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.expansionpicker
helpviewer_keywords:
- Code Snippet Picker
- IntelliSense code snippets, Code Snippet Picker
- code snippets, Code Snippet Picker
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 47eb9c801f638f108a8096b456784278e019f56d
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="code-snippet-picker"></a>Sélecteur d'extraits de code

L’éditeur Visual Studio Code fournit un **sélecteur d’extraits de code** qui vous permet, en quelques clics de souris, d’insérer des blocs de code prêts à l’emploi dans le document actif.

La procédure d’affichage du **sélecteur d’extraits de code** varie en fonction du langage que vous utilisez.

- Visual Basic : cliquez avec le bouton droit à l’emplacement voulu dans l’éditeur de code pour afficher le menu contextuel, puis sélectionnez **Insérer un extrait**.

- C# : cliquez avec le bouton droit à l’emplacement voulu dans l’éditeur de code pour afficher le menu contextuel, puis cliquez sur **Insérer un extrait** ou **Entourer de**.

- C++ : le **sélecteur d’extraits de code** n’est pas disponible.

- F# : le **sélecteur d’extraits de code** n’est pas disponible.

- JavaScript : cliquez avec le bouton droit à l’emplacement voulu dans l’éditeur de code pour afficher le menu contextuel, puis cliquez sur **Insérer un extrait** ou **Entourer de**.

- XML : cliquez avec le bouton droit à l’emplacement voulu dans l’éditeur de code pour afficher le menu contextuel, puis cliquez sur **Insérer un extrait** ou **Entourer de**.

- HTML : cliquez avec le bouton droit à l’emplacement voulu dans l’éditeur de code pour afficher le menu contextuel, puis cliquez sur **Insérer un extrait** ou **Entourer de**.

- SQL : cliquez avec le bouton droit à l’emplacement voulu dans l’éditeur de code pour afficher le menu contextuel, puis cliquez sur **Insérer un extrait**.

Dans la plupart des langages de développement Visual Studio, vous pouvez utiliser le **Gestionnaire des extraits de code** pour ajouter des dossiers à la liste des dossiers dans laquelle le **sélecteur d’extraits de code** recherche les fichiers d’extraits XML. Vous pouvez également créer vos propres extraits à ajouter à la liste. Pour plus d’informations, consultez [Procédure pas à pas : création d’un extrait de code](../../ide/walkthrough-creating-a-code-snippet.md).

## <a name="uielement-list"></a>Liste des éléments d’interface

Nom d'élément  
Un champ de texte modifiable qui affiche le nom de l’élément sélectionné dans la **liste d’éléments**. Pour effectuer une recherche incrémentielle de l’élément souhaité, commencez à taper son nom dans ce champ. Continuez d’ajouter des lettres jusqu’à ce que l’élément voulu soit sélectionné dans la **liste d’éléments**.

Liste d’éléments  
Une liste d’extraits de code disponibles pour être insérés, ou une liste de dossiers contenant des extraits de code. Pour insérer un extrait ou développer un dossier, sélectionnez l’élément voulu et appuyez sur Entrée.

## <a name="see-also"></a>Voir aussi

[Bonnes pratiques pour l’utilisation des extraits de code](../../ide/best-practices-for-using-code-snippets.md)  
[Extraits de code IntelliSense Visual Basic](/dotnet/visual-basic/developing-apps/using-ide/intellisense-code-snippets)  
[Définition de signets dans le code](../../ide/setting-bookmarks-in-code.md)  
[Guide pratique pour utiliser des extraits de code Entourer de](../../ide/how-to-use-surround-with-code-snippets.md)