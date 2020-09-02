---
title: 'Comment : définir une instance de méthode | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], method instance
- BDC [SharePoint development in Visual Studio], method instance
- BDC [SharePoint development in Visual Studio], method
- Business Data Connectivity service [SharePoint development in Visual Studio], method
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 170982a5d4abe33ca8cd705a979acc0737185a9c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016830"
---
# <a name="how-to-define-a-method-instance"></a>Comment : définir une instance de méthode
  Vous devez définir au moins une instance de méthode pour chaque méthode de votre modèle.

 Ajoutez une instance de méthode à l’aide de la fenêtre Détails de la **méthode BDC** . Quand vous ajoutez l’instance de méthode, Visual Studio ajoute un `<MethodInstance>` élément au XML du fichier de modèle dans votre projet. Pour plus d’informations sur les attributs d’un `<MethodInstance>` élément, consultez [MethodInstance](/previous-versions/office/developer/sharepoint-2010/ee556838(v=office.14)).

### <a name="to-define-a-method-instance"></a>Pour définir une instance de méthode

1. Dans la fenêtre **Détails de méthode BDC** , développez le nœud d’une méthode, puis développez le nœud **instances** .

2. Dans la liste **Ajouter une instance de méthode** , choisissez **créer une instance de recherche**.

     Une nouvelle instance de méthode apparaît sous le nœud **instances** .

3. Dans la barre de menus, choisissez **Afficher**la  >  **fenêtre Propriétés**.

4. Dans la fenêtre **Propriétés** , définissez les propriétés de l’instance de la méthode. Pour plus d’informations sur chaque propriété, consultez [MethodInstance](/previous-versions/office/developer/sharepoint-2010/ee556838(v=office.14)).

## <a name="see-also"></a>Voir aussi
- [Vue d’ensemble des outils de conception de modèle BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Comment : ajouter une entité à un modèle](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [Comment : ajouter un paramètre à une méthode](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Comment : définir le descripteur de type d’un paramètre](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [Concevoir un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md)
