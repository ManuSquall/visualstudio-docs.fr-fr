---
title: "Guide pratique pour créer des associations entre les types (Concepteur de classes) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.classdesigner.associationline
helpviewer_keywords:
- types [Visual Studio], associations
- association lines, defining (Class Designer)
- defining association lines (Class Designer)
- associations, types
- association lines
ms.assetid: adccb9c8-2f8a-4086-9fa9-f70f99fb6e00
caps.latest.revision: 20
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 63aad78bdc7df685ca3a73ec16a9cbc87b78151f
ms.openlocfilehash: 81629535c7d6001ad1bbb59ca2b40da4cb252628
ms.contentlocale: fr-fr
ms.lasthandoff: 07/14/2017

---
# <a name="how-to-create-associations-between-types-class-designer"></a>Comment : créer des associations entre les types (Concepteur de classes)
Les lignes d'association du Concepteur de classes affichent la façon dont les classes d'un diagramme sont liées. Une ligne d'association représente une classe qui est le type d'une propriété ou d'un champ d'une autre classe de votre projet. Les lignes d'association sont en général utilisées pour illustrer les relations les plus importantes entre les classes de votre projet.  
  
 Même si vous pouvez afficher tous les champs et propriétés comme associations, il est plus raisonnable de n'afficher comme associations que les membres importants, en fonction des informations que vous voulez souligner dans le diagramme. (Vous pouvez afficher des membres moins importants comme membres normaux ou les masquer entièrement.)  
  
> [!NOTE]
>  Le Concepteur de classes prend uniquement en charge les associations unidirectionnelles.  
  
### <a name="to-define-an-association-line-in-the-class-diagram"></a>Pour définir une ligne d'association dans le Diagramme de classes  
  
1.  Dans la boîte à outils, sous Concepteur de classes, sélectionnez **Association**.  
  
2.  Tracez une ligne entre les deux formes que vous souhaitez relier par une association.  
  
     Une nouvelle propriété est créée dans la première classe. Cette propriété s'affiche comme ligne d'association (et non comme propriété d'un compartiment de la forme) avec un nom par défaut. Son type est la forme vers laquelle pointe la ligne d'association.  
  
### <a name="to-change-the-name-of-an-association"></a>Pour modifier le nom d'une association  
  
-   Sur la surface du diagramme, cliquez sur l'étiquette de la ligne d'association et modifiez-la.  
  
 \- ou -  
  
1.  Cliquez sur la forme qui contient la propriété indiquée comme association.  
  
     La forme obtient le focus et ses membres s'affichent dans la fenêtre Détails de classe et dans la fenêtre Propriétés.  
  
2.  Dans la fenêtre Détails de classe ou dans la fenêtre Propriétés, modifiez le nom du champ de cette propriété et appuyez sur Entrée.  
  
     Le nom est mis à jour dans la fenêtre **Détails de classe**, sur la ligne d’association, dans la fenêtre Propriétés et dans le code.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour changer la notation entre les membres et les associations (Concepteur de classes)](../ide/how-to-change-between-member-notation-and-association-notation-class-designer.md)
