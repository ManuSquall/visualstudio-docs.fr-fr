---
title: 'Procédure : Définir une Instance de méthode | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 2f879f8367ad1b992300c9e5b1c8a2887e89205b
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56608007"
---
# <a name="how-to-define-a-method-instance"></a>Procédure : Définir une instance de méthode
  Vous devez définir au moins une instance de méthode pour chaque méthode dans votre modèle.

 Ajouter une instance de méthode à l’aide de la **détails de méthode BDC** fenêtre. Lorsque vous ajoutez l’instance de méthode, Visual Studio ajoute un `<MethodInstance>` élément pour le code XML du fichier de modèle dans votre projet. Pour plus d’informations sur les attributs d’un `<MethodInstance>` élément, consultez [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282).

### <a name="to-define-a-method-instance"></a>Pour définir une instance de méthode

1.  Dans le **détails de méthode BDC** fenêtre, développez le nœud d’une méthode, puis développez le **Instances** nœud.

2.  Dans le **ajouter une Instance de méthode** , choisissez **créer une Instance de recherche**.

     Une nouvelle instance de méthode apparaît sous le **Instances** nœud.

3.  Dans la barre de menus, choisissez **vue** > **fenêtre Propriétés**.

4.  Dans le **propriétés** fenêtre, définissez les propriétés de l’instance de méthode. Pour plus d’informations sur chaque propriété, consultez [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282).

## <a name="see-also"></a>Voir aussi
- [Vue d’ensemble des outils de conception de modèle BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Guide pratique pour Ajouter une entité à un modèle](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [Guide pratique pour Ajouter un paramètre à une méthode](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Guide pratique pour Définir le descripteur de type d’un paramètre](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [Concevoir un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md)
