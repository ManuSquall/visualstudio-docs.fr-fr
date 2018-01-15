---
title: "Comment : définir des attributs CLR sur un élément | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.dsltools.EditAttributesDialog
helpviewer_keywords: Domain-Specific Language, custom attrributes
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 91f1143e593ae63d41e15beb74612f192ec736d1
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2018
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Comment : définir des attributs CLR sur un élément
Les attributs personnalisés sont des attributs spéciaux qui peuvent être ajoutés à des diagrammes, des formes, des connecteurs et des éléments de domaine. Vous pouvez ajouter tout attribut qui hérite de la `System.Attribute` classe.  
  
### <a name="to-add-a-custom-attribute"></a>Pour ajouter un attribut personnalisé  
  
1.  Dans le **Explorateur DSL**, sélectionnez l’élément auquel vous souhaitez ajouter un attribut personnalisé.  
  
2.  Dans le **propriétés** fenêtre, en regard du **attributs personnalisés** propriété, cliquez sur le bouton de navigation (**...** ) icône.  
  
     Le **modifier les attributs** boîte de dialogue s’ouvre.  
  
3.  Dans le **nom** colonne, cliquez sur  **\<ajouter un attribut >** et tapez le nom de votre attribut. Appuyez sur Entrée.  
  
4.  La ligne sous le nom d’attribut affiche entre parenthèses. Sur cette ligne, tapez un type de paramètre pour l’attribut (par exemple, `string`), puis appuyez sur ENTRÉE.  
  
5.  Dans le **nom de propriété** colonne, tapez un nom approprié, par exemple, `MyString`.  
  
6.  Cliquez sur **OK**.  
  
     Le **attributs personnalisés** propriété affiche désormais l’attribut dans le format suivant :  
  
     `[`*AttributeName* `(` *nom_paramètre* `=` *Type*`)]`  
  
## <a name="see-also"></a>Voir aussi  
 [Glossaire des outils de langage spécifique à un domaine](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)