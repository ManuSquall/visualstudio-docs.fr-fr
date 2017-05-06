---
title: "Comment&#160;: marquer des contr&#244;les comme &#233;tant des contr&#244;les s&#233;curis&#233;s"
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
  - "contrôles sécurisés (développement SharePoint dans Visual Studio)"
  - "développement SharePoint dans Visual Studio, outils d'empaquetage avancés"
  - "développement SharePoint dans Visual Studio, contrôles sécurisés"
ms.assetid: 813727d5-6750-407c-a23e-c38dd611e78c
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# Comment&#160;: marquer des contr&#244;les comme &#233;tant des contr&#244;les s&#233;curis&#233;s
  Pour des raisons de sécurité, SharePoint différencie les contrôles Web protégés contre l'injection de script des contrôles Web qui ne le sont pas.  Les contrôles protégés, ou *contrôles sécurisés*, sont accessibles par les utilisateurs non fiables.  Vous pouvez marquer des contrôles comme sécurisés dans la propriété Entrées de contrôle sécurisé d'un élément de projet SharePoint ou dans le **Concepteur de packages** lorsque vous ajoutez un assembly au package.  Pour plus d'informations, consultez  
  
 [modification des paramètres du fichier Web.config](http://go.microsoft.com/fwlink/?LinkId=178965) et [Enregistrement d'un assembly du composant WebPart en tant que contrôle sécurisé](http://go.microsoft.com/fwlink/?LinkId=171013)  
  
> [!IMPORTANT]  
>  Ces procédures sont fournies à des fins d'illustration.  Ne marquez les contrôles comme sécurisés que si vous êtes certain qu'ils le sont.  
  
## Marquage de contrôles comme sécurisés dans la propriété Entrées de contrôle sécurisé  
  
#### Pour marquer des contrôles comme sécurisés ou potentiellement dangereux dans la propriété Entrées de contrôle sécurisé  
  
1.  Créez une solution SharePoint avec un projet Composant Visual Web Part.  
  
2.  Ajoutez deux contrôles au WebPart : une zone de texte et un bouton.  Conservez les valeurs par défaut des noms, à savoir TextBox1 et Button1, respectivement.  
  
3.  Ajoutez deux entrées à la propriété **Entrées de contrôle sécurisé** du composant WebPart.  Pour ce faire, cliquez sur le bouton de sélection \(![Bouton de sélection du concepteur ASP.NET mobile](../sharepoint/media/mwellipsis.png "Bouton de sélection du concepteur ASP.NET mobile")\) en regard de la propriété **Entrées de contrôle sécurisé** dans la fenêtre **Propriétés**.  
  
     La boîte de dialogue **Entrées de contrôle sécurisé** apparaît.  
  
4.  Dans la boîte de dialogue **Entrées de contrôle sécurisé**, cliquez deux fois sur le bouton **Ajouter** pour ajouter deux entrées de contrôle sécurisé au volet **Membres** : une pour le bouton et l'autre pour la zone de texte.  
  
5.  Cliquez sur la première entrée de contrôle sécurisé et remplacez la valeur de sa propriété **Sécurisé** par **False**, celle de sa propriété **Nom de type** par **Button1** et celle de sa propriété **Protégé contre les scripts** par **False**.  
  
     Cette étape identifie le contrôle bouton comme un contrôle potentiellement dangereux.  
  
6.  Cliquez sur la deuxième entrée de contrôle sécurisé dans la liste.  Conservez les valeurs de ses propriétés **Sécurisé** la valeur **True**. Affectez à sa propriété **Nom de type** la valeur**TextBox1** et à sa propriété **Protégé contre les scripts** la valeur **True**.  
  
     Le contrôle de zone de texte est maintenant marqué comme un contrôle qui est sécurisé contre l'injection de script.  
  
7.  Sélectionnez le bouton **OK** pour fermer la boîte de dialogue.  
  
## Marquage de contrôles comme sécurisés dans le Concepteur de packages  
  
#### Pour marquer des contrôles comme sécurisés ou potentiellement dangereux dans le Concepteur de packages  
  
1.  Créez une solution SharePoint avec un projet Composant Visual Web Part.  
  
2.  Ajoutez deux contrôles au WebPart : une zone de texte et un bouton.  Conservez les valeurs par défaut des noms, à savoir TextBox1 et Button1, respectivement.  
  
     Prenez note de l'espace de noms du contrôle, car il est utilisé ultérieurement.  
  
3.  Dans la barre de menu, choisissez **Générer**, **Générer la solution** pour générer le projet.  
  
4.  Créez une autre solution SharePoint.  
  
5.  Dans l'**Explorateur de solutions**, ouvrez le menu contextuel du fichier Package.Package, puis choisissez **Ouvrir** pour ouvrir le **Concepteur de packages**.  
  
6.  Dans le **Concepteur de packages**, cliquez sur l'onglet **Avancé**.  
  
7.  Sous **Assemblys supplémentaires**, cliquez sur le bouton **Ajouter** puis sélectionnez **Ajouter un assembly existant** dans la liste.  
  
8.  Dans la boîte de dialogue **Ajouter un assembly existant**, cliquez sur le bouton de sélection \(![Bouton de sélection du concepteur ASP.NET mobile](../sharepoint/media/mwellipsis.png "Bouton de sélection du concepteur ASP.NET mobile")\) en regard de **Chemin d'accès source**.  
  
9. Choisissez l'assembly de la solution SharePoint que vous avez créée à l'étape 1, puis cliquez sur le bouton **Ouvrir**.  
  
10. Dans cet exemple, conservez la valeur GlobalAssemblyCache pour l'option **Cible de déploiement**.  
  
     Cette étape provoque le déploiement de l'assembly dans le Global Assembly Cache \(GAC\) du système.  Si vous souhaitez que l'assembly se déploie dans le dossier \(Bin\) de l'application Web, sélectionnez à la place cette option.  Pour plus d'informations, consultez [Composants webpart de déploiement dans la base de SharePoint](http://go.microsoft.com/fwlink/?LinkId=177509).  
  
11. Dans la zone **Contrôle sécurisés**, cliquez sur le bouton **Cliquez ici pour ajouter un nouvel élément**.  
  
12. Entrez les valeurs pour les propriétés à partir du tableau suivant.  
  
    |Nom de la propriété|Valeur|  
    |-------------------------|------------|  
    |Espace de noms|Espace de noms qualifié complet pour le contrôle, tel que **BdcModelProject1.VisualWebPart1**.|  
    |Nom de type|Button1|  
    |Nom de l'assembly|Nom d'assembly fort, tel que Microsoft.Office.SharePoint.ClientExtensions, Version\=14.0.0.0, Culture\=neutral, PublicKeyToken\=71e9bce111e9429c.|  
    |Sécurisé|Désactivez la case à cocher **Sécurisé**.|  
    |Protégé contre les scripts|N'activez pas la case à cocher **Protégé contre les scripts**.|  
  
    > [!NOTE]  
    >  La valeur **Assembly Name** pour les assemblys ajoutés via l'onglet **Avancé** du **Concepteur de packages** ne peut pas être un jeton ; il doit s'agir d'un assembly avec un nom fort.  Pour plus d'informations, consultez [Création et utilisation d'assemblys avec nom fort](http://go.microsoft.com/fwlink/?LinkId=177513).  
  
13. Choisissez la touche TAB pour créer une entrée de contrôle sécurisé.  
  
14. Cliquez de nouveau sur le bouton **Cliquez ici pour ajouter une nouvelle clause**.  
  
15. Entrez les valeurs pour les propriétés à partir du tableau suivant.  
  
    |Nom de la propriété|Valeur|  
    |-------------------------|------------|  
    |Espace de noms|Espace de noms qualifié complet pour le contrôle, tel que **BdcModelProject1.VisualWebPart1**.|  
    |Nom de type|TextBox1|  
    |Nom de l'assembly|Nom d'assembly fort, tel que Microsoft.Office.SharePoint.ClientExtensions, Version\=14.0.0.0, Culture\=neutral, PublicKeyToken\=71e9bce111e9429c.|  
    |Sécurisé|Activez la case à cocher **Sécurisé**.|  
    |Protégé contre les scripts|Activez la case à cocher **Protégé contre les scripts**.|  
  
16. Choisissez la touche TAB, puis cliquez sur le bouton **OK** pour fermer la boîte de dialogue.  
  
## Voir aussi  
 [Fourniture d'informations de création de packages et de déploiement dans des éléments de projet](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [Empaquetage et déploiement de solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  