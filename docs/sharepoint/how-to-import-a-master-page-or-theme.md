---
title: 'Procédure : importer une page maître ou un thème | Microsoft Docs'
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
ms.openlocfilehash: 2c5078d31e2dcb7f11e5c19e0f8cb228e2f75d50
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984202"
---
# <a name="how-to-import-a-master-page-or-theme"></a>Procédure : importer une page maître ou un thème
  Vous pouvez attribuer à des pages de votre site SharePoint une apparence cohérente en créant et en utilisant des pages maîtres et des thèmes. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ne fournit pas de modèles pour ces éléments, mais vous pouvez les créer dans SharePoint Designer, puis les importer dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Pour plus d’informations, consultez [bloc de construction : pages et interface utilisateur](/previous-versions/office/developer/sharepoint-2010/ee539040(v=office.14)) sur le site Web de Microsoft.

### <a name="to-import-a-master-page-or-theme"></a>Pour importer une page maître ou un thème

1. Dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], créez ou ouvrez un projet SharePoint.

     Pour plus d’informations sur la création d’un projet SharePoint, consultez modèles de projet [et d’élément de projet SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. Dans la barre de menus, choisissez **Projet** > **Ajouter un nouvel élément**.

3. Dans la boîte de dialogue **Ajouter un nouvel élément** , développez le nœud **SharePoint** , puis choisissez le nœud **2010** .

4. Dans la liste des modèles SharePoint, choisissez le modèle de **module** , puis spécifiez un nom pour le module.

     Un module contient des fichiers (par exemple, des pages maîtres ou des fichiers de thème) pour le déploiement vers un emplacement que vous spécifiez dans SharePoint.

5. Dans le module, supprimez le fichier par défaut, qui est nommé *Sample. txt*.

6. Choisissez le nœud du module.

7. Dans la barre de menus, choisissez **projet** > **Ajouter un élément existant**, puis choisissez la page maître ou le fichier de thème.

     Les fichiers de pages maîtres ont une extension. Master, et les fichiers de thème ont une extension. thmx.

8. Si vous avez ajouté une page maître, définissez son paramètre de **résolution de conflit de déploiement** sur **automatique** dans les propriétés du module.

    > [!NOTE]
    > Des erreurs peuvent se produire si le nom de la page maître est identique au nom d’une page maître existante qui est marquée comme page maître par défaut ou page maître personnalisée. Pour plus d’informations sur la résolution de ce problème, consultez [procédure pas à pas : importer une page maître personnalisée et une page de site avec une image](../sharepoint/walkthrough-import-a-custom-master-page-and-site-page-with-an-image.md).

9. Dans le module, ouvrez *Elements. xml*.

     Vous devez mettre à jour le fichier *Elements. xml* pour faire référence à la page maître ou au thème que vous avez ajouté.

10. Pour une page maître, remplacez la balise de module existante par le balisage suivant.

    ```xml
    <Module Name="[Module Name]" Url="_catalogs/masterpage">
        <File Path="[Module Name]\[Master Page Name].master"
          Url="[Master Page Name].master" Type="GhostableInLibrary" />
    </Module>
    ```

     Pour un thème, remplacez la balise de module existante par le balisage suivant.

    ```xml
    <Module Name="[Module Name]" Url="_catalogs/theme"
        <File Path="[Module Name]\[Theme Name].thmx" Url="[Theme
          Name].thmx" Type="GhostableInLibrary" />
    </Module>
    ```

     Veillez à remplacer les valeurs d’espace réservé par les noms réels du module et par la page maître ou le thème.

     L’attribut `Type="GhostableInLibrary"` indique que l’élément est ajouté à la base de données de contenu, et l’attribut `Url` du module spécifie l’emplacement où stocker le fichier dans la base de données de contenu SharePoint.

11. Pour modifier l’étendue du déploiement d’une page maître, dans **Explorateur de solutions**, ouvrez le fichier de fonctionnalité dans le concepteur de fonctionnalités, puis choisissez une nouvelle étendue de déploiement dans la liste **étendue** .

     Une valeur **Web** signifie que la page maître s’applique uniquement au site Web actuellement spécifié dans le projet. Une valeur de **site** signifie que la page maître s’applique à la collection de sites actuelle, qui comprend tous les sous-sites et le site Web racine. Les autres valeurs ne s’appliquent pas.

    > [!NOTE]
    > Étant donné que les thèmes s’appliquent uniquement au niveau de la collection de sites, nous vous recommandons de ne pas définir l’étendue d’un thème sur une autre valeur que **site**. Des erreurs peuvent se produire si un thème est utilisé dans un sous-site.

12. Dans la barre de menus, choisissez **générer** > **déployer la solution**.

13. Pour vérifier si les fichiers ont été correctement déployés, ouvrez le site SharePoint, choisissez le menu **actions du site** , choisissez la commande **paramètres du site** , puis cliquez sur le lien **pages maîtres** ou sur le lien **thèmes** .

     La liste des pages maîtres ou des thèmes apparaît et contient la page maître ou le thème que vous avez importé.

## <a name="see-also"></a>Voir aussi
- [Pages maîtres](/previous-versions/office/developer/sharepoint-2010/ms443795(v=office.14))
- [Importation d’éléments à partir d’un site SharePoint existant](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [Créer des pages pour SharePoint](../sharepoint/creating-pages-for-sharepoint.md)
- [Utiliser des modules pour inclure des fichiers dans la solution](../sharepoint/using-modules-to-include-files-in-the-solution.md)
