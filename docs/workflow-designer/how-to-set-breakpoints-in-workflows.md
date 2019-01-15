---
title: 'Concepteur de flux de travail - Comment : Définir des points d’arrêt dans les workflows'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.assetid: e41b21c9-c061-4358-8e2f-eb5e412864a8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 570e7c5b4ec64c4e21b53cef38b89a5846cc1bb7
ms.sourcegitcommit: 38db86369af19e174b0aba59ba1918a5c4fe4a61
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2019
ms.locfileid: "54269694"
---
# <a name="how-to-set-breakpoints-in-workflows"></a>Procédure : Définir des points d’arrêt dans les workflows

Lorsque vous utilisez le Concepteur de flux de travail, vous pouvez définir des points d’arrêt sur vos workflows graphiques comme vous le feriez dans le code Visual Basic ou c#. Comme prévu, l'exécution de workflow s'arrête à chaque point d'arrêt que vous définissez.

Un point d’arrêt a trois états : *En attente*, *lié*, et *erreur*. Lorsque vous définissez un point d'arrêt, il a l'état En attente et est représenté par une icône rouge unie. Lorsque l'exécution a chargé le type de workflow, il adopte l'état Lié. Si vous spécifiez un format incorrect pour le point d'arrêt, par exemple en indiquant un nom d'activité non valide, un message d'erreur s'affiche. Le point d'arrêt est ajouté à la fenêtre de points d'arrêt, mais il est marqué d'un petit « x ».

> [!NOTE]
> La définition des points d'arrêt sur les workflows appelés n'est pas prise en charge.

> [!NOTE]
> Vérifiez que vous sélectionnez l’option **activer uniquement mon Code (managé uniquement)** à partir de la **outils** > **Options** > **débogage**  menu avant de déboguer. Si l’option n’est pas sélectionnée et vous disposez de deux séquences sont imbriquées dans une autre séquence, vous définissez un point d’arrêt sur la première séquence interne, en appuyant sur **F11** ne déboguez pas dans la deuxième séquence interne.

> [!NOTE]
> Points d’arrêt dans un flux de travail ne sont pas atteints si le chemin d’accès complet à la propriété de fichier XAML n’est pas précis. Le chemin d’accès complet au fichier XAML n’est pas précis après le déplacement de la solution ou le projet vers un autre dossier ou à un autre ordinateur. Sélectionnez **Ctrl**+**S** pour enregistrer et mettre à jour la propriété de chemin d’accès complet.

## <a name="to-set-a-breakpoint-on-an-activity-in-the-design-view"></a>Pour définir un point d'arrêt sur une activité en mode Design

1. Sélectionnez l'activité sur laquelle vous voulez que le débogueur s'arrête.

2. Sur le **déboguer** menu, sélectionnez **point d’arrêt**. Une icône rouge s'affiche dans l'angle supérieur gauche de l'activité.

   Vous pouvez également appuyer sur **F9** après sélection de l’activité, ou vous pouvez avec le bouton droit de l’activité et sélectionnez **point d’arrêt** > **insérer un point d’arrêt** dans le menu contextuel.

## <a name="see-also"></a>Voir aussi

- [Débogage de flux de travail à l’aide du Concepteur de flux de travail](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)
- [Guide pratique pour Déboguer XAML avec Workflow Designer](../workflow-designer/how-to-debug-xaml-with-the-workflow-designer.md)