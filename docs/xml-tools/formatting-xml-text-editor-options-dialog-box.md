---
title: "Mise en forme, XML, &#201;diteur de texte, bo&#238;te de dialogue Options | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bb539b3a-027c-4b2f-906e-403e0e22ba8d
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Mise en forme, XML, &#201;diteur de texte, bo&#238;te de dialogue Options
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette boîte de dialogue permet de spécifier les paramètres de mise en forme de l'éditeur XML.Vous pouvez accéder à la boîte de dialogue **Options** à partir du menu **Outils**.  
  
> [!NOTE]
>  Ces paramètres ne sont disponibles que lorsque vous sélectionnez le dossier **Éditeur de texte**, le dossier **XML**, puis l'option **Mise en forme** dans la boîte de dialogue **Options**.  
  
## Attributs  
 **Conserve la mise en forme manuelle des attributs**  
 Les attributs ne sont pas remis en forme.Il s'agit de la valeur par défaut.  
  
> [!NOTE]
>  Si les attributs figurent sur plusieurs lignes, l'éditeur met en retrait chaque ligne d'attributs au niveau d'indentation de l'élément parent.  
  
 **Aligne chaque attribut sur une ligne séparée**  
 À partir du deuxième attribut, aligne les attributs verticalement au niveau d'indentation du premier attribut.Le texte XML qui suivant illustre la façon dont les attributs sont alignés.  
  
```  
<item id = "123-A"  
      name = "hammer"  
      price = "9.95">  
</item>  
```  
  
## Remise en forme automatique  
 **En collant le contenu du Presse\-papiers**  
 Remet en forme le texte XML collé à partir du Presse\-papiers.  
  
 **Après la balise de fin**  
 Remet l'élément en forme après la balise de fin.  
  
## Contenu mixte  
 **Conserve le contenu mixte par défaut**  
 Détermine si l'éditeur remet en forme un contenu mixte.Par défaut, l'éditeur tente de remettre en forme le contenu mixte, sauf lorsque celui\-ci se trouve dans une portée `xml:space="preserve"`.  
  
 Si un élément contient un mélange de texte et de balises, ce contenu est considéré comme mixte.Voici un exemple d'élément avec un contenu mixte.  
  
```  
<dir>c:\data\AlphaProject\  
  <file readOnly="false">test1.txt</file>  
  <file readOnly="false">test2.txt</file>  
</dir>  
```  
  
## Voir aussi  
 [Propriétés des documents XML, fenêtre Propriétés](../xml-tools/xml-document-properties-properties-window.md)   
 [Composants de l'éditeur XML](../xml-tools/xml-editor-components.md)