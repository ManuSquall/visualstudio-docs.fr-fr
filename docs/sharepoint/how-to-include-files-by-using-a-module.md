---
title: "Comment&#160;: inclure des fichiers &#224; l&#39;aide d&#39;un module | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "modules (développement SharePoint dans Visual Studio)"
  - "développement SharePoint dans Visual Studio, modules"
ms.assetid: 16ac3c3b-8219-466c-8550-6109357f2f9a
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Comment&#160;: inclure des fichiers &#224; l&#39;aide d&#39;un module
  Les *modules* \(à ne pas confondre avec les modules [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]\) sont des conteneurs qui vous permettent de déployer des fichiers tels que des images, des fichiers texte ou des pages maîtres ASPX, sur SharePoint.  
  
 Vous pouvez choisir de déployer un fichier dans une bibliothèque de documents ou comme un fichier normal \(par exemple, default.aspx\) à l'extérieur d'une bibliothèque de documents.  Pour ajouter un fichier à une bibliothèque de documents, spécifiez `Type="GhostableInLibrary"` comme attribut dans l'élément **File**.  Ce paramètre indique à SharePoint de créer un élément de liste à associer à votre fichier lorsqu'il est ajouté à la bibliothèque.  Pour déployer un fichier à l'extérieur d'une bibliothèque de documents, spécifiez `Type="Ghostable"` ou omettez simplement l'attribut **Type**.  
  
## Ajout d'un module à une solution SharePoint  
  
#### Pour ajouter un module  
  
1.  Dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], ouvrez ou créez un projet SharePoint.  
  
     Pour plus d'informations, consultez [Modèles de projets et d'éléments de projet SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  Dans l'**Explorateur de solutions**, choisissez le nœud de projet, puis, dans la barre de menus, choisissez **Project**, **Ajouter un nouvel objet**.  
  
     La boîte de dialogue **Ajouter un nouvel élément** s'ouvre.  
  
3.  Dans la liste des modèles, sélectionnez le modèle **Module**, puis choisissez le bouton **OK**.  
  
     Cette étape crée un nœud nommé Module1 dans le projet.  
  
4.  Sous Module1, supprimez le fichier Sample.txt.  
  
     Sample.txt est inclus à titre d'exemple dans tous les nouveaux modules et n'est pas obligatoire. \(Notez que la suppression du fichier supprime également son entrée dans le fichier Elements.xml du module.\)  
  
5.  Si vous voulez déployer vos fichiers dans une arborescence particulière de SharePoint, créez ces dossiers sous Module1 dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] en choisissant le nœud Module1, puis, dans la barre de menus, en choisissant **Projet**, **Nouveau dossier**.  
  
6.  Choisissez le dossier dans lequel vous souhaitez ajouter le fichier, puis, dans la barre de menu, choisisse **Projet**, **Ajouter un élément existant**.  
  
7.  Choisissez un ou plusieurs fichiers que vous souhaitez déployer sur SharePoint, puis choisissez le bouton **Ajouter**.  
  
     Lorsque vous ajoutez un fichier au projet, une entrée pour celui\-ci est automatiquement ajoutée au fichier Elements.xml du module.  Lorsque le projet est déployé, les fichiers sont copiés vers le serveur SharePoint, par rapport au répertoire racine du projet, spécifié par l'attribut **Url** de l'élément **File**, par exemple `Url="Module1/New Folder/SomeFile.doc`.  Si vous souhaitez modifier l'emplacement de déploiement d'un fichier, déplacez\-le vers un autre dossier dans l'**Explorateur de solutions** ou modifiez son paramètre **Url**.  
  
8.  Pour tous les fichiers que vous souhaitez voir apparaître dans une bibliothèque de documents, ajoutez l'attribut `Type="GhostableInLibrary"` à leur entrée dans Elements.xml.  Par exemple :  
  
    ```  
    <File Path="Module1\Some Folder\SomePage.aspx" Url="Module1/Some Folder/SomePage.aspx" Type="GhostableInLibrary" />  
    ```  
  
9. Déployez le projet.  
  
     Les fichiers sont copiés vers les emplacements spécifiés dans SharePoint.  
  
## Voir aussi  
 [Empaquetage et déploiement de solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  