---
title: "Comment : localiser le balisage ASPX | Documents Microsoft"
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
- localizing XML [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 99683e590a2bc6638a809bd3d14486c951a2ad02
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-localize-aspx-markup"></a>Comment : localiser le balisage ASPX
  [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]pages (.aspx) utilisent généralement des valeurs de chaîne codée en dur. Pour localiser ces chaînes, remplacez-les par des expressions qui référencent des ressources localisées.  
  
## <a name="localizing-aspx-markup"></a>Localisation du balisage ASPX  
  
#### <a name="to-localize-aspx-markup"></a>Pour localiser le balisage ASPX  
  
1.  Ajouter des fichiers de ressources séparés : un pour la langue par défaut et un pour chaque langue localisée.  
  
     Si vous localisez le balisage uniquement et pas de code, ajoutez un élément de projet du fichier de ressources Global. Si vous localisez le code et le balisage, ajoutez un élément de projet du fichier de ressources.  
  
    1.  Pour ajouter un fichier de ressources globales dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour un élément de projet SharePoint, puis choisissez **ajouter**, **un nouvel élément**. Sous SharePoint **2010** nœud, choisissez le **fichier de ressources Global** modèle.  
  
    2.  Pour ajouter un fichier de ressources dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour un élément de projet SharePoint, puis choisissez **ajouter**, **un nouvel élément**. Sous le **Visual Basic** ou **Visual C#** nœud, choisissez le **fichier de ressources** modèle.  
  
    > [!NOTE]  
    >  Veillez à ajouter les fichiers de ressources à un élément de projet SharePoint pour activer la propriété Type de déploiement. Cette propriété est requise plus loin dans cette procédure. Si votre solution ne dispose pas d’un élément de projet SharePoint, vous pouvez ajouter un projet SharePoint vide et supprimer son fichier Elements.xml de valeur par défaut.  
  
2.  Nommez le fichier de ressources de langue par défaut de votre choix, avec l’extension .resx, par exemple MyAppResources.resx. Utiliser le même nom de base pour chaque fichier de ressources localisé, mais ajouter la culture [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]. Par exemple, nommez une ressource localisée en allemand MyAppResources.de-de.resx.  
  
3.  Modifiez la valeur de la **Type de déploiement** propriété de chaque fichier de ressources à **par AppGlobalResource** pour les déployer sur le dossier du serveur App_GlobalResources faire.  
  
4.  Si vous utilisez les ressources pour localiser le code en plus du balisage ASPX, conservez la valeur de la **Action de génération** propriété de chaque fichier en tant que **ressource incorporée**. Si vous utilisez les fichiers de ressources uniquement pour localiser le balisage, vous pouvez éventuellement modifier la valeur de propriété des fichiers à **contenu**. Pour plus d’informations, consultez [localiser des Solutions SharePoint](../sharepoint/localizing-sharepoint-solutions.md).  
  
5.  Ouvrez chaque fichier de ressources et ajouter des chaînes localisées, à l’aide de la même chaîne ID dans chaque fichier.  
  
6.  Dans la [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] balisage de la page ASPX ou un contrôle, remplacez les chaînes codées en dur avec des valeurs qui utilisent le format suivant :  
  
    ```  
    <%$Resources:Resource File Name, String ID%>  
    ```  
  
     Par exemple, pour localiser le texte d’un contrôle label sur une page d’application, modifier :  
  
    ```  
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">  
    <asp:Label ID="lbl" runat="server" Text="Label text"></asp:Label>  
    </asp:Content>  
    ```  
  
     par celle-ci :  
  
    ```  
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">  
    <asp:Label ID="lbl" runat="server" Text="<%$Resources:MyAppResources,String1%>"></asp:Label>  
    </asp:Content>  
    ```  
  
7.  Appuyez sur la touche F5 pour générer et exécuter l’application.  
  
8.  Dans SharePoint, modifiez la langue d’affichage à partir de la valeur par défaut.  
  
     Les chaînes localisées s’affichent dans l’application. Pour afficher les ressources localisées, le serveur SharePoint doit disposer d’un module linguistique qui correspond à la culture du fichier de ressources.  
  
## <a name="see-also"></a>Voir aussi  
 [Localisation de Solutions SharePoint](../sharepoint/localizing-sharepoint-solutions.md)   
 [Comment : localiser une fonctionnalité](../sharepoint/how-to-localize-a-feature.md)   
 [Comment : ajouter un fichier de ressources](../sharepoint/how-to-add-a-resource-file.md)   
 [Guide pratique pour localiser du code](../sharepoint/how-to-localize-code.md)  
  
  