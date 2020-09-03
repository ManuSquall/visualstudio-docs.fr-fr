---
title: Options, Éditeur de texte, XML, Mise en forme
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Formatting
ms.assetid: 203e60b2-7b80-4ff4-9fa1-aa9f4374377b
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: b5dabfbc4f705d7de9fa881f373994714e43d26a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75568137"
---
# <a name="options-text-editor-xml-formatting"></a>Options, Éditeur de texte, XML, Mise en forme

Utilisez la page d’options **Mise en forme** pour spécifier la mise en forme des éléments et des attributs dans vos documents XML. Pour accéder aux options de mise en forme XML, choisissez **Outils**  >  **options**  >  **éditeur de texte**  >  **XML**, puis **mise en forme**.

## <a name="attributes"></a>Attributs

**Préserver la mise en forme manuelle des attributs**

Indique qu'il ne faut pas remettre en forme les attributs. Il s’agit du paramètre par défaut.

> [!NOTE]
> Si les attributs se trouvent sur plusieurs lignes, l'éditeur met en retrait chaque ligne d'attributs de façon à correspondre à la mise en retrait de l'élément parent.

**Aligner les attributs chacun sur une ligne séparée **

Aligne verticalement le deuxième attribut et les attributs suivants de façon à correspondre à la mise en retrait du premier attribut. Le texte XML suivant illustre la façon dont les attributs sont alignés :

```xml
<item id = "123-A"
      name = "hammer"
      price = "9.95">
</item>
```

## <a name="auto-reformat"></a>Remise en forme automatique

**Lors du collage à partir du presse-papiers**

Remet en forme le texte XML collé à partir du Presse-papiers.

**Après la balise de fin **

Remet en forme l'élément lorsque la balise de fin est insérée.

## <a name="mixed-content"></a>Contenu mixte

**Formater les contenus mixtes par défaut **

Tente de remettre en forme le contenu mixte, sauf lorsque celui-ci se trouve dans une étendue `xml:space="preserve"`. Il s’agit du paramètre par défaut.

Si un élément contient un mélange de texte et de balises, le contenu est considéré comme mixte. Voici un exemple de contenu mixte.

```xml
<dir>c:\data\AlphaProject\
  <file readOnly="false">test1.txt</file>
  <file readOnly="false">test2.txt</file>
</dir>
```

## <a name="see-also"></a>Voir aussi

- [Options XML - Divers](options-text-editor-xml-miscellaneous.md)
- [Outils XML dans Visual Studio](../../xml-tools/xml-tools-in-visual-studio.md)
