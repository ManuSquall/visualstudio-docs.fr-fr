---
title: "Ins&#233;rer des contr&#244;les et modifier leur comportement dans le concepteur XAML | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a80fff74-bf01-41c9-ab85-ada7a873c3a9
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# Ins&#233;rer des contr&#244;les et modifier leur comportement dans le concepteur XAML
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les contrôles permettent aux utilisateurs d'interagir avec votre application. Elles peuvent s'avérer utiles pour collecter des informations et effectuer des actions, comme animer un objet ou interroger une source de données.  
  
 **Dans cette rubrique :**  
  
-   [Ajouter des contrôles à la planche graphique](#Insert)  
  
-   [Rendre les contrôles actifs](#Modify)  
  
##  <a name="Insert"></a> Ajouter des contrôles à la planche graphique  
 Vous pouvez faire glisser des contrôles du panneau **Composants** vers la **planche graphique**, puis les modifier dans la fenêtre **Propriétés**.  
  
 ![Blend &#45; Composants &#45; FlipView](../designers/media/blend_assetsflipview_xaml.png "blend\_AssetsFlipView\_XAML")  
  
 Ces vidéos vous montrent comment utiliser quelques\-uns des contrôles les plus courants.  
  
|Contrôle|Regardez une courte vidéo :|  
|--------------|---------------------------------|  
|`Menu` ![](../designers/media/015a263c-0b2b-4253-ac57-b86fcb8c9591.png "015a263c\-0b2b\-4253\-ac57\-b86fcb8c9591")|![Configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Ajouter les contrôles](https://www.youtube.com/watch?v=ra4AHfgD4Ys&list=PLBDF977B2F1DAB358&index=45)|  
|`Button` ![](../designers/media/05df1779-a68f-436b-b834-a91b7995a3ec.png "05df1779\-a68f\-436b\-b834\-a91b7995a3ec")|![Configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Concevoir un bouton](http://www.popscreen.com/v/6A4gb/Microsoft-Expression-Blend-Designing-a-Button)|  
|`Textblock` ![](../designers/media/42165963-00f7-4a33-abcd-b0849edebada.png "42165963\-00f7\-4a33\-abcd\-b0849edebada")|![Configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Ajouter des images à un bloc de texte](http://www.popscreen.com/v/6A4du/Microsoft-Expression-Blend-Adding-Images-to-a-TextBlock)|  
|`Slider` ![](../designers/media/bf689d92-3c74-4218-815c-e98c930ac189.png "bf689d92\-3c74\-4218\-815c\-e98c930ac189")|![Configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Créer un curseur avec une info\-bulle](http://www.bing.com/videos/search?q=slider%20expression%20blend&qs=n&form=QBVR&pq=slider%20expression%20blend&sc=1-23&sp=-1&sk=#view=detail&mid=F1BB7DB91B2772A8CA2AF1BB7DB91B2772A8CA2A)|  
|`GridSplitter` ![](../designers/media/d08d529f-a27e-4a8f-95aa-8a4e8b4ee7be.png "d08d529f\-a27e\-4a8f\-95aa\-8a4e8b4ee7be")|![Configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Utiliser un contrôle GridSplitter](http://msdn.microsoft.com/expression/cc188687.aspx)|  
  
### Créer un contrôle à partir d’une image, d’une forme ou d’un tracé  
 Vous pouvez transformer n'importe quel objet en contrôle.  
  
 ![Créer un contrôle dans Blend, boîte de dialogue](../designers/media/blend_makeintocontrol_xaml.png "blend\_MakeIntoControl\_XAML")  
  
 Par exemple, imaginez une image de téléviseur au milieu d'une page. Vous pourriez créer des contrôles à partir de petites images représentant des boutons de téléviseur. Les utilisateurs pourraient ensuite cliquer sur ces boutons pour changer de chaîne.  
  
 Cela serait possible, car les boutons seraient dès lors des contrôles. Les contrôles permettent de répondre aux interactions de l'utilisateur \(dans ce cas, le clic de l'utilisateur sur un bouton\).  
  
 Pour créer un contrôle, sélectionnez un objet. Ensuite, dans le menu **Outils**, cliquez sur **Créer un contrôle**.  
  
##  <a name="Modify"></a> Rendre les contrôles actifs  
 Les contrôles peuvent effectuer des actions quand les utilisateurs interagissent avec eux. Par exemple, ils peuvent démarrer une animation, mettre à jour une source de données ou lire une vidéo.  
  
 Pour rendre des contrôles actifs, vous devez utiliser des *déclencheurs*, des *comportements* et des *événements*.  
  
### Triggers  
 Un *déclencheur* modifie une propriété ou effectue une tâche en réponse à un événement ou à une modification apporté à une autre propriété. Par exemple, vous pouvez faire en sorte qu'un bouton change de couleur quand les utilisateurs le pointent avec la souris.  
  
 ![Volet Déclencheurs](../designers/media/custom_button_blend_propertytriggerinfo.png "custom\_button\_blend\_PropertyTriggerInfo")  
  
 **Regardez une courte vidéo :** ![Configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Ajouter un déclencheur de propriété](http://www.popscreen.com/v/6A4gO/Microsoft-Expression-Blend-Adding-a-Property-Trigger).  
  
### Comportements  
 Un *comportement* est un ensemble de code réutilisable. Il permet de faire un peu plus que modifier les propriétés. Il permet d'effectuer certaines actions, comme interroger un service de données. Blend en propose une petite collection, mais vous pouvez en ajouter d'autres. Faites glisser un comportement sur un objet dans la planche graphique, puis personnalisez\-le en définissant des propriétés.  
  
 ![FluidMoveBehavior dans le volet Propriétés](../designers/media/b4_fluidmovebehaviorproperties_sample.png "b4\_FluidMoveBehaviorProperties\_Sample")  
  
 **Regardez une courte vidéo :** ![Configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Conseils sur Blend : introduction à l’utilisation des comportements, Partie 1](http://www.bing.com/videos/search?q=Expression%20blend%20behaviors&qs=n&form=QBVR&pq=expression%20blend%20behavior&sc=4-25&sp=-1&sk=#view=detail&mid=CF0DD797ED84DE740904CF0DD797ED84DE740904).  
  
### Événements  
 Pour un maximum de souplesse, traitez un *événement*. Vous devrez écrire un peu de code.  
  
 **Regardez une courte vidéo :** ![Configurer les fonctionnalités installées](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Ajouter un événement de souris](https://www.youtube.com/watch?v=2PMxAlb-x_E).