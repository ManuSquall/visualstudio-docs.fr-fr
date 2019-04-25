---
title: 'Procédure : Importer une Page maître ou un thème | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1be553955abdc42c2a9b4d09ff857e9236b1a002
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60081904"
---
# <a name="how-to-import-a-master-page-or-theme"></a>Procédure : Importer une page maître ou un thème
  Vous pouvez attribuer aux pages sur votre site SharePoint une apparence cohérente en créant et en utilisant des thèmes et des pages maîtres. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ne fournit pas les modèles pour ces éléments, mais vous pouvez les créer dans SharePoint Designer et importez-les dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Pour plus d’informations, consultez [bloc de construction : Pages et l’Interface utilisateur](http://go.microsoft.com/fwlink/?LinkID=182095) sur le site Web Microsoft.

### <a name="to-import-a-master-page-or-theme"></a>Pour importer une page maître ou un thème

1. Dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], créez ou ouvrez un projet SharePoint.

     Pour plus d’informations sur la création d’un projet SharePoint, consultez [SharePoint modèles d’élément de projet et le projet](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. Dans la barre de menus, choisissez **Projet** > **Ajouter un nouvel élément**.

3. Dans le **ajouter un nouvel élément** boîte de dialogue, développez le **SharePoint** nœud, puis choisissez le **2010** nœud.

4. Dans la liste de modèles SharePoint, choisissez le **Module** modèle, puis spécifiez un nom pour le module.

     Un module contient des fichiers (par exemple, page maître ou des fichiers de thème) pour le déploiement vers un emplacement que vous spécifiez dans SharePoint.

5. Dans le module, supprimez le fichier par défaut, qui est nommé *Sample.txt*.

6. Choisissez le nœud du module.

7. Dans la barre de menus, choisissez **projet** > **ajouter un élément existant**, puis choisissez le fichier de page ou un thème principal.

     Les fichiers de page maître portent l’extension .master et fichiers de thème portent l’extension .thmx.

8. Si vous avez ajouté une page maître, modifiez son **Deployment Conflict Resolution** à **automatique** dans les propriétés du module.

    > [!NOTE]
    >  Erreurs peuvent se produire si le nom de la page maître est le même que le nom d’une page maître existante qui est marquée comme Page maître par défaut ou Page maître personnalisée. Pour plus d’informations sur la façon de résoudre ce problème, consultez [procédure pas à pas : Importer une page maître personnalisée et la page de site avec une image](../sharepoint/walkthrough-import-a-custom-master-page-and-site-page-with-an-image.md).

9. Dans le module, ouvrez *Elements.xml*.

     Vous devez mettre à jour le *Elements.xml* fichier à référencer la page maître ou un thème que vous avez ajouté.

10. Pour une page maître, remplacez le balisage de module existant par le balisage suivant.

    ```xml
    <Module Name="[Module Name]" Url="_catalogs/masterpage">
        <File Path="[Module Name]\[Master Page Name].master"
          Url="[Master Page Name].master" Type="GhostableInLibrary" />
    </Module>
    ```

     Pour un thème, remplacez le balisage de module existant par le balisage suivant.

    ```xml
    <Module Name="[Module Name]" Url="_catalogs/theme"
        <File Path="[Module Name]\[Theme Name].thmx" Url="[Theme
          Name].thmx" Type="GhostableInLibrary" />
    </Module>
    ```

     Veillez à remplacer les valeurs d’espace réservé par les noms réels du module et la page maître ou un thème.

     L’attribut `Type="GhostableInLibrary"` indique que l’élément est ajouté à la base de données de contenu et le `Url` attribut du module spécifie l’emplacement stocker le fichier dans la base de données de contenu SharePoint.

11. Pour modifier l’étendue de déploiement pour une page maître, dans **l’Explorateur de solutions**, ouvrez le fichier de fonctionnalité dans le Concepteur de fonctionnalités, puis choisissez une nouvelle portée de déploiement à partir de la **étendue** liste.

     La valeur **Web** signifie que la page maître s’applique uniquement au site Web qui est actuellement spécifié dans le projet. La valeur **Site** signifie que la page maître s’applique à la collection de sites actuelle, qui inclut tous les sous-sites et le site web racine. Les autres valeurs ne s’appliquent pas.

    > [!NOTE]
    >  Étant donné que les thèmes s’appliquent uniquement au niveau de la collection de sites, nous recommandons que vous ne définissez pas la portée d’un thème sur n’importe quelle autre que **Site**. Erreurs peuvent se produire si un thème est utilisé dans un sous-site.

12. Dans la barre de menus, choisissez **Build** > **déployer la Solution**.

13. Pour vérifier si les fichiers ont été correctement déployées, ouvrez le site SharePoint, choisissez le **Actions du Site** menu, choisissez le **paramètres du Site** commande, puis choisissez le **Pages maîtres**  lien ou le **thèmes** lien.

     La liste des pages maîtres ou thèmes s’affiche et contient la page maître ou le thème que vous avez importé.

## <a name="see-also"></a>Voir aussi
- [Pages maîtres](http://go.microsoft.com/fwlink/?LinkId=184955)
- [Importation d’éléments d’un site SharePoint existant](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [Créer des pages pour SharePoint](../sharepoint/creating-pages-for-sharepoint.md)
- [Utiliser des modules pour inclure des fichiers dans la solution](../sharepoint/using-modules-to-include-files-in-the-solution.md)
