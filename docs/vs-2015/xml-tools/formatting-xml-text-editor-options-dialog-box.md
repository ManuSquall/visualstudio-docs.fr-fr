---
title: Mise en forme, XML, éditeur de texte, boîte de dialogue Options | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb539b3a-027c-4b2f-906e-403e0e22ba8d
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 352a43cbe16540f1b231077bb1b7c23dd45ffcec
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47493426"
---
# <a name="formatting-xml-text-editor-options-dialog-box"></a>Mise en forme, XML, Éditeur de texte, boîte de dialogue Options
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [mise en forme, XML, éditeur de texte, boîte de dialogue Options](https://docs.microsoft.com/visualstudio/xml-tools/formatting-xml-text-editor-options-dialog-box).  
  
  
Cette boîte de dialogue permet de spécifier les paramètres de mise en forme de l'éditeur XML. Vous pouvez accéder à la **Options** boîte de dialogue à partir de la **outils** menu.  
  
> [!NOTE]
>  Ces paramètres sont disponibles lorsque vous sélectionnez le **éditeur de texte** dossier, le **XML** dossier, puis le **mise en forme** option à partir de la **Options** boîte de dialogue.  
  
## <a name="attributes"></a>Attributs  
 **Conserver la mise en forme manuelle des attributs**  
 Les attributs ne sont pas remis en forme. Il s'agit de la valeur par défaut.  
  
> [!NOTE]
>  Si les attributs figurent sur plusieurs lignes, l'éditeur met en retrait chaque ligne d'attributs au niveau d'indentation de l'élément parent.  
  
 **Aligne chaque attribut sur leur propre ligne**  
 À partir du deuxième attribut, aligne les attributs verticalement au niveau d'indentation du premier attribut. Le texte XML qui suivant illustre la façon dont les attributs sont alignés.  
  
```  
<item id = "123-A"  
      name = "hammer"  
      price = "9.95">  
</item>  
```  
  
## <a name="auto-reformat"></a>Remise en forme automatique  
 **Lors du collage à partir du Presse-papiers**  
 Remet en forme le texte XML collé à partir du Presse-papiers.  
  
 **Sur la balise de fin**  
 Remet l’élément en forme après l’étiquette de fin.  
  
## <a name="mixed-content"></a>Contenu mixte  
 **Conserve le contenu mixte par défaut**  
 Détermine si l'éditeur remet en forme un contenu mixte. Par défaut, l'éditeur tente de remettre en forme le contenu mixte, sauf lorsque celui-ci se trouve dans une portée `xml:space="preserve"`.  
  
 Si un élément contient un mélange de texte et de balises, ce contenu est considéré comme mixte. Voici un exemple d'élément avec un contenu mixte.  
  
```  
<dir>c:\data\AlphaProject\  
  <file readOnly="false">test1.txt</file>  
  <file readOnly="false">test2.txt</file>  
</dir>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés des documents XML, fenêtre Propriétés](../xml-tools/xml-document-properties-properties-window.md)   
 [Composants de l’éditeur XML](../xml-tools/xml-editor-components.md)



