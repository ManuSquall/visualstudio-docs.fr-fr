---
title: "Mise en forme, XML, éditeur de texte, boîte de dialogue Options | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb539b3a-027c-4b2f-906e-403e0e22ba8d
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9a4d6de24a75b5a08820878bc74633c02ab4118f
ms.sourcegitcommit: 5f436413bbb1e8aa18231eb5af210e7595401aa6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="formatting-xml-text-editor-options-dialog-box"></a>Mise en forme, XML, Éditeur de texte, boîte de dialogue Options
Cette boîte de dialogue permet de spécifier les paramètres de mise en forme de l'éditeur XML. Vous pouvez accéder à la **Options** boîte de dialogue à partir de la **outils** menu.  
  
> [!NOTE]
>  Ces paramètres sont disponibles lorsque vous sélectionnez le **éditeur de texte** dossier, le **XML** dossier, puis le **mise en forme** option à partir de la **Options** boîte de dialogue.  
  
## <a name="attributes"></a>Attributs  
 **Conserver la mise en forme manuelle des attributs**  
 Les attributs ne sont pas remis en forme. Il s'agit de la valeur par défaut.  
  
> [!NOTE]
>  Si les attributs figurent sur plusieurs lignes, l'éditeur met en retrait chaque ligne d'attributs au niveau d'indentation de l'élément parent.  
  
 **Aligner les attributs chacun sur leur propre ligne.**  
 À partir du deuxième attribut, aligne les attributs verticalement au niveau d'indentation du premier attribut. Le texte XML qui suivant illustre la façon dont les attributs sont alignés.  
  
```xml
<item id = "123-A"  
      name = "hammer"  
      price = "9.95">  
</item>  
```
  
## <a name="auto-reformat"></a>Remise en forme automatique  
 **Lors du collage à partir du Presse-papiers**  
 Remet en forme le texte XML collé à partir du Presse-papiers.  
  
 **À la fin de la balise de fin**  
 Remet l’élément en forme après l’étiquette de fin.  
  
## <a name="mixed-content"></a>Contenu mixte  
 **Conserve le contenu mixte par défaut**  
 Détermine si l'éditeur remet en forme un contenu mixte. Par défaut, l'éditeur tente de remettre en forme le contenu mixte, sauf lorsque celui-ci se trouve dans une portée `xml:space="preserve"`.  
  
 Si un élément contient un mélange de texte et de balises, ce contenu est considéré comme mixte. Voici un exemple d'élément avec un contenu mixte.  
  
```xml
<dir>c:\data\AlphaProject\  
  <file readOnly="false">test1.txt</file>  
  <file readOnly="false">test2.txt</file>  
</dir>  
```
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés des documents XML, fenêtre Propriétés](../xml-tools/xml-document-properties-properties-window.md)   
 [Composants de l’éditeur XML](../xml-tools/xml-editor-components.md)