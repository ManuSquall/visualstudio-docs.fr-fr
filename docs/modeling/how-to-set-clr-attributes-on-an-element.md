---
title: "Comment : définir des attributs CLR sur un élément | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
ms.assetid: b3db3c74-920c-4701-9544-6f75cbe8b7c9
caps.latest.revision: 19
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 7dcbd0005b80887dae91249a6781a6982414b9e5
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Comment : définir des attributs CLR sur un élément
Les attributs personnalisés sont des attributs spéciaux qui peuvent être ajoutés à des diagrammes, les formes, les connecteurs et les éléments du domaine. Vous pouvez ajouter n’importe quel attribut qui hérite de la `System.Attribute` classe.  
  
### <a name="to-add-a-custom-attribute"></a>Pour ajouter un attribut personnalisé  
  
1.  Dans le **Explorateur DSL**, sélectionnez l’élément auquel vous souhaitez ajouter un attribut personnalisé.  
  
2.  Dans le **propriétés** fenêtre, en regard du **attributs personnalisés** propriété, cliquez sur le bouton de navigation (**... **) icon.  
  
     Le **modifier les attributs** boîte de dialogue s’ouvre.  
  
3.  Dans le **nom** colonne, cliquez sur ** \<Ajouter attribut >** et tapez le nom de votre attribut. Appuyez sur Entrée.  
  
4.  La ligne sous le nom d’attribut indique entre parenthèses. Sur cette ligne, tapez un type de paramètre pour l’attribut (par exemple, `string`), puis appuyez sur ENTRÉE.  
  
5.  Dans le **nom de propriété** colonne, tapez un nom approprié, par exemple, `MyString`.  
  
6.  Cliquez sur **OK**.  
  
     Le **des attributs personnalisés** propriété affiche désormais l’attribut dans le format suivant :  
  
     `[`*AttributeName* `(` *ParameterName* `=` *Type*`)]`  
  
## <a name="see-also"></a>Voir aussi  
 [Glossaire des outils Domain-Specific Language](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)
