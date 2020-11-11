---
title: Lier des contrôles à des images d’une base de données
description: Utilisez la fenêtre sources de données pour lier une image d’une base de données à un contrôle de votre application Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 10ea349186aa46bfb58f4b9ceeaab2c8ac3edd81
ms.sourcegitcommit: 63ff7cb85b3baeeb713240d17bb2a18497f3741d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94518568"
---
# <a name="bind-controls-to-pictures-from-a-database"></a>Lier des contrôles à des images d’une base de données

Vous pouvez utiliser la fenêtre **sources de données** pour lier une image d’une base de données à un contrôle dans votre application. Par exemple, vous pouvez lier une image à un <xref:System.Windows.Controls.Image> contrôle dans une application WPF, ou à un <xref:System.Windows.Forms.PictureBox> contrôle dans une application Windows Forms.

Les images d’une base de données sont généralement stockées en tant que tableaux d’octets. Les éléments de la fenêtre **sources de données** qui sont stockés en tant que tableaux d’octets ont leur type de contrôle défini sur None par défaut, car les tableaux d’octets peuvent contenir **n'** importe quel élément d’un tableau d’octets simple au fichier exécutable d’une application volumineuse. Pour créer un contrôle lié aux données pour un élément de tableau d’octets dans la fenêtre **sources de données** qui représente une image, vous devez sélectionner le contrôle à créer.

La procédure suivante suppose que la fenêtre **sources de données** est déjà remplie avec un élément qui est lié à votre image.

## <a name="to-bind-a-picture-in-a-database-to-a-control"></a>Pour lier une image d’une base de données à un contrôle

1. Assurez-vous que l’aire de conception à laquelle vous souhaitez ajouter le contrôle est ouverte dans le Concepteur WPF ou le Concepteur Windows Forms.

2. Dans la fenêtre **sources de données** , développez la table ou l’objet souhaité pour afficher ses colonnes ou ses propriétés.

   > [!TIP]
   > Si la fenêtre **sources de données** n’est pas ouverte, ouvrez-la en sélectionnant **Afficher** d'  >  **autres**  >  **sources de données** Windows.

3. Sélectionnez la colonne ou la propriété qui contient vos données image, puis sélectionnez l’un des contrôles suivants dans la liste déroulante de contrôle :

    - Si le Concepteur WPF est ouvert, sélectionnez **image**.

    - Si le concepteur de Windows Forms est ouvert, sélectionnez **PictureBox**.

    - Vous pouvez également sélectionner un autre contrôle qui prend en charge la liaison de données et qui peut afficher des images. Si le contrôle que vous souhaitez utiliser ne figure pas dans la liste des contrôles disponibles, vous pouvez l’ajouter à la liste, puis le sélectionner. Pour plus d’informations, consultez [Ajouter des contrôles personnalisés à la fenêtre sources de données](../data-tools/add-custom-controls-to-the-data-sources-window.md).

## <a name="see-also"></a>Voir aussi

- [Lier des contrôles WPF à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
