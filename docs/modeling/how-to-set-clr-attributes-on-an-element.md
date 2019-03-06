---
title: 'Procédure : Définir des attributs CLR sur un élément'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b890a5d3d5c48ad3841075a8ae818d2d37d44f98
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55946624"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Procédure : Définir des attributs CLR sur un élément
Les attributs personnalisés sont des attributs spéciaux qui peuvent être ajoutés à des diagrammes, des formes, des connecteurs et des éléments de domaine. Vous pouvez ajouter n’importe quel attribut qui hérite de la `System.Attribute` classe.

### <a name="to-add-a-custom-attribute"></a>Pour ajouter un attribut personnalisé

1.  Dans le **Explorateur DSL**, sélectionnez l’élément auquel vous souhaitez ajouter un attribut personnalisé.

2.  Dans le **propriétés** fenêtre, en regard du **attributs personnalisés** propriété, cliquez sur le bouton de navigation (**...** ) icône.

     Le **modifier les attributs** boîte de dialogue s’ouvre.

3.  Dans le **nom** colonne, cliquez sur  **\<ajouter un attribut >** et tapez le nom de votre attribut. Appuyez sur Entrée.

4.  La ligne sous le nom d’attribut affiche entre parenthèses. Sur cette ligne, tapez un type de paramètre pour l’attribut (par exemple, `string`), puis appuyez sur ENTRÉE.

5.  Dans le **nom de propriété** colonne, tapez un nom approprié, par exemple, `MyString`.

6.  Cliquez sur **OK**.

     Le **attributs personnalisés** propriété affiche désormais l’attribut dans le format suivant :

     `[` *AttributeName* `(` *ParameterName* `=` *Type* `)]`

## <a name="see-also"></a>Voir aussi

- [Glossaire des Outils Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)