---
title: Lier des contrôles à des images d’une base de données
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- images [Visual Basic], displaying on Windows Forms
- data binding [Windows Forms], pictures
- images [Visual Basic], data binding
- pictures, data binding
- pictures, dragging from Data Sources window
- Data Sources Window, setting controls to display images
- PictureBox control [Windows Forms], data binding
- images [Visual Basic], dragging from Data Sources window
ms.assetid: 9748815e-3556-49e8-86b1-c6aa593c6163
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 5afabf877fbd1a34bc579d81a137abbd5771fed5
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55944063"
---
# <a name="bind-controls-to-pictures-from-a-database"></a>Lier des contrôles à des images d’une base de données

Vous pouvez utiliser la **des Sources de données** fenêtre pour lier une image dans une base de données à un contrôle dans votre application. Par exemple, vous pouvez lier une image à un <xref:System.Windows.Controls.Image> contrôler dans une application WPF, ou à un <xref:System.Windows.Forms.PictureBox> contrôle dans une application Windows Forms.

Images dans une base de données sont généralement stockées en tant que tableaux d’octets. Les éléments dans le **des Sources de données** fenêtre stockés sous forme de tableaux d’octets ont leur contrôle de type définie sur **aucun** par défaut, étant donné que les tableaux d’octets peuvent contenir tout ce à partir d’un simple tableau d’octets au fichier exécutable d’une grande application. Pour créer un contrôle lié aux données pour un élément de tableau d’octets dans le **des Sources de données** fenêtre qui représente une image, vous devez sélectionner le contrôle à créer.

La procédure suivante suppose que le **des Sources de données** fenêtre est déjà remplie avec un élément qui est lié à votre image.

## <a name="to-bind-a-picture-in-a-database-to-a-control"></a>Pour lier une image dans une base de données à un contrôle

1.  Assurez-vous que vous souhaitez ajouter le contrôle à l’aire de conception est ouvert dans le Concepteur WPF ou le Concepteur de formulaires Windows.

2.  Dans le **des Sources de données** fenêtre, développez la table souhaitée ou pour afficher ses colonnes ou propriétés de l’objet.

   > [!TIP]
   > Si le **des Sources de données** fenêtre n’est pas ouverte, ouvrez-le en sélectionnant **vue** > **Windows autres** > **desSourcesdedonnées**.

3.  Sélectionnez la colonne ou la propriété qui contient vos données d’image, puis sélectionnez un des contrôles suivants à partir de sa liste de contrôle de liste déroulante :

    - Si le Concepteur WPF est ouvert, sélectionnez **Image**.

    - Si le Concepteur Windows Forms est ouvert, sélectionnez **PictureBox**.

    - Vous pouvez également sélectionner un autre contrôle qui prend en charge la liaison de données et qui peut afficher des images. Si le contrôle que vous souhaitez utiliser n’est pas dans la liste des contrôles disponibles, vous pouvez l’ajouter à la liste et sélectionnez-le. Pour plus d’informations, consultez [ajouter des contrôles personnalisés à la fenêtre Sources de données](../data-tools/add-custom-controls-to-the-data-sources-window.md).

## <a name="see-also"></a>Voir aussi

- [Lier des contrôles WPF à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)