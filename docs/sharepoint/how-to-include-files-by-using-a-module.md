---
title: "Comment : inclure des fichiers à l’aide d’un Module | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
ms.assetid: 16ac3c3b-8219-466c-8550-6109357f2f9a
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 3dca463352d5e698b74ecc6bda2a1579e3290513
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-include-files-by-using-a-module"></a>Comment : inclure des fichiers à l'aide d'un module
  *Modules* (à ne pas confondre avec [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] modules) sont des conteneurs qui vous permettent de déployer des fichiers tels que les pages maîtres ASPX, des fichiers texte ou des images sur SharePoint.  
  
 Vous pouvez choisir de déployer un fichier dans une bibliothèque de documents ou comme un fichier normal (par exemple, default.aspx) en dehors d’une bibliothèque de documents. Pour ajouter un fichier à une bibliothèque de documents, spécifiez `Type="GhostableInLibrary"` en tant qu’attribut dans le **fichier** élément. Ce paramètre indique à SharePoint pour créer un élément de liste à associer à votre fichier lorsqu’il est ajouté à la bibliothèque. Pour déployer un fichier en dehors d’une bibliothèque de documents, spécifiez `Type="Ghostable"` ou omettez simplement le **Type** attribut.  
  
## <a name="adding-a-module-to-a-sharepoint-solution"></a>Ajout d’un Module à une Solution SharePoint  
  
#### <a name="to-add-a-module"></a>Pour ajouter un module  
  
1.  Dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], ouvrez ou créez un projet SharePoint.  
  
     Pour plus d’informations, consultez [projets et modèles d’élément de projet SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  Dans **l’Explorateur de solutions**, choisissez le nœud du projet, puis, dans la barre de menus, choisissez **projet**, **ajouter un nouvel élément**.  
  
     La boîte de dialogue **Ajouter un nouvel élément** s’ouvre.  
  
3.  Dans la liste de modèles SharePoint, choisissez le **Module** modèle, puis choisissez le **ajouter** bouton.  
  
     Cette étape crée un nœud dans le projet nommé Module1.  
  
4.  Sous Module1, supprimez le fichier Sample.txt.  
  
     Sample.txt est inclus dans tous les nouveaux modules par exemple à des fins et n’est pas nécessaire. (Notez que la suppression du fichier supprime également son entrée dans le fichier Elements.xml du module.)  
  
5.  Si vous souhaitez que vos fichiers à déployer sur une structure de dossiers particulière dans SharePoint, créez ces dossiers sous Module1 dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] en sélectionnant le nœud Module1, puis, dans la barre de menus, en choisissant **projet**, **New Dossier**.  
  
6.  Choisissez le dossier dans lequel vous souhaitez ajouter le fichier, puis, dans la barre de menus, choisissez **projet**, **ajouter un élément existant**.  
  
7.  Choisissez un ou plusieurs fichiers que vous souhaitez déployer sur SharePoint, puis choisissez le **ajouter** bouton.  
  
     Lorsque vous ajoutez un fichier au projet, une entrée pour qu’il est automatiquement ajoutée pour le fichier Elements.xml du module. Lorsque le projet est déployé, les fichiers sont copiés vers le serveur SharePoint, relatif au répertoire racine du projet, qui est spécifié par le **fichier** l’élément **Url** attribut, tel que `Url="Module1/New Folder/SomeFile.doc`. Si vous souhaitez modifier l’emplacement de déploiement d’un fichier, soit le déplacer vers un autre dossier dans **l’Explorateur de solutions** ou modifier sa **Url** paramètre.  
  
8.  Pour tous les fichiers que vous souhaitez voir apparaître dans une bibliothèque de documents, ajoutez le `Type="GhostableInLibrary"` d’attribut à leur entrée dans le fichier Elements.xml. Par exemple :  
  
    ```  
    <File Path="Module1\Some Folder\SomePage.aspx" Url="Module1/Some Folder/SomePage.aspx" Type="GhostableInLibrary" />  
    ```  
  
9. Déployer le projet.  
  
     Les fichiers sont copiés aux emplacements spécifiés dans SharePoint.  
  
## <a name="see-also"></a>Voir aussi  
 [Empaquetage et déploiement de Solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [Développement de solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  