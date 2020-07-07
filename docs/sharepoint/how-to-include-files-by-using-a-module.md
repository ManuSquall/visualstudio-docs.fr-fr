---
title: 'Comment : inclure des fichiers à l’aide d’un module | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 1ada86be30e207e36c7e0d84d3fd5dd877605e4d
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016292"
---
# <a name="how-to-include-files-by-using-a-module"></a>Comment : inclure des fichiers à l’aide d’un module
  Les *modules* (à ne pas confondre avec les [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] modules) sont des conteneurs qui vous permettent de déployer des fichiers tels que des pages maîtres aspx, des fichiers texte ou des images dans SharePoint.

 Vous pouvez choisir de déployer un fichier dans une bibliothèque de documents ou en tant que fichier normal (par exemple, default. aspx) à l’extérieur d’une bibliothèque de documents. Pour ajouter un fichier à une bibliothèque de documents, spécifiez `Type="GhostableInLibrary"` en tant qu’attribut dans l’élément **file** . Ce paramètre indique à SharePoint de créer un élément de liste à utiliser avec votre fichier lorsqu’il est ajouté à la bibliothèque. Pour déployer un fichier en dehors d’une bibliothèque de documents, spécifiez `Type="Ghostable"` ou omettez simplement l’attribut **type** .

## <a name="add-a-module-to-a-sharepoint-solution"></a>Ajouter un module à une solution SharePoint

#### <a name="to-add-a-module"></a>Pour ajouter un module

1. Dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , ouvrez ou créez un projet SharePoint.

     Pour plus d’informations, consultez [modèles de projet et d’élément de projet SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. Dans **Explorateur de solutions**, choisissez le nœud de projet, puis, dans la barre de menus, choisissez **projet**  >  **Ajouter un nouvel élément**.

     La boîte de dialogue **Ajouter un nouvel élément** s’ouvre.

3. Dans la liste des modèles SharePoint, choisissez le modèle de **module** , puis cliquez sur le bouton **Ajouter** .

     Cette étape crée un nœud dans le projet nommé Module1.

4. Sous Module1, supprimez le fichier *Sample.txt* .

     Sample.txt est inclus dans tous les nouveaux modules à titre d’exemple et n’est pas nécessaire. (Notez que la suppression du fichier supprime également son entrée du fichier *Elements.xml* du module.)

5. Si vous souhaitez que vos fichiers soient déployés dans une structure de dossiers particulière dans SharePoint, créez ces dossiers sous Module1 dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] en choisissant le nœud Module1, puis, dans la barre de menus, choisissez **projet**, **nouveau dossier**.

6. Choisissez le dossier dans lequel vous souhaitez ajouter le fichier, puis, dans la barre de menus, choisissez **projet**, **Ajouter un élément existant**.

7. Choisissez un ou plusieurs fichiers que vous souhaitez déployer sur SharePoint, puis choisissez le bouton **Ajouter** .

     Lorsque vous ajoutez un fichier au projet, une entrée pour celui-ci est automatiquement ajoutée au fichier Elements.xml du module. Lorsque le projet est déployé, les fichiers sont copiés vers SharePoint Server, par rapport au répertoire racine du projet, qui est spécifié par l’attribut **URL** de l’élément de **fichier** , tel que `Url="Module1/New Folder/SomeFile.doc` . Si vous souhaitez modifier l’emplacement de déploiement d’un fichier, déplacez-le vers un autre dossier dans **Explorateur de solutions** ou modifiez son paramètre d' **URL** .

8. Pour tous les fichiers que vous souhaitez voir apparaître dans une bibliothèque de documents, ajoutez l' `Type="GhostableInLibrary"` attribut à leur entrée dans *Elements.xml*. Par exemple,

    ```xml
    <File Path="Module1\Some Folder\SomePage.aspx" Url="Module1/Some Folder/SomePage.aspx" Type="GhostableInLibrary" />
    ```

9. Déployez le projet.

     Les fichiers sont copiés vers les emplacements spécifiés dans SharePoint.

## <a name="see-also"></a>Voir aussi
- [Empaqueter et déployer des solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
- [Développement de solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)
