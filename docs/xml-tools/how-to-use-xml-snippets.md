---
title: "Proc&#233;dure&#160;: utiliser des extraits XML | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3a27375b-81cc-48f6-a884-e1cb8c4f78f5
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Proc&#233;dure&#160;: utiliser des extraits XML
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez invoquer des extraits XML en utilisant les deux commandes suivantes du menu contextuel de l'éditeur XML.La commande **Insérer un extrait** insère l'extrait XML à l'emplacement du curseur.La commande **Entourer de** insère l'extrait XML de part et d'autre du texte sélectionné.Chaque extrait XML possède des types d'extrait désignés.Le type d'extrait détermine si cet extrait est disponible avec la commande **Insérer un extrait** et\/ou la commande **Entourer de**.  
  
 Une fois l'extrait XML ajouté à l'éditeur, tous ses champs modifiables sont surlignés en jaune et le curseur est placé dans le premier d'entre eux.  
  
## Insérer un extrait  
 Les procédures suivantes expliquent comment accéder à la commande **Insérer un extrait**.  
  
> [!NOTE]
>  La commande **Insérer un extrait** est également accessible via un raccourci clavier \(CTRL\+K, puis CTRL\+X\).  
  
#### Pour insérer des extraits à partir du menu contextuel  
  
1.  Placez le curseur à l'endroit où vous souhaitez insérer l'extrait XML.  
  
2.  Cliquez avec le bouton droit et sélectionnez **Insérer un extrait**.  
  
     Une liste des extraits XML disponibles s'affiche.  
  
3.  Sélectionnez un extrait dans la liste à l'aide de la souris ou en entrant son nom et en appuyant sur TAB ou ENTRÉE.  
  
#### Pour insérer des extraits à l'aide du menu IntelliSense  
  
1.  Placez le curseur à l'endroit où vous souhaitez insérer l'extrait XML.  
  
2.  Dans le menu **Edition**, pointez sur **IntelliSense**, puis sélectionnez **Insérer un extrait**.  
  
     Une liste des extraits XML disponibles s'affiche.  
  
3.  Sélectionnez un extrait dans la liste à l'aide de la souris ou en entrant son nom et en appuyant sur TAB ou ENTRÉE.  
  
#### Pour insérer des extraits via la liste de remplissage IntelliSense  
  
1.  Placez le curseur à l'endroit où vous souhaitez insérer l'extrait XML.  
  
2.  Commencez à entrer l'extrait XML à ajouter à votre fichier.Si le remplissage automatique est activé, la liste de remplissage IntelliSense s'affiche.Dans le cas contraire, appuyez sur CTRL\+ESPACE pour l'activer.  
  
3.  Sélectionnez l'extrait XML dans la liste de remplissage.  
  
4.  Appuyez sur TAB à deux reprises pour invoquer l'extrait XML.  
  
> [!NOTE]
>  Parfois, l'extrait XML n'est pas invoqué.Par exemple, si vous tentez d'insérer un élément `xs:complexType` dans un nœud `xs:element`, l'éditeur ne génère aucun extrait XML.En effet, lorsqu'un élément `xs:complexType` est utilisé à l'intérieur d'un nœud `xs:element`, aucun attribut ni sous\-élément n'est requis, de sorte que l'éditeur n'a aucune donnée à insérer.  
  
#### Pour insérer des extraits à l'aide du nom raccourci  
  
1.  Placez le curseur à l'endroit où vous souhaitez insérer l'extrait XML.  
  
2.  Entrez `<` dans le volet de l'éditeur.  
  
3.  Appuyez sur ÉCHAP pour fermer la liste de remplissage IntelliSense.  
  
4.  Entrez le nom raccourci de l'extrait XML, puis appuyez sur TAB pour l'invoquer.  
  
## Entourer de  
 Les procédures suivantes expliquent comment accéder à la commande **Entourer de**.  
  
> [!NOTE]
>  La commande **Entourer de** est également accessible via un raccourci clavier \(CTRL\+K, puis CTRL\+S\).  
  
#### Pour utiliser la commande Entourer de du menu contextuel  
  
1.  Sélectionnez le texte à entourer dans l'éditeur XML.  
  
2.  Cliquez avec le bouton droit et sélectionnez **Entourer de**.  
  
     Une liste des encadrements d'extraits XML disponibles s'affiche.  
  
3.  Sélectionnez un extrait dans la liste à l'aide de la souris ou en entrant son nom et en appuyant sur TAB ou ENTRÉE.  
  
#### Pour utiliser un encadrement à partir du menu Intellisense  
  
1.  Sélectionnez le texte à entourer dans l'éditeur XML.  
  
2.  Dans le menu **Edition**, pointez sur **IntelliSense**, puis sélectionnez **Entourer de**.  
  
     Une liste des encadrements d'extraits XML disponibles s'affiche.  
  
3.  Sélectionnez un extrait dans la liste à l'aide de la souris ou en entrant son nom et en appuyant sur TAB ou ENTRÉE.  
  
## Utilisation d'extraits XML  
 Une fois que vous avez choisi un extrait XML, le texte de cet extrait de code est automatiquement inséré à l'emplacement du curseur.Tous les champs modifiables contenus dans l'extrait sont surlignés et le premier de ces champs est automatiquement sélectionné.Le champ actuellement sélectionné est encadré.  
  
 Après avoir sélectionné un champ, vous pouvez y entrer une nouvelle valeur.La touche TAB permet de parcourir en boucle les champs modifiables de l'extrait ; les touches MAJ\+TAB effectuent le même parcours dans l'ordre inverse.Cliquer dans un champ place le curseur dans ce champ ; double\-cliquer sur un champ permet de le sélectionner.Lorsqu'un champ est en évidence, une info\-bulle peut s'afficher pour le décrire.  
  
 Seule la première instance d'un champ donné est modifiable.Lorsque ce champ est surligné, les autres instances du même champ sont mises en évidence.Lorsque vous modifiez la valeur d'un champ modifiable, ce champ change partout où il est utilisé dans l'extrait.  
  
 Appuyez sur ENTRÉE ou sur ÉCHAP pour annuler la modification du champ et revenir au mode normal de l'éditeur.  
  
 Vous pouvez personnaliser les couleurs par défaut des champs modifiables de l'extrait de code en modifiant le paramètre du champ Extrait de code dans le volet **Polices et couleurs** de la boîte de dialogue **Options**.Pour plus d'informations, consultez [Comment : modifier les polices et les couleurs utilisées dans l'Éditeur](../Topic/How%20to:%20Change%20Fonts%20and%20Colors%20in%20the%20Editor.md).  
  
## Voir aussi  
 [Extraits XML](../xml-tools/xml-snippets.md)   
 [Procédure : générer un extrait XML à partir d'un schéma XML](../Topic/How%20to:%20Generate%20an%20XML%20Snippet%20From%20an%20XML%20Schema.md)   
 [Procédure : créer des extraits XML](../xml-tools/how-to-create-xml-snippets.md)