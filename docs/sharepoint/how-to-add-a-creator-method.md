---
title: 'Procédure : Ajouter une méthode de création | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], Creator
- BDC [SharePoint development in Visual Studio], adding entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], adding entities
- Business Data Connectivity service [SharePoint development in Visual Studio], adding entity instances
- BDC [SharePoint development in Visual Studio], adding entities
- Business Data Connectivity service [SharePoint development in Visual Studio], Creator
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 01ad692065a51d51fc1f6b72acc563688da3a217
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53925418"
---
# <a name="how-to-add-a-creator-method"></a>Procédure : Ajouter une méthode de création
  Une méthode de création ajoute de nouvelles données à la source de données d’une entité. Le service de connectivité de données métiers (BDC) appelle cette méthode quand les utilisateurs choisissent le **un nouvel élément** bouton sur le **ruban** d’une liste qui est basée sur le modèle. Pour plus d’informations, consultez [concevoir un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-add-a-creator-method"></a>Pour ajouter une méthode de création  
  
1. Sur le **concepteur BDC**, choisir une entité.  
  
2. Dans la barre de menus, choisissez **vue** > **Windows autres** >**détails de méthode BDC**.  
  
    Le **détails de méthode BDC** fenêtre s’ouvre. Pour plus d’informations sur cette fenêtre, consultez [vue d’ensemble des outils de conception du modèle BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
3. Dans le **ajouter une méthode** , choisissez **créer une méthode de création**.  
  
    Visual Studio ajoute les éléments suivants au modèle, et ces éléments apparaissent dans le **détails de méthode BDC** fenêtre.  
  
   - Une méthode nommée **créer**.  
  
   - Un paramètre d’entrée pour la méthode.  
  
   - Un paramètre de retour pour la méthode.  
  
   - Descripteurs pour les paramètres de type.  
  
   - Une instance de méthode pour la méthode.  
  
     Pour plus d’informations, consultez [concevoir un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
4. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel du service du fichier de code qui a été généré pour l’entité, puis choisissez **afficher le Code**.  
  
    Le fichier de code de service entité s’ouvre dans l’éditeur de Code. Pour plus d’informations sur le fichier de code de service entité, consultez [créer un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
5. Ajoutez le code à la méthode de création qui ajoute des données à la source de données. L’exemple suivant ajoute un contact à la base de données AdventureWorks pour SQL Server.  
  
   > [!NOTE]  
   >  Remplacez la valeur de la `ServerName` champ avec le nom de votre serveur.  
  
    [!code-csharp[SP_BDC#4](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#4)]
    [!code-vb[SP_BDC#4](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#4)]  
  
## <a name="see-also"></a>Voir aussi
 [Concevoir un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Guide pratique pour Ajouter une méthode de recherche](../sharepoint/how-to-add-a-finder-method.md)   
 [Guide pratique pour Ajouter une méthode de recherche spécifique](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Guide pratique pour Ajouter une méthode de suppression](../sharepoint/how-to-add-a-deleter-method.md)   
 [Guide pratique pour Ajouter une méthode de mise à jour](../sharepoint/how-to-add-an-updater-method.md)   
 [Vue d’ensemble des outils de conception de modèle BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Guide pratique pour Ajouter un paramètre à une méthode](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Guide pratique pour Définir une instance de méthode](../sharepoint/how-to-define-a-method-instance.md)  
