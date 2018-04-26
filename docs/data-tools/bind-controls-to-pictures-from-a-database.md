---
title: Lier des contrôles à des images à partir d’une base de données
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
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 00608bae35a9f3272e46e53d7e0205b48c0ea7d9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="bind-controls-to-pictures-from-a-database"></a>Lier des contrôles à des images à partir d’une base de données

Vous pouvez utiliser la **des Sources de données** fenêtre pour lier une image dans une base de données à un contrôle dans votre application. Par exemple, vous pouvez lier une image à un <xref:System.Windows.Controls.Image> contrôler dans une application WPF, ou à un <xref:System.Windows.Forms.PictureBox> contrôle dans une application Windows Forms.

Images dans une base de données sont généralement stockés en tant que tableaux d’octets. Les éléments dans le **des Sources de données** les fenêtres qui sont stockées sous forme de tableaux d’octets ont leur contrôle de type **aucun** par défaut, car les tableaux d’octets peuvent contenir tout ce à partir d’un simple tableau d’octets du fichier exécutable d’une application volumineuse. Pour créer un contrôle lié aux données pour un élément de tableau d’octets dans le **des Sources de données** fenêtre qui représente une image, vous devez sélectionner le contrôle à créer.

La procédure suivante suppose que la **des Sources de données** fenêtre est déjà remplie avec un élément qui est lié à votre image.

## <a name="to-bind-a-picture-in-a-database-to-a-control"></a>Pour lier une image dans une base de données à un contrôle

1.  Assurez-vous que vous souhaitez ajouter le contrôle à l’aire de conception est ouvert dans le Concepteur WPF ou le Concepteur Windows Forms.

2.  Dans le **des Sources de données** fenêtre, développez la table souhaitée, ou pour afficher ses colonnes ou les propriétés de l’objet.

3.  Sélectionnez la colonne ou la propriété qui contient vos données d’image, puis sélectionnez un des contrôles suivants à partir de sa liste de contrôle de liste déroulante :

    -   Si le Concepteur WPF est ouvert, sélectionnez **Image**.

    -   Si le Concepteur Windows Forms est ouvert, sélectionnez **PictureBox**.

    -   Vous pouvez également sélectionner un autre contrôle qui prend en charge la liaison de données et qui peut afficher des images. Si le contrôle que vous souhaitez utiliser n’est pas dans la liste des contrôles disponibles, vous pouvez ajouter à la liste et sélectionnez-le. Pour plus d’informations, consultez [ajouter des contrôles personnalisés à la fenêtre Sources de données](../data-tools/add-custom-controls-to-the-data-sources-window.md).

## <a name="see-also"></a>Voir aussi

- [Lier des contrôles WPF à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)