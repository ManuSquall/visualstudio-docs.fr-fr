---
title: 'Comment : définir des attributs CLR sur un élément'
description: Découvrez comment vous pouvez ajouter n’importe quel attribut qui hérite de la classe System. Attribute.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b11a6bd4a04bdb469cdf5c2fe2d7b78e0c0fe29a
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387331"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Comment : définir des attributs CLR sur un élément
Les attributs personnalisés sont des attributs spéciaux qui peuvent être ajoutés à des éléments de domaine, des formes, des connecteurs et des diagrammes. Vous pouvez ajouter n’importe quel attribut qui hérite de la `System.Attribute` classe.

### <a name="to-add-a-custom-attribute"></a>Pour ajouter un attribut personnalisé

1. Dans l' **Explorateur DSL**, sélectionnez l’élément auquel vous souhaitez ajouter un attribut personnalisé.

2. Dans la fenêtre **Propriétés** , en regard de la propriété **attributs personnalisés** , cliquez sur l’icône de navigation (**...**).

     La boîte de dialogue **modifier les attributs** s’ouvre.

3. Dans la colonne **nom** , cliquez sur **\<add attribute>** et tapez le nom de votre attribut. Appuyez sur Entrée.

4. La ligne sous le nom de l’attribut affiche des parenthèses. Sur cette ligne, tapez un type de paramètre pour l’attribut (par exemple, `string` ), puis appuyez sur entrée.

5. Dans la colonne nom de la **propriété** , tapez un nom approprié, par exemple, `MyString` .

6. Cliquez sur **OK**.

     La propriété **attributs personnalisés** affiche désormais l’attribut au format suivant :

     `[`*AttributeName* `(` *ParameterName* `=` *Type*`)]`

## <a name="see-also"></a>Voir aussi

- [Glossaire des Outils Domain-Specific Language](/previous-versions/bb126564(v=vs.100))