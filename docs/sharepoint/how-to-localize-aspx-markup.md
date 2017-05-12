---
title: "Comment&#160;: localiser le balisage ASPX"
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
  - "localiser du code XML (développement SharePoint dans Visual Studio)"
  - "développement SharePoint dans Visual Studio, localiser"
ms.assetid: 9559a1d1-6558-4c24-a51e-c6ee79432778
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# Comment&#160;: localiser le balisage ASPX
  Les pages [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] \(.aspx\) utilisent généralement des valeurs de chaîne codées en dur.  Pour localiser ces chaînes, remplacez\-les par des expressions qui référencent des ressources localisées.  
  
## Localisation du balisage ASPX  
  
#### Pour localiser le balisage ASPX  
  
1.  Ajoutez des fichiers de ressources séparés : un pour la langue par défaut et un pour chaque langue localisée.  
  
     Si vous localisez le balisage uniquement et pas le code, ajoutez un élément de projet Fichier de ressources global.  Si vous localisez le code et le balisage, ajoutez un élément de projet Fichier de ressources.  
  
    1.  Pour ajouter un fichier de ressources d'agrégation, dans l'**Explorateur de solutions**, ouvrez le menu contextuel d'un élément de projet SharePoint, puis choisissez **Ajouter**, **Nouvel élément**.  Sous le nœud de SharePoint **2010**, sélectionnez le modèle **Fichier de ressources global**.  
  
    2.  Pour ajouter un fichier de ressources d'agrégation, dans l'**Explorateur de solutions**, ouvrez le menu contextuel d'un élément de projet SharePoint, puis choisissez **Ajouter**, **Nouvel élément**.  Sous **Visual Basic** ou le nœud **Visual C\#**, sélectionnez le modèle **Fichier de ressources**.  
  
    > [!NOTE]  
    >  Veillez à ajouter les fichiers de ressources à un élément de projet SharePoint pour activer la propriété Type de déploiement.  Cette propriété est requise plus loin dans cette procédure.  Si votre solution ne contient pas d'élément de projet SharePoint, vous pouvez ajouter un projet SharePoint vide et supprimer son fichier Elements.xml par défaut.  
  
2.  Attribuez au fichier de ressources de langue par défaut le nom de votre choix, avec l'extension .resx, par exemple MyAppResources.resx.  Utilisez le même nom de base pour chaque fichier de ressources localisé, en y ajoutant le [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] de culture.  Par exemple, nommez une ressource localisée en allemand MyAppResources.de\-DE.resx.  
  
3.  Remplacez la valeur de la propriété **Deployment Type** de chaque fichier de ressources par **AppGlobalResource** pour que chaque fichier soit déployé vers le dossier App\_GlobalResources du serveur.  
  
4.  Si vous utilisez les ressources pour localiser le code en plus du balisage ASPX, conservez pour la propriété **Build Action** de chaque fichier la valeur **Ressource incorporée**.  Si vous utilisez uniquement les fichiers de ressources pour localiser le balisage, vous pouvez éventuellement remplacer la valeur de propriété des fichiers par **Contenu**.  Pour plus d'informations, consultez [Localisation de solutions SharePoint](../sharepoint/localizing-sharepoint-solutions.md).  
  
5.  Ouvrez chaque fichier de ressources et ajoutez des chaînes localisées, en utilisant les mêmes ID de chaîne dans chacun des fichiers.  
  
6.  Dans le balisage [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] pour le contrôle ou la page ASPX, remplacez les chaînes codées en dur par des valeurs au format suivant :  
  
    ```  
    <%$Resources:Resource File Name, String ID%>  
    ```  
  
     Par exemple, pour localiser le texte d'un contrôle label dans une page d'application, il vous faudrait changer :  
  
    ```  
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">  
    <asp:Label ID="lbl" runat="server" Text="Label text"></asp:Label>  
    </asp:Content>  
    ```  
  
     en  
  
    ```  
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">  
    <asp:Label ID="lbl" runat="server" Text="<%$Resources:MyAppResources,String1%>"></asp:Label>  
    </asp:Content>  
    ```  
  
7.  Appuyez sur la touche F5 pour générer et exécuter l'application.  
  
8.  Dans SharePoint, modifiez la langue d'affichage par défaut.  
  
     Les chaînes localisées s'affichent dans l'application.  Pour afficher les ressources localisées, un module linguistique qui correspond à la culture du fichier de ressources doit être installé sur le serveur SharePoint.  
  
## Voir aussi  
 [Localisation de solutions SharePoint](../sharepoint/localizing-sharepoint-solutions.md)   
 [Comment : localiser une fonctionnalité](../sharepoint/how-to-localize-a-feature.md)   
 [Comment : ajouter un fichier de ressources](../sharepoint/how-to-add-a-resource-file.md)   
 [Comment : localiser du code](../sharepoint/how-to-localize-code.md)  
  
  