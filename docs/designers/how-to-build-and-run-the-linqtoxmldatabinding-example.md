---
title: Guide pratique pour générer et exécuter l’exemple LinqToXmlDataBinding
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1164312d74259ad4f3a56750a487fb2578595cf0
ms.sourcegitcommit: db680e8fa8066f905e7f9240342ece7ab9259308
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2018
ms.locfileid: "37924159"
---
# <a name="how-to-build-and-run-the-linqtoxmldatabinding-example"></a>Guide pratique pour générer et exécuter l’exemple LinqToXmlDataBinding

Cette rubrique montre comment créer et générer le projet Visual Studio LinqToXmlDataBinding et comment exécuter l'exemple de programme WPF (Windows Presentation Foundation) LinqToXmlDataBinding résultant.

Pour plus d’informations sur Visual Studio, consultez [Présentation de l’IDE de Visual Studio](../ide/visual-studio-ide.md).

## <a name="create-and-populate-the-project"></a>Créer et remplir le projet

### <a name="to-create-the-starting-project"></a>Pour créer le projet de départ

1. Démarrez Visual Studio et créez une application C# WPF nommée LinqToXmlDataBinding. Le projet doit utiliser le .NET Framework 3.5 (ou version ultérieure).

1. Si elles ne sont pas déjà présentes, ajoutez les références de projet pour les assemblys .NET suivants :

    - System.Data

    - System.Data.DataSetExtensions

    - System.Xml

    - System.Xml.Linq

1. Générez la solution en appuyant sur **Ctrl**+**Maj**+**B**, puis exécutez-la en appuyant sur **F5**. Le projet doit être compilé sans erreur et exécuté en tant qu'application WPF générique.

### <a name="to-add-custom-code-to-the-project"></a>Pour ajouter du code personnalisé au projet

1. Dans l’Explorateur de solutions, renommez le fichier source **Window1.xaml** en **L2XDBForm.xaml**. Le fichier source dépendant **Window1.xaml.cs** doit être renommé automatiquement **L2XDBForm.xaml.cs**.

1. Remplacez le code source du fichier **L2XDBForm.xaml** par la section de code de la rubrique [Code source L2DBForm.xaml](../designers/l2dbform-xaml-source-code.md). Utilisez la vue source XAML pour travailler avec ce fichier.

1. De même, remplacez la source du fichier **L2XDBForm.xaml.cs** par le code fourni dans [Code source L2DBForm.xaml.cs](../designers/l2dbform-xaml-cs-source-code.md).

1. Dans le fichier **App.xaml**, remplacez toutes les occurrences de la chaîne `Window1.xaml` par `L2XDBForm.xaml`.

1. Générez la solution en appuyant sur **Ctrl**+**Maj**+**B**.

## <a name="run-the-program"></a>Exécuter le programme

Le programme LinqToXmlDataBinding permet à l'utilisateur d'afficher et de manipuler une liste de livres stockée en tant qu'élément XML incorporé.

### <a name="to-run-the-program-and-view-the-book-list"></a>Pour exécuter le programme et afficher la liste de livres

- Exécutez LinqToXmlDataBinding en appuyant sur **F5** (**Démarrer le débogage**) ou **Ctrl**+**F5** (**Démarrer sans débogage**).

   Une fenêtre de programme avec le titre **WPF Data Binding using LINQ to XML** apparaît.

- Notez la section supérieure de l’interface utilisateur, qui affiche le code **XML** brut qui représente la liste de livres. Il est affiché à l'aide d'un contrôle <xref:System.Windows.Controls.TextBlock> WPF, qui n'autorise pas d'interaction via le clavier ou la souris.

- La deuxième section verticale, libellée **Book List**, affiche les livres sous la forme d’une liste ordonnée en texte brut. Elle utilise un contrôle <xref:System.Windows.Controls.ListBox> qui autorise la sélection via la souris ou le clavier.

### <a name="to-add-and-delete-books-from-the-list"></a>Pour ajouter et supprimer des livres de la liste

- Pour ajouter un nouveau livre à la liste, entrez des valeurs dans les contrôles **ID** et **Value**<xref:System.Windows.Controls.TextBox> de la dernière section, **Add New Book**, puis cliquez sur le bouton **Add Book**. Notez que le livre est ajouté à la liste de livres et à la liste XML. Ce programme ne valide pas les valeurs d'entrée.

- Pour supprimer un livre de la liste, sélectionnez-le dans la section **Book List**, puis cliquez sur le bouton **Remove Selected Book**. Notez que l'entrée du livre a été supprimée de la liste de livres et du code XML source brut.

### <a name="to-edit-an-existing-book-entry"></a>Pour modifier une entrée de livre existante

1. Sélectionnez l’entrée de livre dans la deuxième section **Book List**. Ses valeurs actuelles doivent être affichées dans la troisième section, **Edit Selected Book**.

1. Modifiez les valeurs à l'aide du clavier. Dès que l'un des contrôles <xref:System.Windows.Controls.TextBox> perd le focus, les modifications sont propagées automatiquement au code source XML et à la liste de livres.

## <a name="see-also"></a>Voir aussi

- [Exemple de liaison de données WPF à l’aide de LINQ to XML](../designers/wpf-data-binding-using-linq-to-xml-example.md)
- [Procédure pas à pas : exemple LinqToXmlDataBinding](../designers/walkthrough-linqtoxmldatabinding-example.md)
- [Vue d’ensemble de l’IDE de Visual Studio](../ide/visual-studio-ide.md)