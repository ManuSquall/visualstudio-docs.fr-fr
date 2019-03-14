---
title: Options, Éditeur de texte, XML, Mise en forme
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Formatting
ms.assetid: 203e60b2-7b80-4ff4-9fa1-aa9f4374377b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e20b2f7ebe351aa050ea66468fb33aba8e4a31bc
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57525067"
---
# <a name="options-text-editor-xml-formatting"></a>Options, Éditeur de texte, XML, Mise en forme

Utilisez la page d’options **Mise en forme** pour spécifier la mise en forme des éléments et des attributs dans vos documents XML. Pour accéder aux options de mise en forme XML, choisissez **Outils** > **Options** > **Éditeur de texte** > **XML**, puis **Mise en forme**.

## <a name="attributes"></a>Attributs

**Préserver la mise en forme manuelle des attributs**

Ne remet pas en forme les attributs. Il s’agit du paramétrage par défaut.

> [!NOTE]
> Si les attributs figurent sur plusieurs lignes, l'éditeur met en retrait chaque ligne d'attributs au niveau d'indentation de l'élément parent.

**Aligner les attributs chacun sur une ligne séparée**

À partir du deuxième attribut, aligne les attributs verticalement au niveau d’indentation du premier attribut. Le texte XML suivant illustre la façon dont les attributs sont alignés :

```xml
<item id = "123-A"
      name = "hammer"
      price = "9.95">
</item>
```

## <a name="auto-reformat"></a>Remise en forme automatique

**En collant le contenu du presse-papiers**

Remet en forme le texte XML collé à partir du Presse-papiers.

**Après la balise de fin**

Remet l’élément en forme une fois la balise de fin complétée.

## <a name="mixed-content"></a>Contenu mixte

**Mettre en forme les contenus mixtes par défaut**

Tente de remettre en forme le contenu mixte, sauf lorsque celui-ci se trouve dans une étendue `xml:space="preserve"`. Il s’agit du paramétrage par défaut.

Si un élément contient un mélange de texte et de balises, ce contenu est considéré comme mixte. Voici un exemple d’élément avec un contenu mixte.

```xml
<dir>c:\data\AlphaProject\
  <file readOnly="false">test1.txt</file>
  <file readOnly="false">test2.txt</file>
</dir>
```

## <a name="see-also"></a>Voir aussi

- [Options XML - Divers](options-text-editor-xml-miscellaneous.md)
- [Outils XML dans Visual Studio](../../xml-tools/xml-tools-in-visual-studio.md)