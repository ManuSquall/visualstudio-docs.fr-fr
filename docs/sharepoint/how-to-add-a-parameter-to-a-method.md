---
title: 'Comment : ajouter un paramètre à une méthode | Microsoft Docs'
description: Savoir comment ajouter un paramètre à une méthode de connectivité de données métiers (BDC), qui vous permet de passer des informations dans la méthode ou de retourner des informations à partir de la méthode.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d568d5ca2025f1467fa96387493b1e8b4ed1ec6e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931693"
---
# <a name="how-to-add-a-parameter-to-a-method"></a>Comment : ajouter un paramètre à une méthode
  Utilisez un paramètre pour passer des informations dans la méthode ou pour retourner des informations à partir d’une méthode. Toutes les méthodes doivent avoir au moins un paramètre. Pour plus d’informations sur la conception d’un paramètre pour prendre en charge le type de méthode que vous souhaitez créer, consultez [conception d’un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md).

 Quand vous ajoutez un paramètre à une méthode, Visual Studio ajoute l’élément de paramètre au XML du fichier de modèle dans votre projet. Pour plus d’informations sur les attributs d’un élément de paramètre, consultez [paramètre](/previous-versions/office/developer/sharepoint-2010/ee557705(v=office.14)).

### <a name="to-add-a-parameter-to-a-method"></a>Pour ajouter un paramètre à une méthode

1. Ajoutez une méthode à une entité.

2. Dans la barre de menus, choisissez **Afficher**  >  **les autres** détails de la  >  **méthode BDC** Windows.

     La fenêtre Détails de la **méthode BDC** s’ouvre. Pour plus d’informations, consultez [vue d’ensemble des outils de conception de modèle BDC](../sharepoint/bdc-model-design-tools-overview.md).

3. Dans la fenêtre **Détails de méthode BDC** , développez le nœud de la méthode, puis développez le nœud **paramètres** .

4. Dans la liste **Ajouter un paramètre** , choisissez **créer un paramètre**.

     Un nouveau paramètre apparaît sous le nœud **paramètres** .

5. Dans la barre de menus, choisissez **Afficher** la  >  **fenêtre Propriétés**.

6. Dans la fenêtre **Propriétés** , affectez à la propriété **nom** n’importe quel nom qui est pertinent. Par exemple, si la méthode retourne des clients, vous pouvez nommer la méthode **GetCustomers**.

7. Dans la **fenêtre Détails de méthode BDC** , ouvrez la liste qui s’affiche pour la direction du paramètre, puis choisissez **in**, **INOUT**, **out** ou **Return**.

     Pour plus d’informations sur la direction à choisir pour la méthode de type que vous créez, consultez [concevoir un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md).

8. Modifiez le descripteur de type du paramètre. Pour plus d’informations, consultez [Comment : définir le descripteur de type d’un paramètre](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

## <a name="see-also"></a>Voir aussi
- [Vue d’ensemble des outils de conception de modèle BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Comment : ajouter une entité à un modèle](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [Comment : définir le descripteur de type d’un paramètre](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [Comment : définir une instance de méthode](../sharepoint/how-to-define-a-method-instance.md)
- [Concevoir un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md)
