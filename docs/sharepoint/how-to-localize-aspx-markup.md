---
title: 'Comment : localiser le balisage ASPX | Microsoft Docs'
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
- localizing XML [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 68e74f743c1c00bb940a89039e4fd5cfcf8e63e4
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37118991"
---
# <a name="how-to-localize-aspx-markup"></a>Comment : localiser le balisage ASPX
  [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] pages (.aspx) utilisent généralement des valeurs de chaîne codées en dur. Pour localiser ces chaînes, remplacez-les par les expressions qui référencent des ressources localisées.  
  
## <a name="localize-aspx-markup"></a>Localiser le balisage ASPX  
  
#### <a name="to-localize-aspx-markup"></a>Pour localiser le balisage ASPX  
  
1.  Ajouter des fichiers de ressources distincts : un pour la langue par défaut et un pour chaque langue localisée.  
  
     Si vous localisez le balisage uniquement et pas de code, ajoutez un élément de projet fichier de ressources globales. Si vous localisez le code et le balisage, ajoutez un élément de projet fichier de ressources.  
  
    1.  Pour ajouter un fichier de ressources globales dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour un élément de projet SharePoint, puis choisissez **ajouter** > **un nouvel élément**. Sous SharePoint **2010** nœud, choisissez le **fichier de ressources Global** modèle.  
  
    2.  Pour ajouter un fichier de ressources dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour un élément de projet SharePoint, puis choisissez **ajouter** > **un nouvel élément**. Sous le **Visual Basic** ou **Visual C#** nœud, choisissez le **fichier de ressources** modèle.  
  
    > [!NOTE]  
    >  Veillez à ajouter les fichiers de ressources à un élément de projet SharePoint pour activer la propriété Type de déploiement. Cette propriété est requise plus loin dans cette procédure. Si votre solution n’a pas un élément de projet SharePoint, vous pouvez ajouter un projet SharePoint vide et supprimer sa valeur par défaut *Elements.xml* fichier.  
  
2.  Nommez le fichier de ressources de langue par défaut de votre choix, avec un *.resx* extension, par exemple MyAppResources.resx. Utiliser le même nom de base pour chaque fichier de ressources localisé, mais ajouter la culture [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]. Par exemple, nom un allemand localisé ressource *MyAppResources.de-de.resx*.  
  
3.  Modifiez la valeur de la **Type de déploiement** propriété de chaque fichier de ressources à **AppGlobalResource** pour provoquer la déployer sur le dossier App_GlobalResources du serveur.  
  
4.  Si vous utilisez les ressources pour localiser le code en plus du balisage ASPX, conservez la valeur de la **Action de génération** propriété de chaque fichier en tant que **ressource incorporée**. Si vous utilisez les fichiers de ressources uniquement pour localiser le balisage, vous pouvez éventuellement modifier la valeur de propriété des fichiers à **contenu**. Pour plus d’informations, consultez [solutions SharePoint localiser](../sharepoint/localizing-sharepoint-solutions.md).  
  
5.  Ouvrez chaque fichier de ressources et ajoutez des chaînes localisées, à l’aide de la même chaîne ID dans chaque fichier.  
  
6.  Dans le [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] balisage pour la page ASPX ou un contrôle, remplacez les chaînes codées en dur avec des valeurs qui utilisent le format suivant :  
  
    ```aspx-csharp  
    <%$Resources:Resource File Name, String ID%>  
    ```  
  
     Par exemple, pour localiser le texte d’un contrôle label sur une page d’application, vous modifieriez :  
  
    ```aspx-csharp  
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">  
    <asp:Label ID="lbl" runat="server" Text="Label text"></asp:Label>  
    </asp:Content>  
    ```  
  
     par celle-ci :  
  
    ```aspx-csharp  
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">  
    <asp:Label ID="lbl" runat="server" Text="<%$Resources:MyAppResources,String1%>"></asp:Label>  
    </asp:Content>  
    ```  
  
7.  Choisissez le **F5** clé pour générer et exécuter l’application.  
  
8.  Dans SharePoint, modifiez la langue d’affichage à partir de la valeur par défaut.  
  
     Les chaînes localisées s’affichent dans l’application. Pour afficher les ressources localisées, le serveur SharePoint doit avoir installé un module linguistique qui correspond à la culture du fichier de ressources.  
  
## <a name="see-also"></a>Voir aussi
 [Localiser des solutions SharePoint](../sharepoint/localizing-sharepoint-solutions.md)   
 [Comment : localiser une fonctionnalité](../sharepoint/how-to-localize-a-feature.md)   
 [Comment : ajouter un fichier de ressources](../sharepoint/how-to-add-a-resource-file.md)   
 [Comment : localiser du code](../sharepoint/how-to-localize-code.md)  
  
