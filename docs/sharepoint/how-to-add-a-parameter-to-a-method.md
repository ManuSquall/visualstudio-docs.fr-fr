---
title: 'Procédure : Ajouter un paramètre à une méthode | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], adding a method to a parameter
- Business Data Connectivity service [SharePoint development in Visual Studio], parameter
- BDC [SharePoint development in Visual Studio], adding a method to a parameter
- BDC [SharePoint development in Visual Studio], parameter
- Business Data Connectivity service [SharePoint development in Visual Studio], method parameters
- BDC [SharePoint development in Visual Studio], method parameters
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a5b76e49285a629234557a973f6d4b45703f1cfd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967232"
---
# <a name="how-to-add-a-parameter-to-a-method"></a>Procédure : Ajouter un paramètre à une méthode
  Utiliser un paramètre pour transmettre des informations dans la méthode ou pour retourner des informations à partir d’une méthode. Toutes les méthodes doivent avoir au moins un paramètre. Pour plus d’informations sur la conception d’un paramètre pour prendre en charge le type de méthode que vous souhaitez créer, consultez [conception d’un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md).

 Lorsque vous ajoutez un paramètre à une méthode, Visual Studio ajoute l’élément de paramètre pour le code XML du fichier de modèle dans votre projet. Pour plus d’informations sur les attributs d’un élément de paramètre, consultez [paramètre](http://go.microsoft.com/fwlink/?LinkId=169284).

### <a name="to-add-a-parameter-to-a-method"></a>Pour ajouter un paramètre à une méthode

1. Ajouter une méthode à une entité.

2. Dans la barre de menus, choisissez **vue** > **Windows autres** > **détails de méthode BDC**.

     Le **détails de méthode BDC** fenêtre s’ouvre. Pour plus d’informations, consultez [vue d’ensemble des outils de conception modèle BDC](../sharepoint/bdc-model-design-tools-overview.md).

3. Dans le **détails de méthode BDC** fenêtre, développez le nœud de la méthode, puis développez le **paramètres** nœud.

4. Dans le **ajouter un paramètre** , choisissez **créer un paramètre**.

     Un nouveau paramètre apparaît sous le **paramètres** nœud.

5. Dans la barre de menus, choisissez **vue** > **fenêtre Propriétés**.

6. Dans le **propriétés** fenêtre, définissez la **nom** propriété à n’importe quel nom qui a du sens. Par exemple, si la méthode retourne des clients, vous pouvez nommer la méthode **GetCustomers**.

7. Dans le **détails de méthode BDC** fenêtre, ouvrez la liste qui s’affiche pour la direction du paramètre, puis choisissez **dans**, **InOut**, **Out**, ou **retourner**.

     Pour plus d’informations sur la direction à choisir pour la méthode de type que vous créez, consultez [concevoir un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md).

8. Modifier le descripteur de type du paramètre. Pour plus d'informations, voir [Procédure : Définir le descripteur de type d’un paramètre](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

## <a name="see-also"></a>Voir aussi
- [Vue d’ensemble des outils de conception de modèle BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Guide pratique pour Ajouter une entité à un modèle](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [Guide pratique pour Définir le descripteur de type d’un paramètre](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [Guide pratique pour Définir une instance de méthode](../sharepoint/how-to-define-a-method-instance.md)
- [Concevoir un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md)
