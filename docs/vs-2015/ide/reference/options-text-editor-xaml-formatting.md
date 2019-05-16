---
title: Options, Éditeur de texte, XAML, Mise en forme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XAML.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.XAML.Miscellaneous
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
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8f820ac16667a9550db17bc252c547f16b81e70b
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65696006"
---
# <a name="options-text-editor-xaml-formatting"></a>Options, Éditeur de texte, XAML, Mise en forme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Utilisez la page de propriétés **Mise en forme** pour spécifier la mise en forme des éléments et attributs dans vos documents XAML. Pour ouvrir la boîte de dialogue **Options**, cliquez sur le menu **Outils**, puis sur **Options**. Pour accéder à la page de propriétés **Mise en forme**, développez le nœud **Éditeur de texte**, **XAML**, **Mise en forme**.

> [!NOTE]
> Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="auto-formatting-events"></a>Événements de mise en forme automatique
La mise en forme automatique peut se produire quand un des événements suivants est détecté.

- Saisie d’une balise de fin ou une balise simple

- Saisie d’une balise de début

- Collage du contenu du Presse-papiers

- Mise en forme des commandes de clavier

  Vous pouvez spécifier quels événements entraînent la mise en forme automatique.

|||
|-|-|
|**Après une balise de fin ou une balise simple**|La mise en forme automatique se produit quand vous avez tapé une balise de fin ou une balise simple. Une balise simple n’a pas d’attributs, par exemple `<Button />`.|
|**Après une balise de début**|La mise en forme automatique se produit quand vous avez tapé une balise de début.|
|**En collant le contenu du presse-papiers**|La mise en forme automatique se produit quand vous collez le code XAML à partir du Presse-papiers dans la vue XAML.|

## <a name="quotation-mark-style"></a>Style de guillemet
Ce paramètre indique si les valeurs d’attribut sont entre guillemets simples ou doubles. La mise en forme automatique et la saisie semi-automatique IntelliSense utilisent ce paramètre.

Une fois que vous définissez cette option, seuls les attributs ajoutés par la suite à l’aide du concepteur ou manuellement dans la vue XAML sont affectés.

|||
|-|-|
|**Guillemets doubles (")**|Les valeurs d’attribut sont entre guillemets doubles.<br /><br /> `<Button Name="button1">Hello</Button>`|
|**Guillemets simples (')**|Les valeurs d’attribut sont entre guillemets simples.<br /><br /> `<Button Name='button1'>Hello</Button>`|

## <a name="tag-wrapping"></a>Étiquette de renvoi à la ligne
Vous pouvez spécifier une longueur de ligne pour la balise de renvoi à la ligne. Quand la balise de renvoi à la ligne est activée, tout XAML ajouté par la suite à l’aide du concepteur est encapsulé de manière appropriée.

|||
|-|-|
|**Renvoyer à la ligne les balises qui dépassent la longueur spécifiée**|Spécifie si les lignes sont renvoyées à la longueur de ligne spécifiée par **Longueur**.|
|**Longueur**|Nombre de caractères qu’une ligne peut contenir. Si nécessaire, certaines lignes XAML peuvent dépasser la longueur spécifiée.|

## <a name="attribute-spacing"></a>Espacement d'attributs
Ce paramètre permet de contrôler la manière dont les attributs sont organisés dans votre document XAML.

|||
|-|-|
|**Conserver les nouvelles lignes et les espaces entre les attributs**|La mise en forme automatique n’affecte pas les nouvelles lignes et les espaces entre les attributs.<br /><br /> `<Button Height="23" Name="button1"`<br /><br /> `Width="75">Hello</Button>`|
|**Insérer un seul espace entre les attributs**|Les attributs occupent une seule ligne, avec un espace séparant les attributs adjacents. Les paramètres de balise de renvoi à la ligne sont appliqués.<br /><br /> `<Button Height="23" Name="button1" Width="75">Hello</Button>`|
|**Positionner chaque attribut sur une ligne distincte**|Chaque attribut occupe sa propre ligne. Cela est utile quand il existe beaucoup d’attributs.<br /><br /> `<Button`<br /><br /> `Height="23"`<br /><br /> `Name="button1"`<br /><br /> `Width="75">Hello</Button>`|
|**Positionner le premier attribut sur la même ligne que la balise de début**|Quand cette option est cochée, le premier attribut apparaît sur la même ligne que la balise de début de l’élément.<br /><br /> `<Button Height="23"`<br /><br /> `Name="button1"`<br /><br /> `Width="75">Hello</Button>`|

## <a name="element-spacing"></a>Espacement d'éléments
Ce paramètre permet de contrôler la manière dont les éléments sont organisés dans votre document XAML.

|                                                               |                                                                                                                                                                                       |
|---------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Conserver les nouvelles lignes du contenu**                             | Les lignes vides du contenu de l’élément ne sont pas supprimées.<br /><br /> `<Grid>`<br /><br /><br /><br /><br /><br /> `<Button Name="button1">Hello</Button>`<br /><br /><br /><br /> `</Grid>\`   |
| **Réduire plusieurs lignes vides du contenu en une seule ligne** | Les lignes vides du contenu de l’élément sont réduites en une seule ligne.<br /><br /> `<Grid>`<br /><br /><br /><br /> `<Button Name="button1">Hello</Button>`<br /><br /><br /><br /> `</Grid>` |
| **Supprimer les lignes vides du contenu**                             | Toutes les lignes vides du contenu de l’élément sont supprimées.<br /><br /> `<Grid>`<br /><br /> `<Button Name="button1">Hello</Button>`<br /><br /> `</Grid>`                                        |

## <a name="auto-insert"></a>Insertion automatique
Ce paramètre permet de contrôler à quel moment les balises et les guillemets sont générés automatiquement.

|||
|-|-|
|**Balises de fermeture**|Spécifie si la balise de fermeture d’un élément est générée automatiquement quand vous fermez la balise d’ouverture avec le signe supérieur à (>).|
|**Guillemets d’attribut**|Spécifie si les guillemets de fermeture sont générés quand vous sélectionnez une valeur d’attribut dans la liste déroulante de saisie semi-automatique de l’instruction.|
|**Accolades fermantes pour MarkupExtensions**|Spécifie si l’accolade fermante d’une extension de balisage (}) est générée automatiquement quand vous tapez le caractère d’accolade ouvrante ({).|
|**Virgules pour séparer les paramètres MarkupExtension**|Spécifie si des virgules sont générées quand vous tapez plusieurs paramètres dans une extension de balisage.|

## <a name="default-view"></a>Vue par défaut
Utilisez ce paramètre pour contrôler si le mode Design apparaît quand des documents XAML sont chargés.

|||
|-|-|
|**Toujours ouvrir des documents dans la vue XAML complète**|Indique si les documents XAML apparaissent uniquement dans la vue XAML, sans mode Design. Utile pour le chargement de documents volumineux.|

## <a name="toolbox"></a>Boîte à outils
Utilisez ce paramètre pour spécifier si les contrôles utilisateur et des contrôles personnalisés sont affichés dans la boîte à outils.

|||
|-|-|
|**Remplir automatiquement les éléments de la boîte à outils**|Spécifie si les contrôles utilisateur et les contrôles personnalisés dans la solution actuelle sont automatiquement affichés dans la boîte à outils.|

## <a name="see-also"></a>Voir aussi
[Intégration du format XAML au format WPF](https://msdn.microsoft.com/library/5d858575-a83b-42df-ad3f-047ed2d6e3c8)  
[Guide pratique pour Modifier les paramètres de vue XAML](https://msdn.microsoft.com/aee87c79-ca01-4f84-8fb7-a9e47048ee47)  
[Procédures pas à pas pour XAML et le code](https://msdn.microsoft.com/b3ff41a0-a2a3-4f61-b698-ac88ec8f799c)
