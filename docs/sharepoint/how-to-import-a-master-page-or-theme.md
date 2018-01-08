---
title: "Comment : importer une Page maître ou un thème | Documents Microsoft"
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
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
ms.assetid: 8b446cca-2adb-457b-bbfd-891209290e80
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 447fa8749958a3fa2b65a6ef7eb878b906170e6a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-import-a-master-page-or-theme"></a>Comment : importer une page maître ou un thème
  Vous pouvez attribuer aux pages sur votre site SharePoint une apparence cohérente en créant et en utilisant les thèmes et les pages maîtres. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]ne fournit pas les modèles pour ces éléments, mais vous pouvez les créer dans SharePoint Designer et importez-les dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Pour plus d’informations, consultez [bloc de construction : Pages et Interface utilisateur](http://go.microsoft.com/fwlink/?LinkID=182095) sur le site Web Microsoft.  
  
### <a name="to-import-a-master-page-or-theme"></a>Pour importer une page maître ou un thème  
  
1.  Dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], créez ou ouvrez un projet SharePoint.  
  
     Pour plus d’informations sur la création d’un projet SharePoint, consultez [projets et modèles d’élément de projet SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  Dans la barre de menus, choisissez **projet**, **ajouter un nouvel élément**.  
  
3.  Dans le **ajouter un nouvel élément** boîte de dialogue, développez le **SharePoint** nœud, puis choisissez le **2010** nœud.  
  
4.  Dans la liste de modèles SharePoint, choisissez le **Module** modèle, puis spécifiez un nom pour le module.  
  
     Un module contient des fichiers (par exemple, page maître ou fichiers thème) pour le déploiement vers un emplacement que vous spécifiez dans SharePoint.  
  
5.  Dans le module, supprimez le fichier par défaut, qui est nommé Sample.txt.  
  
6.  Choisissez le nœud de module.  
  
7.  Dans la barre de menus, choisissez **projet**, **ajouter un élément existant**, puis choisissez le fichier de thème ou de page maître.  
  
     Fichiers de page maître portent l’extension .master, et les fichiers de thème portent l’extension .thmx.  
  
8.  Si vous avez ajouté une page maître, modifiez son **Deployment Conflict Resolution** à **automatique** dans les propriétés du module.  
  
    > [!NOTE]  
    >  Erreurs peuvent se produire si le nom de la page maître est le même que le nom d’une page maître existante qui est marquée comme Page maître par défaut ou Page maître personnalisée. Pour plus d’informations sur la façon de résoudre ce problème, consultez [procédure pas à pas : importation d’un gabarit personnalisé et une Page de Site avec une Image](../sharepoint/walkthrough-import-a-custom-master-page-and-site-page-with-an-image.md).  
  
9. Dans le module, ouvrez le fichier Elements.xml.  
  
     Vous devez mettre à jour le fichier Elements.xml pour faire référence à la page maître ou le thème que vous avez ajouté.  
  
10. Pour une page maître, remplacez la balise de module existante par la balise suivante.  
  
    ```  
    <Module Name="[Module Name]" Url="_catalogs/masterpage">  
        <File Path="[Module Name]\[Master Page Name].master"   
          Url="[Master Page Name].master" Type="GhostableInLibrary" />  
    </Module>  
    ```  
  
     Pour un thème, remplacez la balise de module existante par la balise suivante.  
  
    ```  
    <Module Name="[Module Name]" Url="_catalogs/theme"   
        <File Path="[Module Name]\[Theme Name].thmx" Url="[Theme     
          Name].thmx" Type="GhostableInLibrary" />  
    </Module>  
    ```  
  
     Veillez à remplacer les valeurs de l’espace réservé par les noms réels du module et la page maître ou un thème.  
  
     L’attribut `Type="GhostableInLibrary"` indique que l’élément est ajouté à la base de données de contenu et le `Url` attribut du module spécifie l’emplacement de stockage du fichier dans la base de données de contenu SharePoint.  
  
11. Pour modifier la portée de déploiement pour une page maître, dans **l’Explorateur de solutions**, ouvrez le fichier de fonctionnalité dans le Concepteur de fonctionnalités, puis choisissez une nouvelle portée de déploiement à partir de la **étendue** liste.  
  
     La valeur **Web** signifie que la page maître s’applique uniquement au site Web qui est actuellement spécifié dans le projet. La valeur **Site** signifie que la page maître s’applique à la collection de sites actuelle, qui inclut tous les sous-sites et le site web racine. Les autres valeurs ne s’appliquent pas.  
  
    > [!NOTE]  
    >  Étant donné que les thèmes s’appliquent uniquement au niveau de la collection de sites, nous recommandons que vous ne définissez pas la portée d’un thème à tout élément autre que **Site**. Erreurs peuvent se produire si un thème est utilisé dans un sous-site.  
  
12. Dans la barre de menus, choisissez **générer**, **déployer la Solution**.  
  
13. Pour vérifier si les fichiers ont été correctement déployées, ouvrez le site SharePoint, choisissez le **Actions du Site** menu, choisissez le **paramètres du Site** de commandes, puis choisissez le **Pages maîtres**  lien ou le **thèmes** lien.  
  
     La liste des pages maîtres ou les thèmes s’affiche et contient la page maître ou le thème que vous avez importé.  
  
## <a name="see-also"></a>Voir aussi  
 [Pages maîtres](http://go.microsoft.com/fwlink/?LinkId=184955)   
 [Importation d’éléments d’un Site SharePoint existant](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Création de Pages pour SharePoint](../sharepoint/creating-pages-for-sharepoint.md)   
 [Utilisation de modules pour inclure des fichiers dans la solution](../sharepoint/using-modules-to-include-files-in-the-solution.md)  
  
  