---
title: 'Comment : marquer des contrôles comme des contrôles sécurisés | Documents Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, safe controls
- SharePoint development in Visual Studio, advanced packaging tools
- safe controls [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d703beb24821663b08ed69238fcf27e2a752d64b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-mark-controls-as-safe-controls"></a>Comment : marquer des contrôles comme étant des contrôles sécurisés
  Pour la sécurité, SharePoint différencie les contrôles Web qui sont protégés contre l’injection de script et des contrôles Web qui ne sont pas. Protégé par des contrôles, ou *contrôles sécurisés*, soit accessible aux utilisateurs non autorisés. Vous pouvez marquer des contrôles comme sécurisés dans la propriété entrées de contrôle sécurisé d’un élément de projet SharePoint ou dans le **Concepteur de packages** lorsque vous ajoutez un assembly au package. Pour plus d'informations, consultez  
  
 [Modification des paramètres du fichier Web.config](http://go.microsoft.com/fwlink/?LinkId=178965) et [l’inscription d’un Assembly de composant WebPart en tant que](http://go.microsoft.com/fwlink/?LinkId=171013).  
  
> [!IMPORTANT]  
>  Ces procédures sont à titre d’illustration. Marquer des contrôles sécurisés uniquement si vous êtes certain qu’ils sont sécurisés.  
  
## <a name="marking-safe-controls-in-the-safe-control-entries-property"></a>Le marquage des contrôles sécurisés dans la propriété entrées de contrôle sécurisé  
  
#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-safe-control-entries-property"></a>Pour marquer des contrôles comme sécurisés ou potentiellement dangereux dans la propriété entrées de contrôle sécurisé  
  
1.  Créez une solution SharePoint avec un projet de composant Visual Web Part.  
  
2.  Ajoutez deux contrôles au composant WebPart : une zone de texte et un bouton. Conservez les noms de leurs valeurs par défaut, TextBox1 et Button1, respectivement.  
  
3.  Ajouter deux entrées pour le WebPart **entrées de contrôle sécurisé** propriété. Pour ce faire, choisissez le bouton de sélection (![ellipse de concepteur ASP.NET Mobile](../sharepoint/media/mwellipsis.gif "ellipse de concepteur ASP.NET Mobile")) situé en regard du **entrées de contrôle sécurisé** propriété dans le  **Propriétés** fenêtre.  
  
     Le **entrées de contrôle sécurisé** boîte de dialogue s’affiche.  
  
4.  Dans le **entrées de contrôle sécurisé** boîte de dialogue, choisissez le **ajouter** bouton à deux reprises pour ajouter deux entrées de contrôle sécurisé à le **membres** volet : un pour le bouton et un pour la zone de texte.  
  
5.  Choisissez la première entrée de contrôle sécurisé, puis remplacez la valeur de sa **Safe** propriété **False**, ses **nom de Type** propriété **Button1**et son **protégé contre les scripts** propriété **False**.  
  
     Cette étape identifie le contrôle de bouton comme un contrôle non fiable.  
  
6.  Dans la liste, choisissez la deuxième entrée de contrôle sécurisé. Laissez la valeur de son **Safe** propriété en tant que **True** et définir son **nom de Type** propriété **TextBox1** et son **-Safe Par rapport à Script** propriété **True**.  
  
     Le contrôle de zone de texte est désormais marqué comme un contrôle qui est protégé contre l’injection de script.  
  
7.  Choisissez le bouton **OK** pour fermer la boîte de dialogue.  
  
## <a name="marking-safe-controls-in-the-package-designer"></a>Le marquage des contrôles sécurisés dans le Concepteur de packages  
  
#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-package-designer"></a>Pour marquer des contrôles comme safe ou unsafe dans le Concepteur de packages  
  
1.  Créez une solution SharePoint avec un projet de composant Visual Web Part.  
  
2.  Ajoutez deux contrôles au composant WebPart : une zone de texte et un bouton. Conservez les noms de leurs valeurs par défaut, TextBox1 et Button1, respectivement.  
  
     Prenez note de l’espace de noms du contrôle, car elle est utilisée ultérieurement.  
  
3.  Dans la barre de menus, choisissez **générer**, **générer la Solution** pour générer le projet.  
  
4.  Créer une autre solution de SharePoint.  
  
5.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le fichier de package, puis choisissez **ouvrir** pour ouvrir le **Concepteur de packages**.  
  
6.  Dans le **Concepteur de packages**, choisissez le **avancé** onglet.  
  
7.  Sous **des assemblys supplémentaires**, choisissez le **ajouter** bouton, puis choisissez **ajouter un Assembly existant** dans la liste.  
  
8.  Dans le **ajouter un Assembly existant** boîte de dialogue, choisissez le bouton de sélection (![ellipse de concepteur ASP.NET Mobile](../sharepoint/media/mwellipsis.gif "ellipse de concepteur ASP.NET Mobile")) situé en regard  **Chemin d’accès source**.  
  
9. Choisissez l’assembly à partir de la solution SharePoint que vous avez créé à l’étape 1, puis le **ouvrir** bouton.  
  
10. Pour cet exemple, laissez le **cible de déploiement** option GlobalAssemblyCache.  
  
     Cette étape, l’assembly à déployer dans le Global Assembly Cache (GAC) du système. Si vous souhaitez que l’assembly à déployer dans le dossier d’application (emplacement) de Web, sélectionnez cette option à la place. Pour plus d’informations, consultez [déploiement de composants WebPart dans SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177509).  
  
11. Dans le **contrôles sécurisés** , choisissez le **cliquez ici pour ajouter un nouvel élément** bouton.  
  
12. Entrez les valeurs pour les propriétés dans le tableau suivant.  
  
    |Nom de la propriété|Value|  
    |-------------------|-----------|  
    |Espace de noms|L’espace de noms qualifié complet pour le contrôle, tel que **BdcModelProject1.VisualWebPart1**.|  
    |Nom de type|Button1|  
    |Nom de l'assembly|Nom d’un assembly à fort, tel que : Microsoft.Office.SharePoint.ClientExtensions, Version = 14.0.0.0, Culture = neutral, PublicKeyToken = 71e9bce111e9429c.|  
    |Safe|Désactivez le **Safe** case à cocher.|  
    |Protégé contre les scripts|Laissez le **protégé contre les scripts** case à cocher.|  
  
    > [!NOTE]  
    >  Le **nom de l’Assembly** valeur pour les assemblys ajoutés via la **avancé** onglet de la **Concepteur de packages** ne peut pas un jeton, il doit être un assembly à nom fort. Pour plus d’informations, consultez [Création et utilisation d’assemblys avec nom fort](http://go.microsoft.com/fwlink/?LinkId=177513).  
  
13. Choisissez la touche Tab pour créer une autre entrée de contrôle sécurisé.  
  
14. Choisissez le **cliquez ici pour ajouter un nouvel élément** bouton Nouveau.  
  
15. Entrez les valeurs pour les propriétés dans le tableau suivant.  
  
    |Nom de la propriété|Value|  
    |-------------------|-----------|  
    |Espace de noms|L’espace de noms qualifié complet pour le contrôle, tel que **BdcModelProject1.VisualWebPart1**.|  
    |Nom de type|TextBox1|  
    |Nom de l'assembly|Nom d’un assembly à fort, tel que : Microsoft.Office.SharePoint.ClientExtensions, Version = 14.0.0.0, Culture = neutral, PublicKeyToken = 71e9bce111e9429c.|  
    |Safe|Sélectionnez le **Safe** case à cocher.|  
    |Protégé contre les scripts|Sélectionnez le **protégé contre les scripts** case à cocher.|  
  
16. Choisissez la touche Tab, puis le **OK** pour fermer la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [En fournissant l’empaquetage et du déploiement dans les éléments de projet](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [Empaquetage et déploiement de solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  