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
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: df9f8b16edcbe575ebac67f4acde9111a9511b85
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363846"
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