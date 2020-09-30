---
title: Extension de Visual Studio pour Mac
description: Les fonctionnalités de Visual Studio pour Mac peuvent être étendues avec des modules appelés « packages d’extension ». La première partie de ce guide crée un package d’extension simple de Visual Studio pour Mac qui permet d’insérer la date et l’heure dans un document. La seconde partie de ce guide présente les concepts de base du système des packages d’extension et certaines des API principales qui sont à la base de Visual Studio pour Mac.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 12/20/2019
ms.technology: vs-ide-sdk
ms.assetid: D5245AB0-8404-426B-B538-F49125E672B2
ms.openlocfilehash: 10beb7e95807a098cbe6efa89d02fdfa866bc2b8
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91583981"
---
# <a name="extending-visual-studio-for-mac"></a>Extension de Visual Studio pour Mac

Visual Studio pour Mac se compose d’un ensemble de modules appelés *Packages d’extension*. Vous pouvez utiliser des packages d’extension pour introduire une nouvelle fonctionnalité dans Visual Studio pour Mac, comme la prise en charge d’un langage supplémentaire ou d’un nouveau modèle de projet.

Les packages d’extension sont créés à partir des points d’*extension* d’autres packages d’extension. Les points d’extension sont des espaces réservés pour des zones sur lesquelles les développements peuvent s’appuyer, par exemple un menu ou la liste des commandes de l’IDE. Un package d’extension peut être créé à partir d’un point d’extension en inscrivant un nœud de données structurées appelé « extension », comme un nouvel élément de menu ou une nouvelle commande. Chaque point d’extension accepte certains types d’extensions, comme une *Commande*, *Panneau* ou *FileTemplate*. Un module qui contient des points d’extension est appelé un *hôte de compléments*, car il peut être étendu par d’autres packages d’extension.

Pour personnaliser Visual Studio pour Mac, vous pouvez créer un package d’extension qui est créé à partir de points d’extension contenus dans les hôtes de compléments de bibliothèques préexistantes dans Visual Studio pour Mac, comme illustré dans le diagramme suivant :

![Architecture des compléments](media/extending-visual-studio-mac-addin1.png)

Pour qu’un package d’extension soit créé à partir de Visual Studio pour Mac, il doit avoir des extensions qui sont créées à partir de points d’extension préexistants dans l’IDE Visual Studio pour Mac. Lorsqu’un package d’extension repose sur un point d’extension défini dans un hôte de complément, il est dit qu’il a une _dépendance_   sur ce package d’extension.

L’avantage de cette conception modulaire est que Visual Studio pour Mac est extensible : il existe de nombreux points d’extension sur lesquels peuvent être créés des packages d’extension personnalisés. La prise en charge de C# et de F#, des outils de débogage et des modèles de projet sont des exemples de packages d’extension existants.

> [!NOTE]
> Si vous avez un projet Add-in Maker créé avant Add-in Maker 1.2, vous devez migrer votre projet comme indiqué dans les étapes décrites [ici](https://mhut.ch/addinmaker/1.2).

<!---The [Walkthrough](~/extending-visual-studio-mac-walkthrough.md) topic explains how to build an extension package that uses a *Command* to insert the date and time into an open text document.--->

Cette section présente les différents fichiers générés par Add-in Maker et les données nécessaires à une extension de commande.

## <a name="attribute-files"></a>Fichiers d’attributs

Les packages d’extension stockent des métadonnées sur leur nom, leur version, leurs dépendances et d’autres informations dans des attributs C#. Add-in Maker crée deux fichiers, `AddinInfo.cs` et `AssemblyInfo.cs`, pour stocker et organiser ces informations. Les packages d’extension doivent avoir un ID et un espace de noms uniques spécifiés dans leur * `Addin` attribut*:

```csharp
[assembly:Addin (
   "DateInserter",
   Namespace = "DateInserter",
   Version = "1.0"
)]
```

Ils doivent également déclarer les dépendances des packages d’extension qui ont les points d’extension auxquels ils se connectent, qui sont automatiquement référencés au moment du build.

De plus, des références supplémentaires peuvent être ajoutées via le nœud Référence de complément dans le panneau Solution pour le projet, comme illustré par l’image suivante :

![Capture d’écran - Insérer la date](media/extending-visual-studio-mac-addin13.png)

Leurs attributs `assembly:AddinDependency` correspondants sont également ajoutés au moment de la génération. Une fois que les métadonnées et les déclarations de dépendance sont en place, vous pouvez vous concentrer sur les blocs de construction essentiels du package d’extension.

## <a name="extensions-and-extension-points"></a>Extensions et points d’extension

Un point d’extension est un espace réservé qui définit une structure de données (un type), tandis qu’une extension définit les données qui se conforment à une structure spécifiée par un point d’extension spécifique. Les points d’extension spécifient dans leur déclaration les types d’extension qu’ils peuvent accepter. Les extensions sont déclarées via des noms de types ou des chemins d’extension. Pour une explication plus approfondie sur la création du point d’extension dont vous avez besoin, consultez les [Informations de référence sur les points d’extension](https://github.com/mono/mono-addins/wiki/Extension-Points).

L’architecture extension/point d’extension rend le développement de Visual Studio pour Mac rapide et modulable.

<!--Since there are a large number of extension types, this article focuses on the ones used in the extension package that was built in the [Walkthrough](~/extending-visual-studio-mac-walkthrough.md).-->

### <a name="command-extensions"></a>Extensions de commande

<!--[Walkthrough](~/extending-visual-studio-mac-walkthrough.md) uses a Command Extension - an extension that points to methods that are called every time it is executed. -->

Les extensions de commande sont des extensions qui pointent vers des méthodes appelées chaque fois qu’elles sont exécutées.

Les extensions de commande sont définies en ajoutant des entrées au point d’extension `/MonoDevelop/Ide/Commands`. Nous avons défini notre extension dans `Manifest.addin.xml` avec le code suivant :

 ```xml
<Extension path="/MonoDevelop/Ide/Commands/Edit">
  <Command id="DateInserter.DateInserterCommands.InsertDate"
            _label="Insert Date"
            _description="Insert the current date"
            defaultHandler="DateInserter.InsertDateHandler" />
</Extension>
```

Le nœud de l’extension contient un attribut path qui spécifie le point d’extension auquel elle se connecte, dans ce cas `/MonoDevelop/Ide/Commands/Edit`. Il agit également comme nœud parent de la commande. Le nœud Commande a les attributs suivants :

* `id` : spécifie l’identificateur pour cette commande. Les identificateurs de commande doivent être déclarés comme membres d’énumération, et ils sont utilisés pour connecter des commandes à des éléments de commande.
* `_label` : Le texte à afficher dans les menus.
* `_description` : texte à afficher comme info-bulle pour les boutons de la barre d’outils.
* `defaultHandler` - Spécifie la classe `CommandHandler` qui gère la commande

<!--To invoke the command from the Edit Menu, the walkthrough creates a CommandItem extension that plugs into the `/MonoDevelop/Ide/MainMenu/Edit` extension point:-->

L’extrait de code suivant illustre une extension CommandItem qui se connecte au point d’extension `/MonoDevelop/Ide/MainMenu/Edit` :

```xml
<Extension path="/MonoDevelop/Ide/MainMenu/Edit">
  <CommandItem id="DateInserter.DateInserterCommands.InsertDate" />
</Extension>
```

Un élément de commande place une commande spécifiée dans son attribut `id` dans un menu. Cet élément de commande étend le point d’extension `/MonoDevelop/Ide/MainMenu/Edit`, ce qui fait apparaître le libellé de la commande dans le **menu Edition**. Notez que l’ID dans l’élément de commande correspond à l’ID du nœud Commande, `InsertDate`. Si vous supprimez l’élément de commande, l’option **Insérer la date** disparaît du menu Edition.

### <a name="command-handlers"></a>Gestionnaires de commandes

L’extension `InsertDateHandler` est une extension de la classe `CommandHandler`. Elle remplace deux méthodes, `Update` et `Run`. Une requête est faite à la méthode `Update` chaque fois qu’une commande est affichée dans un menu ou exécutée via des combinaisons de touches. En modifiant l’objet info, vous pouvez désactiver la commande ou la rendre invisible, remplir des commandes de tableau, etc. Cette méthode `Update` désactive la commande si elle ne peut pas trouver un *Document* actif avec un *éditeur de texte* pour y insérer du texte :

```csharp
protected override void Update (CommandInfo info)
{
    info.Enabled = IdeApp.Workbench.ActiveDocument?.Editor != null;
}
```

Vous devez remplacer la méthode `Update` seulement quand vous avez une logique spéciale pour activer ou masquer la commande. La méthode `Run` s’exécute chaque fois qu’un utilisateur exécute une commande, ce qui dans ce cas se produit quand un utilisateur sélectionne la commande dans le menu Edition. Cette méthode insère la date et l’heure au point d’insertion dans l’éditeur de texte :

```csharp
protected override void Run ()
{
  var editor = IdeApp.Workbench.ActiveDocument.Editor;
  var date = DateTime.Now.ToString ();
  editor.InsertAtCaret (date);
}
```

Déclarez le type de commande comme membre d’énumération dans `DateInserterCommands` :

```csharp
public enum DateInserterCommands
{
  InsertDate,
}
```

Cela lie la commande et l’élément de commande : l’élément de commande appelle la commande quand il est sélectionné dans le **menu Édition**.

## <a name="ide-apis"></a>API de l’IDE

<!--The extension package detailed in the [Walkthrough](~/extending-visual-studio-mac-walkthrough.md) deals with the Text Editor in Visual Studio for Mac, but this is only one of many possible areas for customization. -->

Pour plus d’informations sur l’étendue de ce qui peut faire l’objet de développements, consultez [Extension Tree Reference](https://www.monodevelop.com/developers/articles/extension-tree-reference/) et [API Overview](https://www.monodevelop.com/developers/articles/api-overview/). Si vous créez des packages d’extension avancés, reportez-vous aussi à [Developer Articles](https://www.monodevelop.com/developers/articles/). Voici une liste partielle des éléments que vous pouvez personnaliser :

* Panneaux
* Schémas de combinaisons de touches
* Stratégies
* Formateurs de code
* Formats de fichiers projet
* Panneaux de préférences
* Panneaux d’options
* Protocoles du débogueur
* Visualiseurs du débogueur
* Dispositions d’espace de travail
* Nœuds d’arborescence de panneau de solution
* Marges de l’éditeur de code
* Moteurs de tests unitaires
* Générateurs de code
* Extraits de code
* Versions cibles de .NET Framework
* Runtime cible
* Back-ends de système de contrôle de version
* Refactorisation
* Gestionnaires d’exécution
* Mise en surbrillance de la syntaxe

## <a name="extending-the-new-editor"></a>Extension du nouvel éditeur

Visual Studio pour Mac [propose un nouvel éditeur de texte Cocoa natif](/visualstudio/releasenotes/vs2019-mac-relnotes) reposant sur les mêmes couches d’éditeur que Visual Studio sur Windows.

Un des nombreux avantages du partage de l’éditeur entre Visual Studio et Visual Studio pour Mac est que le code qui cible l’éditeur Visual Studio peut être adapté pour être exécuté sur Visual Studio pour Mac.

> [!NOTE]
> Le nouvel éditeur prend uniquement en charge les fichiers C# pour l’instant. Les autres langages et formats de fichier s’ouvriront dans l’ancien éditeur. L’ancien éditeur implémente toutefois certaines des API de l’éditeur Visual Studio décrites ci-dessous.

### <a name="visual-studio-editor-overview"></a>Vue d’ensemble de l’éditeur Visual Studio

![Architecture de l’éditeur Visual Studio](media/vs-editor-architecture.png)

Avant de nous pencher sur les détails de l’extension spécifique à Visual Studio pour Mac, il convient d’en savoir plus sur l’éditeur partagé lui-même. Voici quelques ressources qui peuvent approfondir cette compréhension :

* [Managed Extensibility Framework](/dotnet/framework/mef/index)
* [MEF dans l’éditeur](/visualstudio/extensibility/managed-extensibility-framework-in-the-editor)
* [Dans l’éditeur](/visualstudio/extensibility/inside-the-editor)
* [Points d’extension du service de langage et de l’éditeur](/visualstudio/extensibility/language-service-and-editor-extension-points)
* [Une vidéo de présentation de l’architecture de l’éditeur](https://www.youtube.com/watch?v=PkYVztKjO9A)

Avec ces ressources en main, les principaux concepts auxquels vous devez être familiarisé sont un [`ITextBuffer`](/dotnet/api/microsoft.visualstudio.text.itextbuffer) et un [`ITextView`](/dotnet/api/microsoft.visualstudio.text.editor.itextview) :

* Un `ITextBuffer` est une représentation de texte en mémoire qui peut être modifiée au fil du temps. La propriété `CurrentSnapshot` sur `ITextBuffer` retourne une représentation *immuable* du contenu actuel de la mémoire tampon, une instance de `ITextSnapshot`. Lorsqu’une modification est effectuée sur la mémoire tampon, la propriété CurrentSnapshot est mise à jour vers la dernière version. Les analyseurs peuvent inspecter l’instantané de texte sur n’importe quel thread et son contenu a l’assurance de ne jamais changer.

* Un `ITextView` est la représentation de l’interface utilisateur de la façon dont `ITextBuffer` est rendu sur un écran dans le contrôle d'édition. Il contient une référence à sa mémoire tampon de texte, ainsi que `Caret`, `Selection` et d’autres concepts liés à l’interface utilisateur.

Pour un donné [`MonoDevelop.Ide.Gui.Document`](http://source.monodevelop.com/#MonoDevelop.Ide/MonoDevelop.Ide.Gui/Document.cs,4e960d4735f089b5) , vous pouvez récupérer les sous-jacents `ITextBuffer` et `ITextView` via `Document.GetContent<ITextBuffer>()` et `Document.GetContent<ITextView>()` respectivement.

## <a name="additional-information"></a>Informations supplémentaires

> [!NOTE]
> Nous travaillons actuellement à améliorer les scénarios d’extensibilité pour Visual Studio pour Mac. Si vous créez des extensions et que vous avez besoin d’aide ou d’informations supplémentaires, ou que vous avez des commentaires à partager, veuillez remplir le formulaire [Création d’extensions Visual Studio pour Mac](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR3YufGX_azhFl7MkrQO9i9JUNVMyMklVVlAzQVdURDg2NjQxTFRBVTJURC4u).

## <a name="see-also"></a>Voir aussi

- [Développer des extensions Visual Studio (sur Windows)](/visualstudio/extensibility/starting-to-develop-visual-studio-extensions)