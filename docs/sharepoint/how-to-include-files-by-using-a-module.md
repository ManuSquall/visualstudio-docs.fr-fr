---
title: 'Procédure : Inclure des fichiers à l’aide d’un Module | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5813a6f89062bf53f7f8c0b57b4ed3a8ef9c4edf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62813642"
---
# <a name="how-to-include-files-by-using-a-module"></a>Procédure : Inclure des fichiers à l’aide d’un module
  *Modules* (à ne pas confondre avec [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] modules) sont des conteneurs qui vous permettent de déployer des fichiers tels que les pages maîtres ASPX, des fichiers texte ou des images sur SharePoint.

 Vous pouvez choisir de déployer un fichier dans une bibliothèque de documents ou dans un fichier normal (par exemple, default.aspx) en dehors d’une bibliothèque de documents. Pour ajouter un fichier à une bibliothèque de documents, spécifiez `Type="GhostableInLibrary"` en tant qu’attribut dans le **fichier** élément. Ce paramètre indique à SharePoint pour créer un élément de liste à associer à votre fichier lorsqu’il est ajouté à la bibliothèque. Pour déployer un fichier en dehors d’une bibliothèque de documents, spécifiez `Type="Ghostable"` ou omettez simplement le **Type** attribut.

## <a name="add-a-module-to-a-sharepoint-solution"></a>Ajouter un module à une solution SharePoint

#### <a name="to-add-a-module"></a>Pour ajouter un module

1. Dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], ouvrez ou créez un projet SharePoint.

     Pour plus d’informations, consultez [SharePoint modèles d’élément de projet et le projet](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. Dans **l’Explorateur de solutions**, choisissez le nœud du projet, puis, dans la barre de menus, choisissez **projet** > **ajouter un nouvel élément**.

     La boîte de dialogue **Ajouter un nouvel élément** s’ouvre.

3. Dans la liste de modèles SharePoint, choisissez le **Module** modèle, puis choisissez le **ajouter** bouton.

     Cette étape crée un nœud dans le projet nommé Module1.

4. Sous Module1, supprimez le *Sample.txt* fichier.

     Sample.txt est inclus dans tous les nouveaux modules par exemple à des fins et n’est pas nécessaire. (Notez que la suppression du fichier supprime également son entrée à partir du module *Elements.xml* fichier.)

5. Si vous souhaitez que vos fichiers à déployer sur une structure de dossiers particulière dans SharePoint, créez ces dossiers sous Module1 dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] en choisissant le nœud Module1, puis, dans la barre de menus, choisissez **projet**, **New Dossier**.

6. Choisissez le dossier dans lequel vous souhaitez ajouter le fichier, puis, dans la barre de menus, choisissez **projet**, **ajouter un élément existant**.

7. Choisissez un ou plusieurs fichiers que vous souhaitez déployer sur SharePoint, puis choisissez le **ajouter** bouton.

     Lorsque vous ajoutez un fichier au projet, une entrée pour qu’il est automatiquement ajoutée au fichier Elements.xml du module. Lorsque le projet est déployé, les fichiers sont copiés vers SharePoint server, relatif au répertoire du projet racine, qui est spécifié par le **fichier** l’élément **Url** attribut, tel que `Url="Module1/New Folder/SomeFile.doc`. Si vous souhaitez modifier l’emplacement de déploiement pour un fichier, soit le déplacer vers un autre dossier dans **l’Explorateur de solutions** ou modifier ses **Url** paramètre.

8. Pour tous les fichiers que vous souhaitez voir apparaître dans une bibliothèque de documents, ajoutez le `Type="GhostableInLibrary"` leur entrée dans l’attribut *Elements.xml*. Par exemple :

    ```xml
    <File Path="Module1\Some Folder\SomePage.aspx" Url="Module1/Some Folder/SomePage.aspx" Type="GhostableInLibrary" />
    ```

9. Déployer le projet.

     Les fichiers sont copiés aux emplacements spécifiés dans SharePoint.

## <a name="see-also"></a>Voir aussi
- [Empaqueter et déployer des solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
- [Développement de solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)
