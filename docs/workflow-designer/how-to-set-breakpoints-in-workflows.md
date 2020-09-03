---
title: 'Concepteur de flux de travail : définir des points d’arrêt dans les workflows'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: e41b21c9-c061-4358-8e2f-eb5e412864a8
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9530e7ec018a89c3648f61660a5651eddaace805
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85817487"
---
# <a name="how-to-set-breakpoints-in-workflows"></a>Comment : définir des points d’arrêt dans les workflows

Lorsque vous utilisez Concepteur de flux de travail, vous pouvez définir des points d’arrêt sur vos flux de travail graphiques comme vous le feriez dans du code Visual Basic ou C#. Comme prévu, l'exécution de workflow s'arrête à chaque point d'arrêt que vous définissez.

Un point d’arrêt a trois États : *en attente*, *lié*et *erreur*. Lorsque vous définissez un point d'arrêt, il a l'état En attente et est représenté par une icône rouge unie. Lorsque l'exécution a chargé le type de workflow, il adopte l'état Lié. Si vous spécifiez un format incorrect pour le point d'arrêt, par exemple en indiquant un nom d'activité non valide, un message d'erreur s'affiche. Le point d'arrêt est ajouté à la fenêtre de points d'arrêt, mais il est marqué d'un petit « x ».

> [!NOTE]
> La définition des points d'arrêt sur les workflows appelés n'est pas prise en charge.

> [!NOTE]
> Veillez à sélectionner l’option **activer uniquement mon code (managé uniquement)** à partir du menu **Outils**  >  **options**de  >  **débogage** avant de procéder au débogage. Si l’option n’est pas sélectionnée et que vous avez deux séquences imbriquées dans une autre séquence et que vous définissez un point d’arrêt sur la première séquence interne, le fait d’appuyer sur **F11** ne débogue pas dans la deuxième séquence interne.

> [!NOTE]
> Les points d’arrêt dans un workflow ne sont pas atteints si le chemin d’accès complet à la propriété du fichier XAML n’est pas exact. Le chemin d’accès complet au fichier XAML n’est pas exact après le déplacement du projet ou de la solution vers un autre dossier ou vers un autre ordinateur. Sélectionnez **CTRL** + **S** pour enregistrer et mettre à jour la propriété chemin d’accès complet.

## <a name="to-set-a-breakpoint-on-an-activity-in-the-design-view"></a>Pour définir un point d'arrêt sur une activité en mode Design

1. Sélectionnez l'activité sur laquelle vous voulez que le débogueur s'arrête.

2. Dans le menu **Déboguer** , sélectionnez **basculer le point d’arrêt**. Une icône rouge s'affiche dans l'angle supérieur gauche de l'activité.

   Vous pouvez également appuyer sur **F9** après avoir sélectionné l’activité, ou vous pouvez cliquer avec le bouton droit sur l’activité et sélectionner **point d’arrêt**  >  **Insérer un point d’arrêt** dans le menu contextuel.

## <a name="see-also"></a>Voir aussi

- [Débogage de workflows avec Workflow Designer](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)
- [Procédure : déboguer du code XAML avec Workflow Designer](../workflow-designer/how-to-debug-xaml-with-the-workflow-designer.md)
