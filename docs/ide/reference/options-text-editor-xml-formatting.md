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
ms.openlocfilehash: 8452410235226b3d7a1446d7a8c5a2ee709eff6e
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55943543"
---
# <a name="options-text-editor-xml-formatting"></a>Options, Éditeur de texte, XML, Mise en forme

Utilisez la page de propriétés **Mise en forme** pour spécifier la mise en forme des éléments et des attributs dans vos documents XML. Pour ouvrir la boîte de dialogue **Options**, cliquez sur le menu **Outils**, puis sur **Options**. Pour accéder à la page de propriétés **Mise en forme**, développez le nœud **Éditeur de texte** > **XML** > **Mise en forme**.

## <a name="attributes"></a>Attributs

**Préserver la mise en forme manuelle des attributs**

Ne remet pas en forme les attributs. Il s’agit du paramétrage par défaut.

> [!NOTE]
> Si les attributs figurent sur plusieurs lignes, l'éditeur met en retrait chaque ligne d'attributs au niveau d'indentation de l'élément parent.

**Aligner les attributs chacun sur une ligne séparée**

À partir du deuxième attribut, aligne les attributs verticalement au niveau d’indentation du premier attribut. Le texte XML qui suivant illustre la façon dont les attributs sont alignés.

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

- [Guide pratique pour créer une documentation XML (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)
- [Génération de code](../code-generation-in-visual-studio.md)