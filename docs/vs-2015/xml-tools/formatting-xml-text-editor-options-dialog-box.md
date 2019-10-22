---
title: Mise en forme, XML, éditeur de texte, boîte de dialogue Options | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: bb539b3a-027c-4b2f-906e-403e0e22ba8d
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 962321a1ab1a1ca5332300eea0d21781a9e4bbf5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670969"
---
# <a name="formatting-xml-text-editor-options-dialog-box"></a>Mise en forme, XML, Éditeur de texte, boîte de dialogue Options
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette boîte de dialogue permet de spécifier les paramètres de mise en forme de l'éditeur XML. Vous pouvez accéder à la boîte de dialogue **options** à partir du menu **Outils** .

> [!NOTE]
> Ces paramètres sont disponibles lorsque vous sélectionnez le **dossier Éditeur de texte** , le dossier **XML** , puis l’option **mise en forme** dans la boîte de dialogue **options** .

## <a name="attributes"></a>Attributs
 **Conserver la mise en forme manuelle des attributs** Les attributs ne sont pas reformatés. Il s'agit de la valeur par défaut.

> [!NOTE]
> Si les attributs figurent sur plusieurs lignes, l'éditeur met en retrait chaque ligne d'attributs au niveau d'indentation de l'élément parent.

 **Aligner les attributs chacun sur leur propre ligne** Aligne verticalement le deuxième attribut et les attributs suivants pour qu’ils correspondent à la mise en retrait du premier attribut. Le texte XML qui suivant illustre la façon dont les attributs sont alignés.

```
<item id = "123-A"
      name = "hammer"
      price = "9.95">
</item>
```

## <a name="auto-reformat"></a>Remise en forme automatique
 **Lors du collage à partir du presse-papiers** Reformate le texte XML collé à partir du presse-papiers.

 **Après l’achèvement de la balise de fin** Reformate l’élément lorsque la balise de fin est terminée.

## <a name="mixed-content"></a>Contenu mixte
 **Conserver le contenu mixte par défaut** Détermine si l’éditeur reformate le contenu mixte. Par défaut, l'éditeur tente de remettre en forme le contenu mixte, sauf lorsque celui-ci se trouve dans une portée `xml:space="preserve"`.

 Si un élément contient un mélange de texte et de balises, ce contenu est considéré comme mixte. Voici un exemple d'élément avec un contenu mixte.

```
<dir>c:\data\AlphaProject\
  <file readOnly="false">test1.txt</file>
  <file readOnly="false">test2.txt</file>
</dir>
```

## <a name="see-also"></a>Voir aussi
 [Propriétés de document XML, fenêtre Propriétés composants de](../xml-tools/xml-document-properties-properties-window.md) l' [éditeur XML](../xml-tools/xml-editor-components.md)
