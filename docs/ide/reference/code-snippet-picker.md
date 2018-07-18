---
title: Sélecteur d'extraits de code
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.expansionpicker
helpviewer_keywords:
- Code Snippet Picker
- IntelliSense code snippets, Code Snippet Picker
- code snippets, Code Snippet Picker
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 774ee47f02fe146caade0540be5ee2fb7f59904e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31944178"
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

- [Bonnes pratiques pour l’utilisation des extraits de code](../../ide/best-practices-for-using-code-snippets.md)
- [Extraits de code IntelliSense Visual Basic](/dotnet/visual-basic/developing-apps/using-ide/intellisense-code-snippets)
- [Définition de signets dans le code](../../ide/setting-bookmarks-in-code.md)
- [Guide pratique pour utiliser des extraits de code Entourer de](../../ide/how-to-use-surround-with-code-snippets.md)