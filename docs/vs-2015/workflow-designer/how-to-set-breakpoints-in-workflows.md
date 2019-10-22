---
title: 'Comment : définir des points d’arrêt dans les flux de travail | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: e41b21c9-c061-4358-8e2f-eb5e412864a8
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2d1bbb18a9015b52b3d65cb8f8fd02674693abc0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659138"
---
# <a name="how-to-set-breakpoints-in-workflows"></a>Comment : définir des points d'arrêt dans les workflows
Lorsque vous utilisez [!INCLUDE[wfd1](../includes/wfd1-md.md)], vous pouvez définir des points d'arrêt sur vos workflows graphiques comme vous le feriez dans du code Visual Basic ou C#. Comme prévu, l'exécution de workflow s'arrête à chaque point d'arrêt que vous définissez.

 Un point d’arrêt a trois États : *en attente*, *lié*et *erreur*. Lorsque vous définissez un point d'arrêt, il a l'état En attente et est représenté par une icône rouge unie. Lorsque l'exécution a chargé le type de workflow, il adopte l'état Lié. Si vous spécifiez un format incorrect pour le point d'arrêt, par exemple en indiquant un nom d'activité non valide, un message d'erreur s'affiche. Le point d'arrêt est ajouté à la fenêtre de points d'arrêt, mais il est marqué d'un petit « x ».

> [!NOTE]
> La définition des points d'arrêt sur les workflows appelés n'est pas prise en charge.
>
> [!WARNING]
> Veillez à sélectionner l’option **activer la uniquement mon code (managé uniquement)** dans le menu **Outils**, **options**, **débogage** avant de procéder au débogage. Si vous avez deux séquences imbriquées dans une autre séquence et que vous définissez un point d’arrêt sur la première séquence interne, le fait d’appuyer sur **F11** ne débogue pas dans la deuxième séquence interne si l’option <strong>activer uniquement mon code (managé uniquement)</strong>n’est pas sélectionnée.
>
> [!WARNING]
> Les points d’arrêt dans un workflow ne sont pas atteints si le chemin d’accès complet à la propriété du fichier XAML n’est pas exact. Le chemin d’accès complet au fichier XAML n’est pas précis après avoir déplacé le projet ou la solution vers un autre dossier ou sur un autre ordinateur. Appuyez sur Ctrl+S pour enregistrer et mettre à jour la propriété de chemin complet.

### <a name="to-set-a-breakpoint-on-an-activity-in-the-design-view"></a>Pour définir un point d'arrêt sur une activité en mode Design

1. Sélectionnez l'activité sur laquelle vous voulez que le débogueur s'arrête.

2. Dans le menu **Déboguer** , sélectionnez **basculer le point d’arrêt**. Une icône rouge s'affiche dans l'angle supérieur gauche de l'activité.

     Vous pouvez également appuyer sur la touche de raccourci **F9** après avoir sélectionné l’activité, ou vous pouvez cliquer avec le bouton droit sur l’activité et sélectionner **point d’arrêt** , puis insérer un **point d’arrêt** dans le menu contextuel.

## <a name="see-also"></a>Voir aussi
 [Comment : appeler le](../workflow-designer/how-to-invoke-the-workflow-debugger.md) débogueur de workflow [débogage de flux de travail avec le concepteur de flux de travail](../workflow-designer/debugging-workflows-with-the-workflow-designer.md) [Comment : déboguer du code XAML avec l’Concepteur de flux de travail](../workflow-designer/how-to-debug-xaml-with-the-workflow-designer.md)