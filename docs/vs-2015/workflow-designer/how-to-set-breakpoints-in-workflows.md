---
title: 'Procédure : Définir des points d’arrêt dans les Workflows | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: e41b21c9-c061-4358-8e2f-eb5e412864a8
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2aaf61ada4167f29f1c6d4754ced7c9757054a88
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58953926"
---
# <a name="how-to-set-breakpoints-in-workflows"></a>Procédure : Définir des points d’arrêt dans les workflows
Lorsque vous utilisez [!INCLUDE[wfd1](../includes/wfd1-md.md)], vous pouvez définir des points d'arrêt sur vos workflows graphiques comme vous le feriez dans du code Visual Basic ou C#. Comme prévu, l'exécution de workflow s'arrête à chaque point d'arrêt que vous définissez.  
  
 Un point d’arrêt a trois états : *En attente*, *lié*, et *erreur*. Lorsque vous définissez un point d'arrêt, il a l'état En attente et est représenté par une icône rouge unie. Lorsque l'exécution a chargé le type de workflow, il adopte l'état Lié. Si vous spécifiez un format incorrect pour le point d'arrêt, par exemple en indiquant un nom d'activité non valide, un message d'erreur s'affiche. Le point d'arrêt est ajouté à la fenêtre de points d'arrêt, mais il est marqué d'un petit « x ».  
  
> [!NOTE]
>  La définition des points d'arrêt sur les workflows appelés n'est pas prise en charge.  
> 
> [!WARNING]
>  Vérifiez que vous sélectionnez l’option **activer uniquement mon Code (managé uniquement)** à partir de la **outils**, **Options**, **débogage** menu avant déboguer. Si vous avez deux séquences sont imbriquées dans une autre séquence et vous définissez un point d’arrêt sur la première séquence interne, en appuyant sur **F11** ne sera pas déboguer dans la deuxième séquence interne si la <strong>activer uniquement mon Code (managé uniquement)</strong>option n’est pas sélectionnée.  
> 
> [!WARNING]
>  Les points d’arrêt dans un workflow ne sont pas atteints si le chemin d’accès complet à la propriété du fichier XAML n’est pas exact. Le chemin d’accès complet au fichier XAML n’est pas précis après avoir déplacé le projet ou la solution vers un autre dossier ou sur un autre ordinateur. Appuyez sur Ctrl+S pour enregistrer et mettre à jour la propriété de chemin complet.  
  
### <a name="to-set-a-breakpoint-on-an-activity-in-the-design-view"></a>Pour définir un point d'arrêt sur une activité en mode Design  
  
1.  Sélectionnez l'activité sur laquelle vous voulez que le débogueur s'arrête.  
  
2.  Sur le **déboguer** menu, sélectionnez **point d’arrêt**. Une icône rouge s'affiche dans l'angle supérieur gauche de l'activité.  
  
     Ou bien, vous pouvez également appuyer sur le raccourci **F9** après la sélection de l’activité, ou vous pouvez avec le bouton droit de l’activité et sélectionner **point d’arrêt** puis **Insert point d’arrêt**dans le menu contextuel.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour Appelez le débogueur de flux de travail](../workflow-designer/how-to-invoke-the-workflow-debugger.md)   
 [Débogage de Workflows avec Workflow Designer](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)   
 [Guide pratique pour déboguer du code XAML à l’aide du concepteur de workflow](../workflow-designer/how-to-debug-xaml-with-the-workflow-designer.md)