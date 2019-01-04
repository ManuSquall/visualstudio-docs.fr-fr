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
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 5b9a96f70febc6a33d80557a09cc8bc8e1adf2f4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53938080"
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

- [Glossaire des outils Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)