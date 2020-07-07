---
title: 'Comment : ajouter une méthode de suppression | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], deleting data
- Business Data Connectivity service [SharePoint development in Visual Studio], Deleter
- BDC [SharePoint development in Visual Studio], Deleter
- BDC [SharePoint development in Visual Studio], removing data
- BDC [SharePoint development in Visual Studio], deleting entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], deleting entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], deleting data
- Business Data Connectivity service [SharePoint development in Visual Studio], removing data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: dd97d28936e9f0cc50e9064fdc1a6a64bb20fc77
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86017033"
---
# <a name="how-to-add-a-deleter-method"></a>Comment : ajouter une méthode de suppression
  Vous pouvez autoriser un utilisateur final à supprimer un enregistrement de données d’une liste externe sur un site SharePoint en ajoutant une méthode de suppression au modèle. Pour plus d’informations, consultez [concevoir un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-create-a-deleter-method"></a>Pour créer une méthode de suppression

1. Dans le **concepteur BDC**, choisissez une entité.

2. Dans la barre de menus, choisissez **Afficher**  >  **les autres**détails de la  >  **méthode BDC**Windows.

    La fenêtre Détails de la **méthode BDC** s’ouvre. Pour plus d’informations sur cette fenêtre, consultez [vue d’ensemble des outils de conception de modèle BDC](../sharepoint/bdc-model-design-tools-overview.md).

3. Dans la liste **Ajouter une méthode** , choisissez **créer une méthode de suppression**.

    Visual Studio ajoute les éléments suivants au modèle. Ces éléments s’affichent dans la fenêtre Détails de la **méthode BDC** .

   - Une méthode nommée **Delete**.

   - Paramètre d’entrée pour la méthode.

   - Descripteur de type pour le paramètre.

   - Instance de méthode pour la méthode.

     Pour plus d’informations, consultez [concevoir un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md).

4. Dans **Explorateur de solutions**, ouvrez le menu contextuel du fichier de code de service qui a été généré pour l’entité, puis choisissez **afficher le code**.

    Le fichier de code du service d’entité s’ouvre dans l’éditeur de code. Pour plus d’informations sur le fichier de code du service d’entité, consultez [créer un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md).

5. Ajoutez du code à la méthode de suppression pour supprimer un enregistrement. L’exemple suivant supprime un élément de ligne d’une commande client à l’aide de l’exemple de base de données AdventureWorks pour SQL Server.

   > [!NOTE]
   > La méthode dans cet exemple utilise deux paramètres d’entrée.

   > [!NOTE]
   > Remplacez la valeur du `ServerName` champ par le nom de votre serveur.

    [!code-csharp[SP_BDC#6](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs#6)]
    [!code-vb[SP_BDC#6](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb#6)]

## <a name="see-also"></a>Voir aussi
- [Concevoir un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Comment : ajouter une méthode de recherche](../sharepoint/how-to-add-a-finder-method.md)
- [Comment : ajouter une méthode de recherche spécifique](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Comment : ajouter une méthode Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Comment : ajouter une méthode de mise à jour](../sharepoint/how-to-add-an-updater-method.md)
- [Vue d’ensemble des outils de conception de modèle BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Comment : ajouter un paramètre à une méthode](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Comment : définir une instance de méthode](../sharepoint/how-to-define-a-method-instance.md)
