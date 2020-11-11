---
title: Débogage - Visualisations des données
description: Le débogage est une partie courante et nécessaire de la programmation. Visual Studio pour Mac contient une suite complète de fonctionnalités facilitant le débogage. Cet article présente les différentes visualisations des données qui peuvent être affichées lors de l’inspection d’objets dans le débogueur.
author: jmatthiesen
ms.author: jomatthi
ms.date: 11/09/2020
ms.technology: vs-ide-debug
ms.assetid: 527E6BEC-EF15-4002-ACB5-62AE1C16F6B7
ms.openlocfilehash: 838762435268ea06c09392475f294dbb22c3038d
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493242"
---
# <a name="data-visualizations"></a>Visualisations de données

Visual Studio pour Mac offre la prise en charge de l’interface utilisateur du débogueur, qui permet des visualisations des valeurs d’une variable, d’un champ ou d’une propriété pendant le débogage. Ces visualiseurs de données montrent une version étendue des données et permettent aux développeurs d’inspecter des structures connues, par exemple en affichant la couleur d’un struct.

Les visualiseurs de la fenêtre  **variables locales** de débogage peuvent être affichés en cliquant sur l’icône d’aperçu qui apparaît à droite de la valeur lorsque l’utilisateur pointe sur la ligne :

![Variables locales (fenêtre)](media/data-visualizations-image9.png)

La liste ci-dessous présente la plupart des nouvelles visualisations disponibles lors du débogage dans Visual Studio pour Mac.

## <a name="point"></a>Point
Un point/PointF, ou CGPoint dans iOS et Mac, s’affiche sous la forme d’un tuple qui affiche les valeurs X et Y dans les fenêtres de débogage :

![Visualisation d’une structure Point](media/data-visualizations-image10.png)

## <a name="size"></a>Taille
Une structure Size/SizeF, ou CGSize dans iOS et Mac, est restituée sous la forme d’un rectangle. Elle est dessinée à l’échelle jusqu’à ce qu’une dimension dépasse 250 pixels, limite à partir de laquelle elle est mise à l’échelle par rapport au rectangle avec comme dimension maximale 250 pixels :

[Visualisation d’une structure Size](media/data-visualizations-image11.png)

## <a name="rectangle"></a>Rectangle
Une structure Rectangle/RectangleF, ou CGRect dans iOS et Mac, affiche les dimensions et l’origine. Similaire à la structure Size, elle est dessinée à l’échelle, jusqu’à ce qu’une dimension dépasse 250 pixels :

![Visualisation d’une structure Rectangle](media/data-visualizations-image12.png)

## <a name="coordinate"></a>Coordonnée
Les coordonnées sont tracées sur un plan, avec l’emplacement épinglé au centre :

[Visualisation d’une coordonnée](media/data-visualizations-image13.png)

## <a name="color"></a>Couleur
Ceci affiche les propriétés UIColor, CGColor et Color, en montrant un aperçu de la couleur, les composants RVBA, les valeurs Teinte-Saturation-Luminosité et la valeur hexadécimale de la couleur :

![Visualisation d’une couleur](media/data-visualizations-image14.png)

## <a name="images"></a>Images

Le média est affiché à l’échelle, jusqu’à une dimension maximale de 250 pixels, et est ajusté quand l’image dépasse 250 pixels :

![Visualisation d’une image](media/data-visualizations-image15.png)

## <a name="bezier-curves"></a>Courbes de Bézier

Le visualiseur affiche un `NSBezierPath` :

![Visualisation d’une courbe de Bézier](media/data-visualizations-image16.png)

## <a name="string"></a>String

Une chaîne de moins de 100 caractères s’affiche en totalité, sans aperçu. Les chaînes plus longues s’affichent en totalité dans l’aperçu. Les chaînes sont modifiables, et le visualiseur comporte un bouton Modifier, qui permet la modification de la valeur de la chaîne dans l’aperçu ou dans l’éditeur de valeur de chaîne, montré ci-dessous :

![Visualisation d’une chaîne](media/data-visualizations-image17.png)

### <a name="small-strings"></a>Chaînes de petite taille :
![Visualisation d’une chaîne de petite taille](media/data-visualizations-image18.png)]

### <a name="medium-length-strings"></a>Chaînes de longueur moyenne :
![Visualisation d’une chaîne de longueur moyenne](media/data-visualizations-image19.png)

### <a name="editor"></a>Éditeur :

![Visualisation de l’éditeur](media/data-visualizations-image21.png)

## <a name="ienumerable"></a>IEnumerable

IEnumerable énumère toutes les valeurs ; les valeurs de chaque élément peuvent être affichés en cliquant sur le bouton **Afficher les valeurs**. L’option IEnumerable n’affiche pas les valeurs pour les objets tels que `Array`, `ArrayList`, `List<>`, `Dictionary<,>`, car ceux-ci ont leur propre visualiseur dans le débogueur.

![Visualisation d’un élément IEnumerable](media/data-visualizations-image22.png)

## <a name="other-visualizers"></a>Autres visualiseurs

Voici quelques autres types qui ont leur propre visualiseur :

![Autre visualisation](media/data-visualizations-image23.png)

* **Primitives**
  * Ceci affiche la valeur brute du type primitif.
* **Variables**
  * Ceci affiche la valeur du champ sans le qualificateur de type enum.
* **Passent**
  * Affiché dans le format (,)
* **Null**
  * Affiche la valeur « null ».
* **URL**
  * Ceci affiche un lien hypertexte sur lequel vous pouvez cliquer.
* **IntPtr**
  * Ceci affiche une représentation hexadécimale de IntPtr.

## <a name="see-also"></a>Voir aussi

- [Inspecter les variables dans les fenêtres Automatique et Variables locales (Visual Studio sur Windows)](/visualstudio/debugger/autos-and-locals-windows)
- [Afficher les chaînes dans un visualiseur (Visual Studio sur Windows)](/visualstudio/debugger/string-visualizer-dialog-box)