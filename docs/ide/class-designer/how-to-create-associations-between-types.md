---
title: 'Comment : créer des associations entre les types (Concepteur de classes)'
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.classdesigner.associationline
helpviewer_keywords:
- types [Visual Studio], associations
- association lines, defining (Class Designer)
- defining association lines (Class Designer)
- associations, types
- association lines
ms.assetid: adccb9c8-2f8a-4086-9fa9-f70f99fb6e00
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3cce893efaad5f2317b175391a2685cae7053e3c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85770953"
---
# <a name="how-to-create-associations-between-types-in-class-designer"></a>Guide pratique pour créer des associations entre les types dans le Concepteur de classes

Les lignes d’association dans **Concepteur de classes** montrent comment les classes d’un diagramme sont liées. Une ligne d'association représente une classe qui est le type d'une propriété ou d'un champ d'une autre classe de votre projet. Les lignes d'association sont en général utilisées pour illustrer les relations les plus importantes entre les classes de votre projet.

Même si vous pouvez afficher tous les champs et propriétés comme associations, il est plus raisonnable de n'afficher comme associations que les membres importants, en fonction des informations que vous voulez souligner dans le diagramme. (Vous pouvez afficher des membres moins importants comme membres normaux ou les masquer entièrement.)

> [!NOTE]
> **Concepteur de classes** prend en charge uniquement les associations unidirectionnelles.

## <a name="to-define-an-association-line-in-the-class-diagram"></a>Pour définir une ligne d'association dans le Diagramme de classes

1. Dans la boîte à outils, sous **Concepteur de classes**, sélectionnez **Association**.

2. Tracez une ligne entre les deux formes que vous souhaitez relier par une association.

     Une nouvelle propriété est créée dans la première classe. Cette propriété s'affiche comme ligne d'association (et non comme propriété d'un compartiment de la forme) avec un nom par défaut. Son type est la forme vers laquelle pointe la ligne d'association.

## <a name="to-change-the-name-of-an-association"></a>Pour modifier le nom d'une association

Sur la surface du diagramme, cliquez sur l'étiquette de la ligne d'association et modifiez-la.

Vous pouvez également effectuer les étapes suivantes :

1. Sélectionnez la forme qui contient la propriété indiquée comme association.

   La forme obtient le focus et ses membres s’affichent dans les fenêtres **Détails de classe** et **Propriétés**.

2. Dans la fenêtre **Détails de classe** ou **Propriétés**, modifiez le champ de nom de cette propriété et appuyez sur **Entrée**.

   Le nom est mis à jour dans la fenêtre **Détails de classe** , sur la ligne d’association, dans la fenêtre **Propriétés** et dans le code.

## <a name="see-also"></a>Voir aussi

- [Comment : changer la notation entre les membres et les associations](how-to-change-between-member-notation-and-association-notation.md)
