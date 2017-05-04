---
title: "Comment&#160;: importer une page ma&#238;tre ou un th&#232;me | Microsoft Docs"
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
helpviewer_keywords: 
  - "importer des éléments (développement SharePoint dans Visual Studio)"
  - "développement SharePoint dans Visual Studio, importer des éléments"
ms.assetid: 8b446cca-2adb-457b-bbfd-891209290e80
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# Comment&#160;: importer une page ma&#238;tre ou un th&#232;me
  Vous pouvez donner aux pages sur votre site SharePoint une apparence cohérente en créant et en utilisant les pages maître et les thèmes.  Bien que [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ne fournisse pas de modèles pour ces éléments, vous pouvez en créer dans SharePoint Designer, puis les importer dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Pour plus d'informations, consultez [Bloc de construction : Pages et l'interface utilisateur](http://go.microsoft.com/fwlink/?LinkID=182095) sur le site Web Microsoft.  
  
### Pour importer une page maître ou un thème  
  
1.  Dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], ouvrez ou créez un projet SharePoint.  
  
     Pour plus d'informations sur la création d'un plan de projet SharePoint, consultez [Modèles de projets et d'éléments de projet SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  Dans la barre de menus, choisissez **Projet**, **Ajouter un nouvel élément**.  
  
3.  Dans la boîte de dialogue **Ajouter un nouvel élément**, développez le noeud **SharePoint**, puis sélectionnez le noeud **2010**.  
  
4.  Dans la liste des modèles de SharePoint, choisissez le modèle **Module**, puis spécifiez un nom pour le module.  
  
     Un module contient des fichiers, \(par exemple des fichiers de page maître ou de thème\) à déployer vers un emplacement spécifié dans SharePoint.  
  
5.  Dans le module, supprimez le fichier par défaut, appelé Sample.txt.  
  
6.  Choisissez le noeud Module.  
  
7.  Dans la barre de menus, cliquez sur **Projet**, **Ajouter un élément existant**, puis sélectionnez la page maître ou le fichier de thème.  
  
     Les fichiers de page maître portent l'extension .master et les fichiers de thème portent l'extension .thmx.  
  
8.  Si vous avez ajouté une page maître, modifiez son paramètre **Résolution de conflit de déploiement** en **Automatique** dans les propriétés du module.  
  
    > [!NOTE]  
    >  Des erreurs peuvent avoir lieu si le nom de la page maître est le même que le nom d'une page maître existante marquée comme page maître par défaut ou page maître personnalisée, des erreurs peuvent se produire.  Pour plus d'informations sur la résolution de ce problème, consultez [Procédure pas à pas : importation d'une page maître et d'une page de site personnalisées avec une image](../sharepoint/walkthrough-import-a-custom-master-page-and-site-page-with-an-image.md).  
  
9. Dans le module, ouvrez Elements.xml.  
  
     Vous devez mettre à jour le fichier Elements.xml pour référencer la page maître ou le thème que vous venez d'ajouter.  
  
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
  
     Veillez à remplacer les valeurs d'espace réservé par les noms réels du module et de la page maître ou du thème.  
  
     L'attribut `Type="GhostableInLibrary"` indique que l'élément est ajouté à la base de données de contenu, et l'attribut `Url` du module spécifie l'emplacement de stockage du fichier dans la base de données de contenu SharePoint.  
  
11. Pour modifier l'étendue de déploiement pour une page maître, dans **Explorateur de solutions**, ouvrez le fichier de fonctionnalités dans le concepteur de fonctionnalité, puis choisissez une nouvelle étendue de déploiement de la liste **Étendue**.  
  
     La valeur **Web** signifie que la page maître s'applique uniquement au site Web actuellement spécifié dans le projet.  La valeur **Site** signifie que la page maître s'applique à la collection de sites actuelle, qui inclut tous les sous\-sites et le Web racine.  Les autres valeurs ne s'appliquent pas.  
  
    > [!NOTE]  
    >  Étant donné que les thèmes s'appliquent uniquement au niveau de la collection de sites, nous vous recommandons de ne pas affecter une autre valeur que **Site** à la portée d'un thème.  Des erreurs peuvent se produire si un thème est utilisé dans un sous\-site.  
  
12. Dans la barre de menus, choisissez **Générer**, puis **Déployer la solution**.  
  
13. Pour vérifier que les fichiers ont été déployés correctement, ouvrez le site SharePoint, choisissez le menu **Actions de site**, choisissez la commande **Paramètres du site**, puis cliquez sur le lien **Pages maîtres** ou le lien **Thèmes**.  
  
     La liste des pages maître ou de thèmes mentionnés apparaît et affiche la page maître ou le thème que vous avez importé.  
  
## Voir aussi  
 [Pages maîtres](http://go.microsoft.com/fwlink/?LinkId=184955)   
 [Importation d'éléments d'un site SharePoint existant](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Création de pages pour SharePoint](../sharepoint/creating-pages-for-sharepoint.md)   
 [Utilisation de modules pour inclure des fichiers dans la solution](../sharepoint/using-modules-to-include-files-in-the-solution.md)  
  
  