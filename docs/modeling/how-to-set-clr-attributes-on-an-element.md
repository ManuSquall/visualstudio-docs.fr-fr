---
title: 'Comment : définir des attributs CLR sur un élément'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f943f9713e4432f0b06242a2f66acae6b390e5cc
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748366"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Comment : définir des attributs CLR sur un élément
Les attributs personnalisés sont des attributs spéciaux qui peuvent être ajoutés à des éléments de domaine, des formes, des connecteurs et des diagrammes. Vous pouvez ajouter n’importe quel attribut qui hérite de la classe `System.Attribute`.

### <a name="to-add-a-custom-attribute"></a>Pour ajouter un attribut personnalisé

1. Dans l' **Explorateur DSL**, sélectionnez l’élément auquel vous souhaitez ajouter un attribut personnalisé.

2. Dans la fenêtre **Propriétés** , en regard de la propriété **attributs personnalisés** , cliquez sur l’icône de navigation ( **...** ).

     La boîte de dialogue **modifier les attributs** s’ouvre.

3. Dans la colonne **nom** , cliquez sur **\<add attribut >** et tapez le nom de votre attribut. Appuyez sur Entrée.

4. La ligne sous le nom de l’attribut affiche des parenthèses. Sur cette ligne, tapez un type de paramètre pour l’attribut (par exemple, `string`), puis appuyez sur entrée.

5. Dans la colonne nom de la **propriété** , tapez un nom approprié, par exemple, `MyString`.

6. Cliquez sur **OK**.

     La propriété **attributs personnalisés** affiche désormais l’attribut au format suivant :

     `[` *AttributeName* `(` *ParameterName* `=` *type* `)]`

## <a name="see-also"></a>Voir aussi

- [Glossaire des Outils Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)