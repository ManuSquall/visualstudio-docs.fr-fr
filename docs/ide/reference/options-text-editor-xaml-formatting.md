---
title: Options, Éditeur de texte, XAML, Mise en forme
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XAML.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.XAML.Formatting.Spacing
helpviewer_keywords:
- element spacing, XAML view settings
- attribute spacing, XAML view settings
- XAML view settings, auto-formatting events
- auto-formatting events, XAML view settings
- XAML view settings, tag wrapping
- XAML view settings, auto insert
- quotation mark style, XAML view settings
- XAML formatting, WPF Designer
- XAML view settings, Toolbox
- XAML view settings, element spacing
- default view, XAML view settings
- auto insert, XAML view settings
- XAML view settings, default view
- XAML view settings, quotation mark style
- tag wrapping, XAML view settings
- WPF Designer, XAML formatting
- XAML view settings, attribute spacing
ms.assetid: ad3820b1-0d94-4807-a74c-c3467ed973a2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 4686760625062fea7984cdc05386284f8f98c4ee
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388986"
---
# <a name="options-text-editor-xaml-formatting"></a>Options, Éditeur de texte, XAML, Mise en forme

Utilisez la page de propriétés **Mise en forme** pour spécifier la mise en forme des éléments et attributs dans vos documents XAML. Pour ouvrir la boîte de dialogue **Options**, cliquez sur le menu **Outils**, puis sur **Options**. Pour accéder à la page de propriétés **Mise en forme**, développez le nœud **Éditeur de texte** > **XAML** > **Mise en forme**.

## <a name="auto-formatting-events"></a>Événements de mise en forme automatique

La mise en forme automatique peut se produire quand un des événements suivants est détecté.

-   Saisie d’une balise de fin ou une balise simple

-   Saisie d’une balise de début

-   Collage du contenu du Presse-papiers

-   Mise en forme des commandes de clavier

Vous pouvez spécifier quels événements provoquent la mise en forme automatique.

**Après une balise de fin ou une balise simple**

La mise en forme automatique se produit quand vous finissez de taper une balise de fin ou une balise simple. Une balise simple n’a pas d’attributs, par exemple `<Button />`.

**Après une balise de début**

La mise en forme automatique se produit quand vous avez fini de taper une balise de début.

**En collant le contenu du presse-papiers**

La mise en forme automatique se produit quand vous collez du XAML à partir du Presse-papiers dans la vue XAML.

## <a name="quotation-mark-style"></a>Style de guillemet

Ce paramètre indique si les valeurs d’attribut sont entre guillemets simples ou doubles. La mise en forme automatique et la complétion automatique IntelliSense utilisent ce paramètre.

Une fois que vous définissez cette option, seuls les attributs ajoutés par la suite à l’aide du concepteur ou manuellement dans la vue XAML sont affectés.

**Guillemets doubles (")**

Les valeurs d’attribut sont entre guillemets doubles.
`<Button Name="button1">Hello</Button>`

**Guillemets simples (')**

Les valeurs d’attribut sont entre guillemets simples.
`<Button Name='button1'>Hello</Button>`

## <a name="tag-wrapping"></a>Étiquette de renvoi à la ligne

Vous pouvez spécifier une longueur de ligne pour la balise de renvoi à la ligne. Quand la balise de renvoi à la ligne est activée, tout XAML ajouté par la suite à l’aide du concepteur est encapsulé de manière appropriée.

**Renvoyer à la ligne les balises qui dépassent la longueur spécifiée**

Spécifie si les lignes sont renvoyées à la longueur de ligne spécifiée par **Longueur**.

**Longueur**

Nombre de caractères qu’une ligne peut contenir. Si nécessaire, certaines lignes XAML peuvent dépasser la longueur spécifiée.

## <a name="attribute-spacing"></a>Espacement d'attributs

Ce paramètre permet de contrôler la manière dont les attributs sont organisés dans votre document XAML.

**Conserver les nouvelles lignes et les espaces entre les attributs**

La mise en forme automatique n’affecte pas les nouvelles lignes et les espaces entre les attributs.

```xml
<Button Height="23"   Name="button1"
Width="75">Hello</Button>
```

**Insérer un seul espace entre les attributs**

Les attributs occupent une seule ligne, avec un espace séparant les attributs adjacents. Les paramètres de balise de renvoi à la ligne sont appliqués.

```xml
<Button Height="23" Name="button1" Width="75">Hello</Button>
```

**Positionner chaque attribut sur une ligne distincte**

Chaque attribut occupe sa propre ligne, ce qui est pratique quand de nombreux attributs sont présents.

```xml
<Button
Height="23"
Name="button1"
Width="75">Hello</Button>
```

**Positionner le premier attribut sur la même ligne que la balise de début**

Quand cette option est cochée, le premier attribut apparaît sur la même ligne que la balise de début de l’élément.

```xml
<Button Height="23"
Name="button1"
Width="75">Hello</Button>
```

## <a name="element-spacing"></a>Espacement d'éléments

Ce paramètre permet de contrôler la manière dont les éléments sont organisés dans votre document XAML.

**Conserver les nouvelles lignes du contenu**

Les lignes vides du contenu de l’élément ne sont pas supprimées.

```xml
<Grid>


<Button Name="button1">Hello</Button>

</Grid>
```

**Réduire plusieurs lignes vides du contenu en une seule ligne**

Les lignes vides du contenu de l’élément sont réduites en une seule ligne.

```xml
<Grid>

<Button Name="button1">Hello</Button>

</Grid>
```

**Supprimer les lignes vides du contenu**

Toutes les lignes vides du contenu de l’élément sont supprimées.

```xml
<Grid>
<Button Name="button1">Hello</Button>
</Grid>
```

## <a name="see-also"></a>Voir aussi

- [Intégration du format XAML au format WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)